---
slug: install-bolloprint-agent-home-assistant
title: "Instala el agente de BolloPrint en Home Assistant"
description: ¿Ya tienes Home Assistant en marcha en el taller? Entonces ya tienes dónde poner el agente. Añádelo a Home Assistant con un botón desde BolloPrint, instálalo, pulsa Vincular con BolloPrint y aparecen tus impresoras. Sin códigos y sin tocar el router.
date: 2026-11-03
updated: 2026-11-03
tags: [tutoriales]
draft: true
---

Si en tu taller hay un Home Assistant encendido día y noche, ya tienes resuelta
la parte más difícil de montar el **agente local**: encontrar un equipo que esté
siempre en marcha y en la misma red que tus impresoras.

El agente es el pequeño programa que habla con tus impresoras por tu propia red
y le cuenta a BolloPrint lo que ve. En Home Assistant se instala como **una
app**, desde la propia tienda de apps de Home Assistant, y lo vinculas con tu
taller con un botón.

- **Sin códigos ni claves que copiar**: lo vinculas desde su página y lo
  confirmas en BolloPrint.
- **No tocas el router**: ni puertos abiertos ni IP fija.
- **Se cuida solo**: el agente se actualiza solo, y la app cuando Home Assistant
  te lo ofrece.

:::info Beta
La app de Home Assistant está en beta. Si algo no encaja, cuéntanoslo desde
**Ayuda** en BolloPrint.
:::

## Lo que necesitas

- **Home Assistant OS**, que es la instalación que trae tienda de apps. Si tu
  Home Assistant va en Docker («Container»), no tiene apps: instala el agente
  con Docker, como cuenta
  [Agente en Docker](/help/agente-en-docker).
- **Un equipo de 64 bits**: un mini-PC o un PC con Intel o AMD, una Raspberry
  Pi 4 o 5, o un Home Assistant Green o Yellow. Una Raspberry Pi 3 o cualquier
  sistema de 32 bits no sirve.
- Que Home Assistant esté **en la misma red que tus impresoras**. Si va en una
  máquina virtual, su red tiene que estar en modo **puente** (bridge), no en NAT.
- Ser **propietario** del taller en BolloPrint: el agente solo se puede vincular
  a un taller tuyo.

## 1. Añade BolloPrint a tu Home Assistant

Desde un ordenador o un móvil conectado a la red del taller, abre BolloPrint y
ve a **Configuración → Impresoras → Agente local → Nuevo agente**. En **Con un
paquete o un instalador**, elige **Home Assistant** y pulsa **Añadir a Home
Assistant**.

![La tarjeta de Home Assistant en BolloPrint, con el botón Añadir a Home Assistant y los tres pasos de instalación](/blog/media/2026-11-03-homeassistant-agent/01-ha-card.png "75%")

El botón abre **My Home Assistant**, una página de Home Assistant que te lleva a
tu propio Home Assistant. La primera vez te pide su dirección, algo como
`http://homeassistant.local:8123`. Luego pulsa **Open link**.

![La página de My Home Assistant pidiendo abrir el enlace en tu propio Home Assistant](/blog/media/2026-11-03-homeassistant-agent/02-my-home-assistant.png "75%")

Tu Home Assistant te pregunta si quieres añadir el repositorio de aplicaciones
de BolloPrint (`github.com/bolloprint/agent-home-assistant`). Pulsa **Añadir**.

<!-- SCREENSHOT: 03-add-repository.png — Home Assistant (English UI) dialog «Add app repository?» showing the BolloPrint repository URL and the Add button. -->
<!-- PENDING (uncomment when the screenshot exists): ![Home Assistant pidiendo añadir el repositorio de aplicaciones de BolloPrint](/blog/media/2026-11-03-homeassistant-agent/03-add-repository.png "75%") -->

:::info ¿Prefieres hacerlo a mano?
En Home Assistant, ve a **Configuración → Aplicaciones → Tienda de
aplicaciones**, abre el menú **⋮** de arriba a la derecha y entra en
**Repositorios**. Pulsa **Añadir**, pega
`https://github.com/bolloprint/agent-home-assistant` y confirma. BolloPrint
tiene su propia sección en la tienda.
:::

## 2. Instala e inicia la app

**BolloPrint Agent** ya aparece en la tienda de aplicaciones, en su propia
sección de BolloPrint: es la del perro de BolloPrint. Ábrela y pulsa
**Instalar**. Home Assistant prepara la app él mismo; tarda uno o dos minutos.

<!-- SCREENSHOT: 04-install.png — Home Assistant (English UI) app page of BolloPrint Agent, not installed yet, with the Install button. -->
<!-- PENDING (uncomment when the screenshot exists): ![La app BolloPrint Agent en Home Assistant, lista para instalar](/blog/media/2026-11-03-homeassistant-agent/04-install.png) -->

Después pulsa **Iniciar** y deja activado **Iniciar en el arranque**, para que el
agente vuelva solo cada vez que se reinicie Home Assistant.

<!-- SCREENSHOT: 05-started.png — Home Assistant (English UI) app page of BolloPrint Agent, running, with Start on boot on and the Open Web UI button. -->
<!-- PENDING (uncomment when the screenshot exists): ![La app en marcha, con Iniciar en el arranque activado y el botón Open Web UI](/blog/media/2026-11-03-homeassistant-agent/05-started.png) -->

