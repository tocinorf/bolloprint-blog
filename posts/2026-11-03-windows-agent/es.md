---
slug: install-bolloprint-agent-windows
title: "Instalar el agente de BolloPrint en un PC con Windows"
description: ¿Tienes en el taller un PC con Windows que nunca se apaga? Es todo lo que necesita el agente. Descarga el instalador desde BolloPrint, sigue el asistente, pulsa Vincular con BolloPrint y tus impresoras aparecen. Nada que copiar, sin Docker y sin tocar el router.
date: 2026-11-03
updated: 2026-11-03
tags: [tutoriales]
draft: true
---

Casi todos los talleres tienen uno: el PC del rincón que hace funcionar el
laminador, imprime las etiquetas de envío y que, en realidad, nunca se apaga.
Ese PC es todo lo que necesita el **agente local**.

El agente es el pequeño programa que habla con tus impresoras por tu propia red
y le cuenta a BolloPrint lo que ve. En Windows se instala como cualquier otro
programa, se queda funcionando en segundo plano sin molestar y se vincula a tu
taller con un botón.

- **Sin códigos ni claves que copiar**: lo vinculas desde su página y confirmas en BolloPrint.
- **Sin Docker**: es un instalador de Windows de los de siempre.
- **No tocas el router**: ni puertos abiertos ni IP fija.
- **Se actualiza solo**: cuando sale una versión nueva, la instala él.

:::info Beta
El agente para Windows está en beta. Si algo no te cuadra, cuéntanoslo desde
**Ayuda** en BolloPrint.
:::

## Lo que necesitas

- Un **PC con Windows 10 u 11 de 64 bits**, con procesador Intel o AMD.
- Que ese PC esté **siempre encendido** y **en la misma red que tus impresoras**.
  Si se suspende, BolloPrint deja de ver tus impresoras hasta que vuelva.
- Poder **instalar programas** en él: Windows te pedirá permiso de
  administrador.
- Ser el **dueño** del taller en BolloPrint: solo el dueño puede añadir un
  agente.

No hace falta crear nada antes en BolloPrint. El agente se une a tu taller al
vincularlo.

## 1. Descarga el instalador desde BolloPrint

En BolloPrint, ve a **Configuración → Impresoras**, abre la pestaña **Agente
local** y pulsa **Nuevo agente**. En **Con un paquete o un instalador**, elige
**Windows** y pulsa **Descargar para Windows**.

![La tarjeta de Windows en la ventana Nuevo agente de BolloPrint: el botón Descargar para Windows y los tres pasos de Cómo instalarlo](/blog/media/2026-11-03-windows-agent/01-download.png "75%")

La tarjeta te resume en tres pasos lo que viene ahora. Ahí no hay nada que crear
ni que rellenar: el agente aparece solo en esa lista en cuanto lo vinculas.

Descárgalo siempre desde ahí: es donde está la versión que toca. Si el
navegador te avisa de que el archivo no se descarga habitualmente, elige
**Conservar**.

## 2. Pasa el aviso de Windows

Nuestro instalador todavía no lleva firma digital, así que Windows lo trata
como un programa desconocido. Al abrirlo verás una pantalla azul: **Windows
protegió su PC**. Es lo esperado:

1. Pulsa **Más información**.
2. Pulsa **Ejecutar de todas formas**.

<!-- SCREENSHOT: 02-smartscreen.png — Windows 11 (English) SmartScreen «Windows protected your PC» AFTER clicking «More info»: app name bolloprint-agent-setup-….exe, publisher Unknown, and the «Run anyway» button. -->
<!-- PENDING (uncomment when the screenshot exists): ![Windows SmartScreen después de Más información, con el botón Ejecutar de todas formas](/blog/media/2026-11-03-windows-agent/02-smartscreen.png "75%") -->

Después Windows pregunta si permites que la aplicación haga cambios en el
equipo. Pulsa **Sí**: el agente lo necesita para instalarse como servicio y
para poder encontrar tus impresoras en la red.

