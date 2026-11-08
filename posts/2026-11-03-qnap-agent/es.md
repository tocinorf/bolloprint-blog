---
slug: install-bolloprint-agent-qnap
title: "El agente de BolloPrint en un QNAP: instálalo desde el App Center, sin Docker"
description: Si en tu taller ya hay un QNAP, el agente puede vivir ahí como una aplicación más. Descargas un fichero desde BolloPrint, lo instalas en el App Center y lo vinculas pulsando un botón. Ya en beta.
date: 2026-11-03
updated: 2026-11-03
tags: [tutoriales]
draft: true
---

Si en tu taller hay un QNAP, ya tienes el mejor sitio para el agente. Está
encendido día y noche, está en la misma red que tus impresoras y nadie lo
apaga al acabar la jornada.

Hasta ahora, ponerlo ahí era cosa de Container Station y de una plantilla de
Docker. Ya no: el agente viene ahora como **aplicación nativa de QNAP**.
Descargas un fichero desde BolloPrint, lo instalas en el App Center como
cualquier otra aplicación y lo vinculas a tu taller con un solo botón. Sin
comandos, sin plantillas, sin códigos que copiar y sin tocar nada del router.

Calcula diez minutos, casi todos esperando al App Center.

:::warning 🧪 Esto es una beta
Lo hemos probado de principio a fin en QTS 5.2 con procesador Intel. Los
paquetes para procesadores ARM también están publicados, pero aún no los hemos
visto funcionar en un QNAP de verdad. Si tienes uno, cuéntanos cómo te ha ido:
vaya bien o mal, nos ayuda.
:::

:::info
Esto va solo de **instalar el agente en un QNAP**. Qué es el agente, qué marcas
admite y cómo añades cada impresora está en el
[tutorial de red local](/blog/connect-printers-local-network-agent). Cuando
termines aquí, sigue por ahí.
:::

## Por qué en el NAS y no en tu portátil

Porque el agente solo sirve si está despierto. Si lo pones en el ordenador que
apagas al irte, esas horas no las ves: ni qué imprimió, ni cuánto tardó, ni si
se paró a las tres de la mañana. El NAS ya está encendido de todas formas.

Lo demás viene de regalo: está en la red de las impresoras, que es lo que le
permite al agente encontrarlas solo, y es ligero: no necesita un equipo
potente y convive con todo lo que ya tiene en marcha tu NAS.

:::info 💡 No vas a tener que tocar el router
El agente **llama hacia fuera**, igual que tu navegador cuando abres una página
web. Nunca recibe conexiones de internet: nada de abrir puertos, ni IP fija, ni
reglas de cortafuegos.
:::

## Lo que necesitas antes de empezar

- **Un QNAP con QTS 4.5 o posterior**, siempre encendido y en la misma red que
  tus impresoras. Si están en redes distintas (VLAN, red de invitados), el
  agente funciona igual, pero tendrás que añadir las impresoras por su IP en
  vez de que las encuentre solo.
- **Una cuenta de administrador de QTS.** Hace falta para instalar
  aplicaciones y para abrir la página del agente.
- **Ser el dueño del taller** en BolloPrint. Solo el dueño puede añadir
  agentes.
- **Saber qué procesador tiene tu QNAP.** Lo ves en la ficha de tu modelo en la
  web de QNAP, o en QTS, en **Panel de control → Sistema → Estado del sistema**.
  La mayoría de modelos son Intel o AMD; algunos, como las series TS-x33 o
  TS-x31P, son ARM.

## Paso 1: descarga el paquete desde BolloPrint

El agente aún no está en la tienda de QNAP, así que lo bajas desde BolloPrint,
y solo desde BolloPrint.

1. Ve a **Configuración → Impresoras** y abre la pestaña **Agente local**.
2. Pulsa **Nuevo agente** y elige la tarjeta **QNAP**, en **Con un paquete o un
   instalador**.

