---
slug: instalar-agente-bolloprint-synology-container-manager
title: Instalar el agente de BolloPrint en un NAS Synology, paso a paso
description: Si ya tienes un Synology encendido en el taller, es el sitio ideal para el agente. Veinte minutos con Container Manager, sin tocar el router y sin saber nada de contenedores.
date: 2026-09-10
updated: 2026-09-10
tags: [tutoriales]
draft: false
---

Para conectar tus impresoras por red local hace falta el **agente**, un programa
pequeño que corre en un equipo del taller. Y si ya tienes un **NAS Synology**,
ese equipo ya lo tienes: está siempre encendido, está en la misma red que las
impresoras y sabe ejecutar contenedores desde DSM.

Este tutorial monta el agente entero en un Synology, **desde cero y sin saber
nada de Docker**. Son unos 20 minutos, y casi todo es esperar descargas.

:::info
Aquí solo se cubre **el despliegue en Synology**. Cómo funciona el agente, qué
marcas admite y cómo dar de alta cada impresora está en el
[tutorial de red local](/blog/conectar-impresoras-red-local-agente-bolloprint).
Cuando acabes aquí, sigue por ahí.
:::

![Container Manager en DSM, con el proyecto del agente en ejecución](/blog/media/2026-09-10-agente-synology/01-container-manager.png)

## Por qué el NAS es buen sitio

- **Está siempre encendido.** Es el requisito de verdad del agente: si el equipo
  se apaga por la noche, dejas de ver lo que hacen las impresoras.
- **Está en la red de las impresoras**, que es lo que le permite descubrirlas
  solo.
- **Consume nada**: entre 10 y 20 MB de memoria con varias máquinas conectadas.
  En un NAS eso no se nota.

:::info 💡 El agente no abre tu NAS a internet
Es **él quien llama hacia fuera**, por el puerto 443, igual que cuando abres una
página web. No recibe conexiones de fuera nunca. Por eso **no hay que abrir
puertos en el router**, ni tener IP fija, ni tocar el cortafuegos — y funciona
igual detrás de un router doméstico o de una conexión con CGNAT.
:::

## Antes de empezar

Cinco comprobaciones. Si falla alguna, el resto no va a funcionar y es mejor
saberlo ahora que a mitad:

- [ ] **El NAS está en la misma red que las impresoras.** Misma LAN, sin router
      de por medio. Si están separadas el agente funciona igual, pero no las
      descubrirá solo: habrá que añadirlas a mano por su IP.
- [ ] **El NAS tiene salida a internet** por el puerto **443**. Nada más.
- [ ] **Tienes un usuario administrador de DSM.**
- [ ] **DSM es la versión 7.2 o superior.** Se ve en **Panel de control →
      Actualización y restauración** (*Control Panel → Update & Restore*). Con
      DSM 7.0 o 7.1 este tutorial no sirve: hay que actualizar DSM primero.
- [ ] **Tienes creado el agente en BolloPrint** y a mano su **código de
      conexión**. Se crea en **Settings → Printers → Local agent**, y está
      explicado en el [tutorial de red local](/blog/conectar-impresoras-red-local-agente-bolloprint).

:::danger ⚠️ Arranca el agente SOLO en el NAS
**El primer contenedor que arranque con ese código se queda con la
instalación.** Si lo pruebas antes en tu portátil «para ver si va» y luego lo
montas en el Synology, el NAS llegará como una instalación desconocida y se
quedará **pendiente de autorizar**.

No es grave —se autoriza con un clic— pero te ahorras el susto sabiéndolo.
:::

:::warning 🔐 El código es una credencial
Da acceso a los datos de conexión de las impresoras del taller. Trátalo como una
contraseña: no va en un chat de grupo ni en una captura de pantalla.
:::

## Paso 1 — Instala Container Manager

Es la aplicación de Synology que sabe ejecutar contenedores. Se instala como
cualquier otra y **no hay nada que configurar dentro de ella**.

1. Entra en DSM: en el navegador, `http://IP-DEL-NAS:5000`, con tu usuario
   administrador.
2. Abre **Menú principal → Centro de paquetes** (*Package Center*).
3. Busca **Container Manager** y pulsa **Instalar**. Tarda uno o dos minutos.
4. Ábrelo y espera a que arranque. Cuando la pestaña **Descripción general**
   (*Overview*) enseñe datos en vez de un aviso, ya está.