## 3. Vincúlalo con tu taller

Pulsa **Open Web UI** en la ficha de la app (Home Assistant lo deja en inglés).
Se abre la página del agente en una pestaña nueva: dice que todavía no
pertenece a ningún taller y enseña un código corto.

<!-- SCREENSHOT: 06-agent-page.png — the agent's page at http://<home-assistant>:8257 in English: «This agent doesn't belong to any workshop yet», the code and the Link with BolloPrint button. -->
<!-- PENDING (uncomment when the screenshot exists): ![La página del agente, con su código y el botón Vincular con BolloPrint](/blog/media/2026-11-03-homeassistant-agent/06-agent-page.png "75%") -->

Pulsa **Vincular con BolloPrint**. Te lleva a BolloPrint (entra con tu cuenta si
te lo pide):

1. Elige el taller.
2. Comprueba que el código es **el mismo** que enseña la página del agente.
3. Revisa el nombre que te propone para el agente, cámbialo si quieres y
   confirma.

<!-- SCREENSHOT: 07-confirm.png — BolloPrint (English UI) link confirmation page: workshop, matching code, agent name, Confirm button. -->
<!-- PENDING (uncomment when the screenshot exists): ![Confirmando la vinculación en BolloPrint: el taller, el código y el nombre del agente](/blog/media/2026-11-03-homeassistant-agent/07-confirm.png "75%") -->

Vuelves a la página del agente, que ahora dice que está vinculado a tu taller.
En BolloPrint, en **Configuración → Impresoras → Agente local**, el agente sale
**En línea** en menos de un minuto, con el logo de Home Assistant, y empieza a
buscar tus impresoras.

![El agente de Home Assistant en la lista de agentes locales de BolloPrint: En línea, con el logo de Home Assistant y su versión](/blog/media/2026-11-03-homeassistant-agent/08-online.png)

:::warning Hazlo desde la red del taller
La página del agente solo se abre dentro de tu red local. Si entras en Home
Assistant desde fuera (con el acceso remoto o una VPN), **Open Web UI** no
cargará. Vincúlalo desde un ordenador o un móvil conectado a la red del taller.
:::

En BolloPrint no hay que crear nada: confirmar la vinculación es lo que añade
el agente a la lista.

## Si el puerto 8257 ya está ocupado

La página del agente usa el puerto **8257** del equipo de Home Assistant. Si otra
cosa ya lo está usando, la app se para nada más arrancar y su pestaña
**Registro** dice `address already in use`. Abre la pestaña **Configuración** de
la app, pon otro número en **Red** (por ejemplo, 8364), pulsa **Guardar** y acepta
cuando Home Assistant te pregunte si reinicia la app. **Open Web UI** ya te lleva
al puerto nuevo, y el agente sigue vinculado.

## Mantenerlo al día

Aquí se actualizan dos cosas, y casi nunca tendrás que hacer nada:

- **El agente**, lo que habla con tus impresoras, se actualiza solo cada vez que
  BolloPrint publica una versión nueva.
- **La app**, lo que pone en marcha el agente dentro de Home Assistant, se
  actualiza cuando Home Assistant te avisa de que hay una versión nueva de
  **BolloPrint Agent**: pulsa **Actualizar** en su ficha, o activa
  **Actualización automática** y olvídate.

Actualizar nunca desvincula el agente. Su identidad se guarda en los datos de la
app, que también entran en las copias de seguridad de Home Assistant.

## Cambiarlo de equipo o quitarlo

Si reinstalas la app o la pones en **otro Home Assistant**, vincúlala otra vez:
será un **agente nuevo**. Añade tus impresoras con él y pasarán con su número y
todo su historial. Después elimina el agente antiguo, que se habrá quedado sin
impresoras.

Para quitarlo del todo, elimina primero el agente en BolloPrint (**⋮** →
**Eliminar** en su fila). En unos segundos su página vuelve a ofrecer **Vincular
con BolloPrint**. Después desinstala la app en Home Assistant y, si ya no lo
necesitas, quita el repositorio en **Repositorios**.

Si desinstalas la app sin eliminar antes el agente, en BolloPrint se queda como
**Desconectado**: elimínalo desde su menú **⋮**.

## ¿Algo no va?

Lo primero es la pestaña **Registro** de la app en Home Assistant: cuenta lo que
hace el agente y, si se para, por qué. Los tropiezos más habituales:

- **La app no aparece en la tienda**: en la tienda de aplicaciones, **⋮** →
  **Buscar actualizaciones**, y recarga la página.
- **No te deja instalarla**: el equipo es de 32 bits. La app necesita 64 bits.
- **No encuentra ninguna impresora**: Home Assistant y las impresoras no están en
  la misma red, o la máquina virtual usa NAT. Añádelas por IP y funcionan
  igual.
- **Al vincular no aparece tu taller**: solo el propietario del taller puede
  vincular un agente.

Todo lo demás, paso a paso, está en la guía
[**Agente en Home Assistant**](/help/agente-en-home-assistant).

Que disfrutes de tener tus impresoras a la vista, con Home Assistant haciendo de puente.

![Bollo, la mascota de BolloPrint, junto al logo de Home Assistant](/blog/media/2026-11-03-homeassistant-agent/10-bollo.webp "60%")
