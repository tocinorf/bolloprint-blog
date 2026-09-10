---
slug: instalar-agente-bolloprint-synology-container-manager
title: Montar el agente de BolloPrint en un Synology
description: Si ya tienes un NAS en el taller, deja de buscar dónde meter el agente. Veinte minutos por la interfaz de DSM, sin escribir un solo comando y sin tocar el router.
date: 2026-09-10
updated: 2026-09-10
tags: [tutoriales]
draft: true
---

Si tienes un Synology en el taller, ya tienes dónde meter el agente. Está
encendido las veinticuatro horas, está en la misma red que las impresoras y sabe
ejecutar contenedores desde hace años. Es difícil encontrar mejor sitio.

Y no hace falta que sepas nada de Docker: no vas a escribir ni un comando. Todo
sale de la interfaz de DSM, pegando un texto en un recuadro. Calcula veinte
minutos, y la mitad es esperar a que descargue.

:::info
Esto va solo del **despliegue en Synology**. Qué es el agente, qué marcas admite
y cómo das de alta cada impresora está en el
[tutorial de red local](/blog/conectar-impresoras-red-local-agente-bolloprint) —
cuando termines aquí, sigue por ahí.
:::

![Container Manager en DSM con el proyecto del agente en marcha](/blog/media/2026-09-10-agente-synology/01-container-manager.png)

## Por qué en el NAS y no en tu portátil

Porque el agente solo sirve si está despierto. Si lo pones en el ordenador que
apagas al irte, esas horas no las ves: ni qué imprimió, ni cuánto tardó, ni si
se paró a las tres de la mañana. El NAS ya está encendido de todas formas.

Lo demás viene de regalo: está en la red de las impresoras, que es lo que le
permite encontrarlas solo, y consume entre 10 y 20 MB de memoria. En un NAS eso
no lo nota nadie.

:::info 💡 No, no vas a tener que tocar el router
El agente **llama hacia fuera**, por el 443, igual que cuando abres una página
web. Nunca recibe conexiones de internet. Así que nada de abrir puertos, ni IP
fija, ni pelearte con el cortafuegos — y funciona igual detrás de un router
doméstico o de una fibra con CGNAT.
:::

## Lo que necesitas antes de ponerte

Cuatro cosas, y conviene mirarlas ahora y no a mitad:

- **Que el NAS y las impresoras estén en la misma red.** Si están en VLANs
  distintas el agente funciona igual, pero pierde el descubrimiento automático:
  tendrás que añadir cada impresora a mano por su IP.
- **Que el NAS salga a internet por el 443.** Nada más.
- **DSM 7.2 o superior.** Lo miras en **Panel de control → Actualización y
  restauración** (*Control Panel → Update & Restore*). Con 7.0 o 7.1 esto no te
  va a servir: actualiza DSM primero.
- **El código de conexión del agente**, que sacas creándolo en BolloPrint desde
  **Settings → Printers → Local agent**.

:::danger ⚠️ Arráncalo solo en el NAS, no lo pruebes antes en otro sitio
El **primer contenedor que arranque con ese código se queda la instalación**.
Así que si lo lanzas en tu portátil «a ver si tira» y luego lo montas en el
Synology, el NAS llega como una instalación desconocida y se queda esperando que
lo autorices.

Tampoco es una tragedia —se autoriza con un clic— pero te evitas el momento de
«¿y ahora por qué no sale?».
:::

:::warning 🔐 Ese código es una contraseña
Da acceso a los datos de conexión de las impresoras del taller. No lo pegues en
un grupo de WhatsApp ni lo dejes en una captura de pantalla.
:::

## 1. Instalar Container Manager

Es la app de Synology que ejecuta contenedores. Se instala como cualquier otra y
**por dentro no hay nada que configurar**, así que este paso es rápido.