:::warning ¿No aparece «Ejecutar de todas formas»?
Entonces tu PC tiene activado el **Control inteligente de aplicaciones**
(*Smart App Control*). Bloquea los programas sin firma y no deja hacer
excepciones. No te recomendamos desactivarlo. Mejor pon el agente en **otro
equipo siempre encendido de la misma red** (un NAS, una Raspberry Pi, otro PC):
las opciones están en [El agente local](/help/el-agente-local).
:::

## 3. Sigue el asistente

Es cortito:

1. Elige el idioma y deja la carpeta que propone.
2. En **Página del agente**, deja el puerto en **8257**. Solo tienes que
   cambiarlo si otro programa del PC ya lo usa; en ese caso, prueba con **8364**.
3. Pulsa **Instalar**.

<!-- SCREENSHOT: 03-port.png — the installer (English) on the «The agent's page» step, with the port field at 8257. -->
<!-- PENDING (uncomment when the screenshot exists): ![El paso del asistente para la página del agente, con el puerto en 8257](/blog/media/2026-11-03-windows-agent/03-port.png "75%") -->

Cuando termine, deja marcada la casilla **Abrir la página del agente para
vincularlo** y pulsa **Finalizar**.

<!-- SCREENSHOT: 04-finish.png — the installer (English) final screen with «Open the agent's page to link it» ticked and the Finish button. -->
<!-- PENDING (uncomment when the screenshot exists): ![El último paso del asistente, con Abrir la página del agente para vincularlo marcada](/blog/media/2026-11-03-windows-agent/04-finish.png "75%") -->

A estas alturas el agente ya funciona como servicio de Windows: arranca con el
PC, sigue trabajando aunque nadie haya iniciado sesión y tiene un pequeño
**icono de BolloPrint** junto al reloj.

## 4. Vincúlalo con tu taller

La página del agente se abre en tu navegador. Dice que el agente todavía no
pertenece a ningún taller y enseña un **código** corto. Fíjate en él y pulsa
**Vincular con BolloPrint**.

![La página del agente, con su código y el botón Vincular con BolloPrint](/blog/media/2026-11-03-windows-agent/05-agent-page.png "75%")

Se abre BolloPrint. Inicia sesión con la cuenta del dueño si no la tenías
abierta. Si eres dueño de más de un taller, te pregunta **¿A qué taller lo
añades?**

<!-- SCREENSHOT: 06-choose-workshop.png — bolloprint.com (English) «Add an agent to your workshop» asking which workshop to add it to, with two workshops listed. Only if the account owns more than one; otherwise drop this image. -->
<!-- PENDING (uncomment when the screenshot exists): ![Elegir a qué taller se añade el agente](/blog/media/2026-11-03-windows-agent/06-choose-workshop.png "75%") -->

Luego ves la confirmación: el nombre de tu PC y un **código**. Comprueba que es
el mismo código que el de la página del agente, ponle al agente un nombre que
reconozcas (mejor dónde está, como «Oficina», que «Agente 1») y pulsa **Añadir
al taller**.