![La ventana «Nuevo agente local» de BolloPrint: la tarjeta de QNAP entre los agentes que se instalan con un paquete o un instalador](/blog/media/2026-11-03-qnap-agent/01-new-agent-qnap-card-en.png)

3. Elige la descarga de tu procesador: **Intel o AMD (64 bits)**,
   **ARM (64 bits)** o **ARM (32 bits)**. Se descarga un fichero que termina en
   `.qpkg`.

![La tarjeta de QNAP en BolloPrint: tres descargas, una por procesador, y los seis pasos de instalación en «Cómo instalarlo»](/blog/media/2026-11-03-qnap-agent/02-qnap-downloads-en.png)

Si no sabes qué procesador tiene el tuyo, la tarjeta te enlaza a la web de
QNAP. En **Cómo instalarlo** tienes los mismos pasos que en este artículo,
resumidos. Aquí no se crea nada todavía en BolloPrint: el agente aparecerá en
tu lista cuando lo vincules.

## Paso 2: permite aplicaciones sin la firma de QNAP

QNAP firma las aplicaciones de su tienda. La nuestra está pendiente de
publicarse allí, así que de momento llega sin esa firma y QTS necesita tu
permiso para instalarla.

1. Entra en QTS con tu cuenta de administrador y abre el **App Center**.
2. Abre sus opciones (el icono ⚙ arriba a la derecha).
3. Activa **Permitir la instalación de aplicaciones sin una firma digital
   válida** y guarda.

<!-- SCREENSHOT 03-app-center-settings-en.png: QTS (English), App Center → Settings, the «Allow installation of applications without a valid digital signature» option turned on. -->

Si prefieres no dejarla activada, puedes desactivarla en cuanto esté instalado
el agente. Tendrás que volver a activarla para la próxima actualización.

## Paso 3: instala el paquete

1. En el App Center, pulsa el icono de **instalación manual**: unas cajitas con
   un **+**, arriba a la derecha, justo a la izquierda del ⚙ (al pasar el ratón
   pone **Instalar**).
2. Elige el fichero `.qpkg` que has descargado y pulsa **Instalar**.

<!-- SCREENSHOT 04-install-manually-en.png: QTS (English), App Center «Install Manually» dialog with BolloPrintAgent_<version>_x86_64.qpkg selected. -->

3. QTS te avisa de que la aplicación no tiene una firma digital válida. Es lo
   esperado: **acéptalo** y la instalación sigue.

<!-- SCREENSHOT 05-signature-warning-en.png: QTS (English), the digital signature warning shown while installing the BolloPrint Agent package. -->

Cuando termine, **BolloPrint Agent** aparece entre tus aplicaciones.

<!-- SCREENSHOT 06-app-center-installed-en.png: QTS (English), App Center → My Apps with «BolloPrint Agent» installed and its «Open» button visible. -->

## Paso 4: vincúlalo con tu taller

Pulsa **Abrir**. QTS te lleva a la página del agente. Solo la ve un
administrador de QTS con la sesión iniciada; a cualquier otra persona le pide
que entre primero.

La página dice que el agente todavía no pertenece a ningún taller y enseña un
**código** corto.

![La página del agente en el QNAP: aún sin vincular, con su código y el botón «Vincular con BolloPrint»](/blog/media/2026-11-03-qnap-agent/07-agent-page-en.png)

1. Pulsa **Vincular con BolloPrint**. Se abre BolloPrint en tu navegador (inicia
   sesión si no la tenías abierta).
2. Si eres dueño de más de un taller, elige a cuál añades el agente.
3. Comprueba que el **código** que enseña BolloPrint es el mismo que el de la
   página del agente y pulsa **Añadir al taller**.

<!-- SCREENSHOT 08-add-to-workshop-en.png: BolloPrint (English UI), the «Add an agent to …» confirmation page with the device name, the code and the «Add to workshop» button. -->

4. Vuelves a la página del agente, que ahora dice **Vinculado a** y el nombre
   de tu taller.

