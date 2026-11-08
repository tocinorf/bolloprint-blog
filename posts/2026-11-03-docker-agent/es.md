---
slug: install-bolloprint-agent-docker
title: "Pon en marcha el agente de BolloPrint con Docker"
description: Un NAS, un mini-PC, una Raspberry Pi o un servidor con Docker es todo lo que necesita el agente. Créalo en BolloPrint, pega el manifiesto que te da, arráncalo y tus impresoras aparecen. Sin tocar el router.
date: 2026-11-03
updated: 2026-11-03
tags: [tutoriales]
draft: true
---

El **agente local** es el programa pequeño que habla con tus impresoras por tu
propia red y le cuenta a BolloPrint lo que ve. Si en el taller ya hay un equipo
que usa **Docker**, ese equipo es todo lo que necesita el agente.

- **Cualquier equipo con Docker**: un NAS, un mini-PC, el PC del taller, una
  Raspberry Pi o un servidor que ya tengas. También con **Portainer**.
- **Un solo fichero, ya relleno**: BolloPrint te da el manifiesto con las claves
  de tu agente dentro. No hay nada que editar.
- **Sin tocar el router**: ni puertos abiertos, ni IP fija, ni reglas de
  cortafuegos.
- **Se actualiza solo**: cuando sale una versión nueva, la instala por su cuenta.

:::info 💡 ¿Tu equipo es una Synology, un QNAP, un TrueNAS, un PC con Windows o Home Assistant?
Entonces mira antes su paquete: se instala como cualquier otra aplicación y se
vincula con un clic, sin manifiesto de por medio. Tienes todas las opciones en
[el agente local](/help/el-agente-local). Docker es para todo lo demás.
:::

## Qué necesitas

- Un equipo del taller **siempre encendido**.
- **Docker** con **Docker Compose**, o **Portainer**.
- Lo ideal es que el equipo esté **en la misma red que las impresoras**, para que
  el agente las encuentre solo.

El agente es ligero: no necesita un equipo potente, el manifiesto le pone un tope
de 512 MB de memoria y la imagen funciona igual en Intel/AMD que en ARM.

:::info 💡 Docker Desktop en Windows o Mac
Ahí Docker corre dentro de una máquina virtual que no ve tu red, así que las
impresoras no se descubren solas. El agente funciona exactamente igual; solo que
añades cada impresora por su IP. En Windows, el
[instalador de Windows](/help/agente-en-windows) no tiene esa limitación.
:::

## 1. Crea el agente en BolloPrint

En BolloPrint, ve a **Configuración → Impresoras**, abre la pestaña **Agente
local** y pulsa **Nuevo agente**. Te pregunta **¿Dónde lo vas a instalar?**:
elige **Docker**, en **Con un contenedor**.

![La ventana Nuevo agente local: paquetes para Synology, QNAP, Windows, Home Assistant y TrueNAS, y Docker y Kubernetes en Con un contenedor](/blog/media/2026-11-03-docker-agent/01-new-agent.png "75%")

Ponle un nombre que dentro de seis meses te siga diciendo algo: **dónde está, no
qué es**. «Planta baja» o «Nave 2» sirven; «Agente 1», no. Después pulsa **Crear
agente**.

![Paso 2 de 3: el nombre del agente, Planta baja, y el botón Crear agente](/blog/media/2026-11-03-docker-agent/02-name.png "75%")

## 2. Copia el manifiesto

Ahora BolloPrint te enseña el **manifiesto**: un `docker-compose.yml` corto con el
código de tu agente, su identidad y la versión que toca **ya escritos dentro**.
Deja seleccionada la pestaña **Docker Compose**, pulsa **Copiar** y guárdalo en un
lugar seguro. Después pulsa **Guardar**.

![El manifiesto Docker Compose del agente nuevo, con sus dos claves (aquí difuminadas) y el botón Copiar](/blog/media/2026-11-03-docker-agent/03-manifest.png "75%")

:::warning 🔐 Cópialo ahora: las claves solo se muestran una vez
No las guardamos, así que no te las podemos volver a enseñar. Si pierdes el
manifiesto, no pasa nada: abre el agente con **Editar** (en su menú **⋮**), ve a
**Despliegue** y pulsa **Regenerar claves**. Si nunca se ha llegado a conectar, no
se corta nada.
:::

Hay dos líneas que conviene entender, aunque no vayas a tocarlas:

- `BP_AGENT_CODE` y `BP_AGENT_INSTANCE_ID` son **las claves del agente**: en qué
  taller trabaja y quién es. Trátalas como una contraseña.
- `network_mode: host` es lo que deja al agente **ver tu red** para encontrar las
  impresoras. No abre ningún puerto.

## 3. Arráncalo en tu equipo

Pega el manifiesto **tal cual**. Elige la forma en que uses Docker:

**Docker Compose.** Crea una carpeta, por ejemplo `bolloprint-agent`, guarda
dentro el manifiesto como `docker-compose.yml` y, desde esa carpeta, ejecuta:

```
docker compose up -d
```

**Portainer.** Ve a **Stacks → Add stack**, ponle de nombre `bolloprint-agent`,
pega el manifiesto en el **Web editor** y pulsa **Deploy the stack**.

<!-- SCREENSHOT: 04-portainer.png — Portainer (English UI, dark theme if possible), Stacks → Add stack: name «bolloprint-agent», the manifest pasted into the Web editor with its keys covered, and the Deploy the stack button visible. -->
![La pantalla Add stack de Portainer con el manifiesto del agente pegado en el editor web](/blog/media/2026-11-03-docker-agent/04-portainer.png "75%")