Entra en DSM (`http://IP-DEL-NAS:5000`) con tu usuario administrador, abre
**Centro de paquetes** (*Package Center*), busca **Container Manager** y dale a
instalar. Uno o dos minutos. Luego ábrelo y espera a que arranque: cuando la
pestaña **Descripción general** (*Overview*) enseñe datos en vez de un aviso, ya
está.

![El Centro de paquetes de DSM con Container Manager](/blog/media/2026-09-10-agente-synology/02-centro-paquetes.png)

Verás que DSM se crea por su cuenta una carpeta compartida llamada `docker`. Es
normal, déjala en paz.

:::warning ⚠️ Si Container Manager no te aparece
Es que ese modelo de NAS no admite contenedores. No hay nada que hacer por
software: monta el agente en otra máquina de la misma red — un mini-PC, una
Raspberry Pi, cualquier cosa que esté siempre encendida.
:::

## 2. Crear el proyecto

En Container Manager un **proyecto** es básicamente una receta escrita: pegas un
texto, y el NAS se encarga de descargar y arrancar lo que ponga. No hay que
crear carpetas ni copiar ficheros.

Ve a **Proyecto → Crear** (*Project → Create*).

![Container Manager, pestaña Proyecto, botón Crear](/blog/media/2026-09-10-agente-synology/03-crear-proyecto.png)

De nombre, `bolloprint-agent`, en minúsculas — DSM no traga mayúsculas ni
espacios ahí. Para la ruta, pulsa **Establecer ruta** (*Set Path*), métete en la
carpeta `docker`, crea una llamada `bolloprint-agent` y selecciónala.

:::info 💡 Ahí solo va la receta, no tus datos
En esa carpeta se guarda **únicamente el texto del `docker-compose.yml`**. Lo
que el agente necesita recordar vive en un volumen interno de Docker que se crea
solo y que ni siquiera sale en File Station. Mejor así: nada que tocar y nada
que borrar sin querer.
:::

En **Origen** (*Source*) elige crear un `docker-compose.yml`. Te sale un
recuadro vacío, y ahí va el bloque.

:::danger ⚠️ Copia el bloque de tu pantalla, no el de aquí
Lo tienes en BolloPrint, en **Settings → Printers → Local agent → How to deploy
it**, pestaña **Docker Compose**, con su botón de copiar. Ese lleva la versión
del agente que toca en cada momento; el de abajo es para que veas la pinta.

**Y no se te ocurra poner `latest`.** Esa etiqueta no existe en el registro —lo
he comprobado hoy: devuelve 404— así que el proyecto se quedaría en
`manifest unknown` sin llegar a arrancar. No es un descuido de nadie: es
deliberado, porque una etiqueta móvil dejaría que una actualización cambiara el
agente por debajo de una flota en marcha sin que el taller lo decida.
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

Cambia `PEGA_AQUI_TU_CODIGO` por el tuyo, entero y sin espacios sueltos delante
o detrás — es el fallo más tonto y el que más veces pasa.

![El editor del docker-compose.yml dentro de Container Manager](/blog/media/2026-09-10-agente-synology/04-compose.png)

Cuatro cosas de ese texto que conviene que sepas:

- **Pégalo, no lo reescribas.** Los espacios del principio de cada línea son
  parte del formato, y como te cuele un tabulador DSM lo rechaza.
- **`network_mode: host`** es lo que hace que el agente vea la red del NAS y
  encuentre impresoras solo. Sin eso, todas a mano.
- **El volumen `identity`** es la memoria del agente. Es lo que evita que te
  pida autorización cada vez que reinicies.
- **Las líneas con `#` están apagadas a propósito.** Solo se encienden si hay
  que diagnosticar algo.

Cuando siga, DSM te ofrece publicar un «portal web». Dile **Ninguno** (*None*):
el agente no tiene ninguna página que enseñar.

Y ya. DSM descarga la imagen y arranca el contenedor enseñándote un registro en
vivo. Un par de minutos según tu conexión. Si al terminar el proyecto se queda
parado, lo seleccionas y **Acción → Iniciar** (*Action → Start*).