:::warning 🔐 Vincula solo lo que acabas de instalar
Sigue adelante en BolloPrint solo si acabas de pulsar **Vincular con BolloPrint**
en tu propio QNAP. Si alguien te manda un enlace para «vincular un agente»,
ciérralo.
:::

## Paso 5: comprueba que está en línea

Vuelve a **Configuración → Impresoras → Agente local**. En menos de un minuto
el agente nuevo sale **En línea**, con el logo de QNAP al lado.

<!-- SCREENSHOT 09-agent-online-en.png: BolloPrint (English UI), Settings → Printers → Local agent with the QNAP agent online and the QNAP logo on its row. -->

A partir de aquí funciona como cualquier otro agente: las impresoras de tu red
aparecen solas para que las añadas, o las añades por su IP. El
[tutorial de red local](/blog/connect-printers-local-network-agent) te lleva
marca por marca.

## Actualizarlo más adelante

Normalmente no haces nada: **el agente se actualiza solo**. Cuando sale una
versión nueva, la descarga, comprueba que es nuestra y se reinicia con ella.

Solo si BolloPrint te avisa de que tu agente necesita una **actualización
manual** instalas el paquete nuevo encima del antiguo: descárgalo desde la
misma tarjeta de QNAP en BolloPrint (la del mismo procesador), comprueba que
sigue activada la opción de las aplicaciones sin firma y vuelve a usar el icono
de **instalación manual**. QTS sustituye el programa y deja intactos sus datos,
así que el agente sigue vinculado, con sus impresoras y su historial. No hay
que volver a vincular nada.

## Moverlo o quitarlo

- **Reinstalarlo o moverlo a otro NAS** es vincular un agente nuevo. Instálalo
  en el equipo nuevo, vincúlalo y después elimina el antiguo en BolloPrint,
  desde el menú **⋮** de su fila. Tus impresoras pasan al agente nuevo, con
  todo su historial, en cuanto las añadas.
- **Para quitarlo**, elimina primero el agente en BolloPrint, desde el menú
  **⋮** de su fila, y luego abre **BolloPrint Agent** en el App Center y pulsa
  **Eliminar**. Si solo lo eliminas en BolloPrint, el agente se queda instalado
  sin taller y su página vuelve a ofrecer **Vincular con BolloPrint**.

## Si algo no va

- **QTS no deja instalar el fichero**: revisa la opción de las aplicaciones sin
  firma. Si dice que el paquete no es compatible, has bajado el de otro
  procesador.
- **«Abrir» te pide que inicies sesión en QTS**: la página solo se abre a un
  administrador. Entra con una cuenta de administrador y vuelve a pulsar
  **Abrir**.
- **Al vincular dice que no ha podido hablar con BolloPrint**: el QNAP necesita
  salida a internet. Comprueba su conexión y su DNS en **Panel de control →
  Red**.
- **No encuentra ninguna impresora**: si el QNAP y las impresoras están en
  redes distintas, añádelas por IP. Si están en la misma red y aun así no
  salen, añádelas por IP y cuéntanoslo: nos ayuda a terminar la beta.

La lista completa está en la [guía del agente en QNAP](/help/agente-en-qnap).

:::info 💡 ¿Necesitas ayuda?
Escríbenos desde la [página de contacto](/contact) o abre un hilo en
[nuestro Discord](/help/soporte-por-discord). Dinos tu modelo de QNAP y te
ayudamos con el resto.
:::

Que disfrutes de tener tus impresoras a la vista, con tu QNAP haciendo de puente.

![Bollo, la mascota de BolloPrint, junto al logo de QNAP](/blog/media/2026-11-03-qnap-agent/10-bollo.webp "60%")

## Documentación relacionada

- [Agente en QNAP](/help/agente-en-qnap): la guía completa, con la actualización y los problemas habituales
- [El agente local](/help/el-agente-local): la referencia completa
- [Agente en Docker](/help/agente-en-docker): si prefieres usar Container Station (Docker)
- [Impresoras compatibles](/help/impresoras-compatibles): busca aquí tu modelo