**El gestor de contenedores de tu NAS.** Si tu NAS trae el suyo (el **Container
Manager** de Synology, por ejemplo), crea un **proyecto** nuevo y pega el
manifiesto como su `docker-compose.yml`. Es Docker Compose con pantalla.

## 4. Comprueba que está en línea

De vuelta en BolloPrint, la fila del agente dice **Sin instalar** hasta que se
conecta por primera vez. No es un error: es que todavía no lo has arrancado. Su
botón **Instalar** te da la versión corta de estos pasos, por si la necesitas.

![El agente Docker nuevo, Sin instalar, con su botón Instalar, encima de otro agente que está En línea](/blog/media/2026-11-03-docker-agent/05-not-installed.png)

En menos de un minuto después de arrancar el contenedor, pasa a **En línea**, con
el nombre del equipo en el que corre y su versión. No te pedirá que autorices
nada: esa instalación ya viene autorizada.

![El agente Docker En línea, con el logo de Docker, el nombre del equipo y su versión](/blog/media/2026-11-03-docker-agent/06-online.png)

Si no sale en línea, mira lo que dice el agente en ese equipo:

```
docker logs bolloprint_agent --tail 50
```

Casi siempre es una de estas tres cosas: el manifiesto se pegó **a medias**, el
equipo **no tiene internet** o un **cortafuegos** bloquea la salida.

A partir de aquí, tus impresoras aparecen solas en **Impresoras por red local**,
listas para **Añadir**. El resto del camino, marca por marca, lo tienes en
[conecta tus impresoras por tu propia red](/blog/connect-printers-local-network-agent).

## Mantenerlo al día

Desde la versión **2026.1.1** el agente **se actualiza solo**: descarga la versión
nueva, comprueba que de verdad es nuestra y se reinicia con ella. Nunca lo hace
mientras alguna de sus impresoras está imprimiendo. Tú no tocas tu fichero.

Solo si BolloPrint te pide actualizar a mano (un agente instalado hace tiempo, de
antes de la actualización automática) tienes que hacer algo, y es poco: cambiar
**solo la versión** del final de la línea `image:` y volver a desplegar.

```yaml
    image: ghcr.io/bolloprint/bolloprint-agent:2026.1.1
```

La versión que toca es la de la línea `image:` en la pestaña **Despliegue** del
agente (**⋮ → Editar**). Después, desde la carpeta de tu `docker-compose.yml`:

```
docker compose pull
docker compose up -d
```

En Portainer, abre el stack, cambia la versión, activa **Re-pull image and
redeploy** y pulsa **Update the stack**.

![La pestaña Despliegue del agente: el manifiesto con CHANGE_ME en lugar de las claves, y Regenerar claves abajo](/blog/media/2026-11-03-docker-agent/07-deployment-tab.png "75%")

:::warning ⚠️ No pegues el manifiesto de la pestaña Despliegue encima de tu fichero
En un agente que ya existe, BolloPrint enseña **CHANGE_ME** donde van las claves,
porque no las guarda. Si lo pegas encima de tu fichero, el agente pierde sus
claves. Cambia solo la versión.
:::

## Moverlo a otro equipo

La identidad del agente va **dentro del manifiesto**, así que el mismo fichero
arrancado en otra máquina **es el mismo agente**, con todas sus impresoras y sin
autorización que dar.

1. Páralo en el equipo antiguo: `docker compose down` en su carpeta, o borra el
   stack en Portainer.
2. Copia el `docker-compose.yml` al nuevo y arráncalo allí con
   `docker compose up -d`.

Para el antiguo **antes**: dos equipos con las mismas claves a la vez se pisan la
conexión una y otra vez.

## Cuándo regenerar las claves

**Regenerar claves** (en la pestaña **Despliegue** del agente) crea un código y
una identidad nuevos y te enseña un manifiesto nuevo. Úsalo solo si **perdiste el
manifiesto** o crees que **alguien más tiene tus claves**. Corta el agente que
está en marcha en el momento, hasta que despliegues el manifiesto nuevo en lugar
del antiguo.

Para actualizar el agente no te hace falta nunca.

## Preguntas frecuentes

### ¿Necesito un agente por impresora?

No. **Un agente lleva toda la flota.** Ten varios solo si tienes redes separadas o
locales distintos, uno por sitio.

### ¿Puedo usar el mismo manifiesto en dos equipos?

No. Para dos equipos, crea dos agentes en BolloPrint, cada uno con su manifiesto.

### ¿Qué pasa si apago el equipo?

Nada. Cuando vuelve, el agente se reconecta solo. Y si se te cae internet, el
agente sigue leyendo las impresoras y lo manda todo cuando vuelve la línea.

### ¿Cómo lo quito?

Elimínalo en BolloPrint (**⋮ → Eliminar** en su fila) y después para y borra el
contenedor en tu equipo (`docker compose down`). Sus impresoras conservan su
número y su historial si las vuelves a añadir más adelante.

:::info 💡 ¿Necesitas ayuda?
Escríbenos desde la [página de contacto](/contact) o en
[nuestro Discord](/help/soporte-por-discord). Las últimas líneas de
`docker logs bolloprint_agent` son lo primero que te vamos a pedir.
:::

## Documentación relacionada

- [Agente en Docker](/help/agente-en-docker): todos los pasos y todos los detalles
- [El agente local](/help/el-agente-local): qué instalación te conviene
- [Impresoras por red local](/help/impresoras-por-red-local): añadir tus impresoras
- [Impresoras compatibles](/help/impresoras-compatibles): busca tu modelo