![Centro de paquetes de DSM con Container Manager](/blog/media/2026-09-10-agente-synology/02-centro-paquetes.png)

DSM crea por su cuenta una carpeta compartida llamada `docker`. Es normal y no
hay que tocarla.

:::warning ⚠️ Si Container Manager no aparece en la lista
Ese modelo de NAS **no admite contenedores**. Es una limitación del hardware, no
hay solución por software: monta el agente en otra máquina de la misma red — un
mini-PC, una Raspberry Pi o cualquier equipo que esté siempre encendido.
:::

## Paso 2 — Crea el proyecto del agente

En Container Manager, un **proyecto** es una receta escrita: pegas un texto y el
NAS se encarga de descargar y arrancar lo que diga. No hay que crear carpetas ni
copiar ficheros a mano.

### 2.1 · Nuevo proyecto

Ve a **Container Manager → Proyecto → Crear** (*Project → Create*).

![Container Manager, pestaña Proyecto, botón Crear](/blog/media/2026-09-10-agente-synology/03-crear-proyecto.png)

### 2.2 · Nombre y ruta

- **Nombre**: `bolloprint-agent`. En minúsculas — DSM no acepta mayúsculas ni
  espacios aquí.
- **Ruta**: pulsa **Establecer ruta** (*Set Path*), entra en la carpeta `docker`,
  pulsa **Crear carpeta**, llámala `bolloprint-agent` y selecciónala.

:::info 💡 Ahí solo se guarda la receta
En esa carpeta va **únicamente el texto del `docker-compose.yml`**. Los datos del
agente **no van a ninguna carpeta compartida**: viven en un volumen interno de
Docker que se crea solo y que ni siquiera aparece en File Station. Es lo que
queremos — nada que tocar y nada que romper por accidente.
:::

### 2.3 · Pega el bloque

En el desplegable **Origen** (*Source*) elige **crear un `docker-compose.yml`**.
Aparecerá un recuadro de texto vacío.

:::danger ⚠️ Copia el bloque de TU pantalla, no de este artículo
En BolloPrint, en **Settings → Printers → Local agent → How to deploy it**,
pestaña **Docker Compose**, tienes el bloque con el botón **Copy**. Ese lleva
**la versión del agente que toca en cada momento**.

El de aquí abajo es para que veas la pinta que tiene. **Y no pongas `latest`:**
esa etiqueta no existe en el registro —lo he comprobado hoy: responde 404— y el
proyecto fallaría con `manifest unknown` sin llegar a arrancar. No es un olvido,
es deliberado: una etiqueta móvil dejaría que una actualización cambiara el
agente bajo una flota en marcha sin que el taller lo decida.
:::

```yaml
services:
  bolloprint-agent:
    image: ghcr.io/bolloprint/bolloprint-agent:0.4.8   # ← la que diga tu pantalla
    container_name: bolloprint_agent
    restart: unless-stopped
    network_mode: host
    mem_limit: 512m
    pids_limit: 512
    ulimits:
      nofile:
        soft: 65536
        hard: 65536
    environment:
      BP_AGENT_CODE: PEGA_AQUI_TU_CODIGO
      # BP_STATUS_PORT: 9911
      # BP_LOG_LEVEL: debug
    volumes:
      - identity:/var/lib/bolloprint

volumes:
  identity:
    name: bolloprint_agent_identity
```

Sustituye `PEGA_AQUI_TU_CODIGO` por tu código de conexión, entero y sin espacios
delante ni detrás.

![El editor del docker-compose.yml en Container Manager](/blog/media/2026-09-10-agente-synology/04-compose.png)

Cuatro apuntes sobre ese texto:

- **Pégalo, no lo reescribas.** Los espacios del principio de cada línea son
  parte del formato, y un tabulador en lugar de espacios hace que DSM lo
  rechace.
- **`network_mode: host`** es lo que permite el descubrimiento automático de
  impresoras. Sin eso, el contenedor no ve la red del NAS y habría que añadirlas
  todas a mano.
- **El volumen `identity`** guarda la identidad de esta instalación. Es lo que
  evita que el agente pida autorización cada vez que se reinicie.
- **Las dos líneas con `#` están apagadas a propósito.** Solo se encienden para
  diagnosticar.

### 2.4 · Sin portal web