## 3. Comprobar que va

Hay tres señales, pero **la que de verdad vale es la tercera**. Las dos primeras
solo te dicen que el contenedor arrancó, no que esté hablando con nadie.

**El contenedor está en marcha.** En **Contenedor** (*Container*) debe salir
`bolloprint_agent` como **En ejecución**, gastando unas pocas decenas de MB.

![La lista de contenedores con bolloprint_agent en ejecución](/blog/media/2026-09-10-agente-synology/05-contenedor.png)

**El registro dice lo que tiene que decir.** Doble clic en el contenedor,
pestaña **Registro** (*Log*), y en los primeros segundos deberías ver esto:

```
INFO bolloprint-agent starting version=0.4.8
INFO installation fingerprint source=stored ...
INFO bootstrapped agent_id=... printers=0
INFO broker connected
```

Cada línea confirma una cosa distinta, y por eso merece la pena mirarlas:

| Línea | Qué te está diciendo |
|---|---|
| `source=stored` | El volumen de identidad está montado y se puede escribir. Si pone otra cosa, prepárate a autorizar el agente cada vez que se recree el contenedor. |
| `bootstrapped` | El código es bueno y BolloPrint lo ha reconocido. |
| `broker connected` | La conexión permanente está abierta. De aquí en adelante el agente ya reporta. |

![La pestaña Registro con las líneas de arranque](/blog/media/2026-09-10-agente-synology/06-registro.png)

**Y el agente se pone verde en BolloPrint.** En **Settings → Printers → Local
agent**, la tarjeta debe pasar a **Online** en unos treinta segundos. Esa es la
buena: significa que el circuito entero funciona.

![La tarjeta del agente en Online dentro de BolloPrint](/blog/media/2026-09-10-agente-synology/07-agente-online.png)

## Si algo no sale

| Lo que ves | Qué suele ser |
|---|---|
| `manifest unknown` al descargar | La versión de la imagen no existe. Vuelve a copiar el bloque de tu pantalla — y mira que no hayas puesto `latest`. |
| Arranca y se para solo | Al registro. Casi siempre es el código mal pegado, con un espacio colado delante o detrás. |
| `bootstrapped` no sale nunca | El NAS no llega a internet por el 443, o hay un cortafuegos comiéndose la salida. |
| Te pide autorización en cada reinicio | Le falta el volumen de identidad. Comprueba que pegaste la sección `volumes` entera. |
| Aparece como instalación pendiente de autorizar | Ese código ya se usó en otra máquina. Si reconoces el equipo, autorízalo — eso sí, al autorizar uno el anterior pierde el acceso. |
| No encuentra ninguna impresora | ¿Están el NAS y las impresoras en la misma red? Si no, es lo esperado: añádelas por IP y van igual de bien. |

## Lo que queda

Con el agente en verde tienes media faena. Falta darle las impresoras: las que
aparecen solas, las que hay que meter por IP y lo que pide cada marca está todo
en el [tutorial de red local](/blog/conectar-impresoras-red-local-agente-bolloprint).

A partir de ahí te puedes olvidar. El contenedor vuelve solo cada vez que
reinicies el NAS y no pide mantenimiento. Lo único que harás de vez en cuando es
actualizarlo: cuando BolloPrint te avise de que hay versión nueva, copias otra
vez el bloque de la pantalla y reinicias el proyecto.

## Para seguir leyendo

- [El agente local](/help/el-agente-local) — instalación, identidad, varios agentes y diagnóstico
- [Impresoras por red local](/help/impresoras-por-red-local) — dar de alta las máquinas
- [Tipos de conexión](/help/tipos-de-conexion) — qué permite cada familia de impresora
- [Impresoras compatibles](/help/impresoras-compatibles) — busca aquí tu modelo
- [Conectar impresoras](/help/conectar-impresoras) — las dos vías y cuál te conviene