<!-- SCREENSHOT: 07-confirm.png — BolloPrint (English UI) «Add an agent to <workshop>»: Device (the PC's name), Code (matching the one in 05), the agent's name field and the «Add to workshop» button. -->
<!-- PENDING (uncomment when the screenshot exists): ![Confirmar en BolloPrint: el PC, el código que coincide y el nombre del agente](/blog/media/2026-11-03-windows-agent/07-confirm.png "75%") -->

:::warning 🔐 Solo si has pulsado tú el botón
Confirma únicamente si acabas de pulsar **Vincular con BolloPrint** en tu
propio PC. Si alguien te ha mandado un enlace para «añadir un agente»,
ciérralo.
:::

## 5. Comprueba que funciona

Llegas a **Configuración → Impresoras → Agente local**, con tu agente nuevo en
la lista, **En línea**, con el logo de Windows. La página del agente, en tu PC,
dice ahora **Vinculado a** y el nombre de tu taller.

<!-- SCREENSHOT: 08-online.png — BolloPrint (English UI, dark theme) Settings → Printers → Local agent with the Windows agent Online (Windows logo, version) and, below, Printers on the local network with printers it has found. -->
<!-- PENDING (uncomment when the screenshot exists): ![El agente de Windows En línea en BolloPrint, con las impresoras que ha encontrado](/blog/media/2026-11-03-windows-agent/08-online.png) -->

En unos minutos, las impresoras que encuentra en tu red empiezan a salir en
**Impresoras por red local** (pulsa **Buscar ahora** si acabas de encender
una). Añade las que quieras: el
[tutorial de red local](/blog/connect-printers-local-network-agent) te lleva
marca por marca.

## El icono junto al reloj

El icono de BolloPrint es tu atajo al agente. Con un clic abres la página del
agente; con el botón derecho ves si el agente está en marcha, puedes
desinstalarlo o esconder el icono.

<!-- SCREENSHOT: 09-tray.png — the Windows 11 taskbar (English) with the BolloPrint icon's right-click menu open: «Open the agent's page», «The agent is running», «Uninstall…», «Hide this icon». -->
<!-- PENDING (uncomment when the screenshot exists): ![El menú del icono de BolloPrint en la barra de tareas de Windows](/blog/media/2026-11-03-windows-agent/09-tray.png "50%") -->

Ocultar el icono no para nada: el agente sigue funcionando y el icono vuelve la
próxima vez que inicies sesión. También tienes **Agente de BolloPrint** en el
menú Inicio.

## Mantenerlo al día

No tienes que hacer nada. Cuando sale una versión nueva, el agente la descarga,
comprueba que de verdad es nuestra y se reinicia con ella. Tus impresoras, su
historial y la vinculación con tu taller se quedan como están.

Si alguna vez quieres actualizarlo tú, descarga el instalador otra vez del
mismo sitio y ábrelo **encima** del que tienes. Recuerda tu carpeta y tu puerto,
así que es **Siguiente** hasta el final, y sigue siendo el mismo agente en el
mismo taller. No hace falta desinstalar antes ni volver a vincularlo.

## Moverlo o quitarlo

Reinstalarlo en el **mismo PC** no cambia nada: el agente recuerda quién es y
vuelve vinculado.

Llevarlo a **otro PC** es poner un agente nuevo: instálalo allí, vincúlalo y
añádele tus impresoras. Pasan a él con todo su historial. Después elimina el
agente antiguo en BolloPrint (**⋮** → **Eliminar** en su fila) y desinstálalo
del PC antiguo.

Para quitarlo de tu taller, elimínalo en BolloPrint (**⋮** → **Eliminar** en su
fila). El agente lo nota en unos segundos y su página vuelve a ofrecer
**Vincular con BolloPrint**; si lo vinculas otra vez, entra como un agente
nuevo.

Para desinstalarlo, botón derecho en el icono de BolloPrint → **Desinstalar…**,
o ve a **Configuración de Windows → Aplicaciones → Aplicaciones instaladas**,
busca **BolloPrint Agent** y desinstálalo desde ahí. Se quitan el programa, el
servicio, el icono y su permiso en el cortafuegos. Si no lo vas a usar más,
elimínalo también en BolloPrint.

## ¿Algo no va?

- **La página del agente no abre**: mira el icono de BolloPrint con el botón
  derecho. Si dice que el agente no responde, reinicia el PC. Si con eso no se
  arregla, puede que otro programa use el puerto: vuelve a pasar el instalador
  y elige **8364**.
- **«El enlace ha caducado o ya se usó»**: la confirmación dura solo un par de
  minutos. Vuelve a pulsar **Vincular con BolloPrint**.
- **No sale tu taller al vincular**: solo el dueño del taller puede vincular un
  agente.
- **No encuentra impresoras**: el PC y las impresoras no están en la misma red
  (una VPN, la red de invitados o un wifi aparte lo impiden). Añádelas por IP y
  funcionan igual.
- **Se desconecta todas las noches**: el PC se suspende. En **Configuración de
  Windows → Sistema → Energía**, pon que no se suspenda nunca cuando esté
  enchufado.

Todo lo demás, paso a paso, está en la guía
[**Agente en Windows**](/help/agente-en-windows).

Que disfrutes de tener tus impresoras a la vista, con el PC del taller haciendo de puente.

![Bollo, la mascota de BolloPrint, junto al logo de Windows](/blog/media/2026-11-03-windows-agent/10-bollo.webp "60%")