DSM ofrece publicar un «portal web» para el proyecto. Elige **Ninguno** (*None*):
el agente no tiene ninguna página que publicar.

### 2.5 · Termina

DSM descarga la imagen y arranca el contenedor mientras enseña un registro en
vivo. Uno o dos minutos según tu conexión. Cuando acabe, ciérralo.

:::info
Si el proyecto se queda parado, selecciónalo en la lista y pulsa **Acción →
Iniciar** (*Action → Start*).
:::

## Paso 3 — Comprueba que ha funcionado

Tres señales, en este orden. **La tercera es la que cuenta.**

### a) El contenedor está en ejecución

En **Container Manager → Contenedor** (*Container*) debe aparecer
`bolloprint_agent` en estado **En ejecución**, con un consumo de memoria de unas
pocas decenas de MB.

![La lista de contenedores con bolloprint_agent en ejecución](/blog/media/2026-09-10-agente-synology/05-contenedor.png)

### b) El registro dice lo que tiene que decir

Doble clic en el contenedor y abre la pestaña **Registro** (*Log*). En los
primeros segundos deben salir estas líneas:

```
INFO bolloprint-agent starting version=0.4.8
INFO installation fingerprint source=stored ...
INFO bootstrapped agent_id=... printers=0
INFO broker connected
```

| Línea | Qué confirma |
|---|---|
| `source=stored` | El volumen de identidad está montado y se puede escribir. Si pone otra cosa, el agente pedirá autorización cada vez que se recree el contenedor. |
| `bootstrapped` | El código es válido y BolloPrint lo ha reconocido. |
| `broker connected` | La conexión permanente está establecida. A partir de aquí el agente ya reporta. |

![La pestaña Registro con las líneas de arranque](/blog/media/2026-09-10-agente-synology/06-registro.png)

### c) El agente se pone en verde en BolloPrint

En **Settings → Printers → Local agent**, la tarjeta del agente debe pasar a
**Online** en unos 30 segundos.

**Esa es la comprobación de verdad**: significa que el circuito completo
funciona. Las dos anteriores solo dicen que el contenedor arrancó.

![La tarjeta del agente en Online dentro de BolloPrint](/blog/media/2026-09-10-agente-synology/07-agente-online.png)

## Si algo no va

| Lo que ves | Qué suele ser |
|---|---|
| `manifest unknown` al descargar | La versión de la imagen no existe. Copia el bloque otra vez desde tu pantalla de BolloPrint — y comprueba que no pusiste `latest`. |
| El contenedor arranca y se para solo | Mira el registro: casi siempre es el código mal pegado, con un espacio delante o detrás. |
| `bootstrapped` no aparece nunca | El NAS no llega a internet por el 443, o hay un cortafuegos bloqueando la salida. |
| El agente pide autorización en cada reinicio | Falta el volumen de identidad. Revisa que el bloque lleva la sección `volumes` entera, tal cual. |
| Sale como instalación pendiente de autorizar | Ese código ya se usó en otra máquina. Autorízalo desde BolloPrint si reconoces el equipo — al autorizar uno, el anterior pierde el acceso. |
| No detecta ninguna impresora | ¿Están el NAS y las impresoras en la misma red? Si no, es lo esperado: añádelas a mano por su IP y funcionarán igual. |

## Y ahora, las impresoras

Con el agente en verde ya tienes la mitad hecha: falta darle de alta las
máquinas. Eso —las que aparecen solas, las que hay que añadir por IP, y lo que
pide cada marca— está en el
[tutorial de conectar impresoras por red local](/blog/conectar-impresoras-red-local-agente-bolloprint).

El contenedor **arranca solo cada vez que se reinicie el NAS** y no necesita
mantenimiento. Lo único que harás de vez en cuando es actualizarlo: cuando
BolloPrint avise de que hay versión nueva, vuelves a copiar el bloque de la
pantalla y reinicias el proyecto.

## Documentación relacionada

- [El agente local](/help/el-agente-local) — instalación, identidad, varios agentes y diagnóstico
- [Impresoras por red local](/help/impresoras-por-red-local) — dar de alta las máquinas
- [Tipos de conexión](/help/tipos-de-conexion) — qué permite cada familia de impresora
- [Impresoras compatibles](/help/impresoras-compatibles) — busca aquí tu modelo
- [Conectar impresoras](/help/conectar-impresoras) — las dos vías y cuál te conviene
