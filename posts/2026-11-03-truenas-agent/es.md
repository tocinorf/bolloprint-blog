---
slug: install-bolloprint-agent-truenas
title: Instala el agente de BolloPrint en tu TrueNAS
description: Tu TrueNAS ya está encendido todo el día, en la misma red que tus impresoras. Pega un YAML en Install via YAML, pulsa un botón para vincularlo y tu flota aparece en BolloPrint. Sin comandos y sin tocar el router.
date: 2026-11-03
updated: 2026-11-03
tags: [tutoriales]
draft: true
---

Si tienes un TrueNAS en el taller, ya tienes el sitio perfecto para el agente de
BolloPrint. Está encendido las veinticuatro horas, está en la misma red que tus
impresoras y lleva años haciendo funcionar apps.

No vas a escribir ni un comando. Todo pasa en la interfaz web de TrueNAS: copias
un texto corto de BolloPrint, lo pegas en un recuadro y pulsas un botón para
vincular el agente con tu taller. Calcula diez minutos, la mitad esperando a que
termine la descarga.

:::info
Esto va solo de **instalar el agente en TrueNAS**. Qué es el agente, qué marcas
admite y cómo das de alta cada impresora está en el
[tutorial de red local](/blog/connect-printers-local-network-agent). La página
de referencia, con lo que hacer si algo falla, es
[Agente en TrueNAS](/help/agente-en-truenas), en el manual.
:::

:::warning Beta
El agente para TrueNAS está en **beta**: funciona, pero aún puede cambiar algún
paso. Si algo no cuadra con lo que ves en tu pantalla, cuéntanoslo.
:::

## Lo que necesitas

- **TrueNAS 24.10 o posterior** (Community Edition). Las versiones anteriores no
  tienen **Install via YAML**. La tuya la ves en **Dashboard → System
  Information**.
- **Las apps activadas.** La primera vez que abres **Apps**, TrueNAS te pide
  elegir el pool donde guardarlas. Si ya pone **Apps Service Running**, listo.
- Ser **dueño** de tu taller en BolloPrint. Solo los dueños pueden añadir un
  agente.
- Que el TrueNAS esté en la **misma red que tus impresoras** y salga a
  internet. Nada más: no hay que abrir puertos ni tener IP fija.

:::info 💡 No, no vas a tener que tocar el router
El agente **llama hacia fuera**, a BolloPrint, igual que cuando abres una página
web. Nunca recibe conexiones de internet.
:::

## 1. Copia el YAML de BolloPrint

En BolloPrint, ve a **Configuración → Impresoras → Agente local → Nuevo agente**
y elige **TrueNAS** en **Con un paquete o un instalador**. Verás cuatro pasos
cortos y, debajo, un recuadro con el **YAML**: el texto que le dice a TrueNAS qué
instalar. Pulsa **Copiar**.

![Nuevo agente → TrueNAS en BolloPrint: los cuatro pasos de instalación y el recuadro del YAML con su botón Copiar](/blog/media/2026-11-03-truenas-agent/01-bolloprint-new-agent-truenas.png)

No hay nada que crear ni ninguna clave que guardar: el YAML es el mismo para
todos los talleres. El agente nace cuando lo vinculas, en el paso 3.

:::info ¿Por qué un YAML y no el catálogo de apps?
El agente de BolloPrint aún no está en el catálogo de apps de TrueNAS. Mientras
no esté, TrueNAS lo instala como **app personalizada** a partir de este YAML.
Cuando esté en el catálogo, lo encontrarás en **Discover Apps** como cualquier
otra app.
:::

## 2. Instálalo en TrueNAS

1. En TrueNAS, abre **Apps** y pulsa **Discover Apps**.
2. Arriba a la derecha, junto a **Custom App**, abre el menú **⋮** y elige
   **Install via YAML**.

![La pantalla Discover de TrueNAS con el menú ⋮ abierto en Install via YAML](/blog/media/2026-11-03-truenas-agent/02-truenas-discover-menu.png)

3. En **Name**, escribe `bolloprint-agent`.
4. En **Custom Config**, pega el YAML que copiaste.
5. Pulsa **Save**.

![Install via YAML con el nombre bolloprint-agent y el YAML del agente pegado](/blog/media/2026-11-03-truenas-agent/03-truenas-install-via-yaml.png)

TrueNAS descarga el agente y lo arranca. En un minuto aparece en
**Apps → Installed** como **Running**.

![El agente en marcha en Apps → Installed, con el botón Web UI en Application Info](/blog/media/2026-11-03-truenas-agent/04-truenas-installed-web-ui.png)

## 3. Vincúlalo con tu taller

1. En **Apps → Installed**, pulsa **bolloprint-agent** y, en
   **Application Info**, pulsa **Web UI**. Se abre la página del agente en una
   pestaña nueva.
2. La página dice que el agente todavía no pertenece a ningún taller y enseña un
   **código** de ocho caracteres. Pulsa **Vincular con BolloPrint**.

![La página del agente en TrueNAS, aún sin vincular, con su código y el botón Vincular con BolloPrint](/blog/media/2026-11-03-truenas-agent/05-agent-page.png)

3. Se abre BolloPrint. Inicia sesión si no la tienes iniciada y elige el taller
   al que lo añades.
4. BolloPrint te enseña el **equipo** (tu TrueNAS) y el **código**. Comprueba que
   es **el mismo código** que salía en la página del agente, ponle un nombre al
   agente y pulsa **Añadir al taller**.

<!-- SCREENSHOT 06-bolloprint-add-agent.png: BolloPrint (English UI), the «Add an agent to <workshop>» screen — Device «truenas · TrueNAS», the code, the Agent name field and the Add to workshop button. -->

Ya está. De vuelta en **Configuración → Impresoras → Agente local**, el agente
nuevo sale con el logo de TrueNAS y **En línea**, y su página ahora dice que está
vinculado a tu taller.

<!-- SCREENSHOT 07-bolloprint-agent-online.png: BolloPrint (English UI), Settings → Printers → Local agent — the TrueNAS agent in the list, Online, with its version. -->

:::warning Confirma solo lo que acabas de pulsar tú
Si alguna vez te llega un enlace para «añadir un agente» que no has pedido,
ciérralo. Un agente solo se vincula desde su propia página, en tu red.
:::

## 4. Dale las impresoras

El agente empieza a buscar impresoras en tu red en cuanto se vincula. Lo que
encuentra aparece en **Impresoras por red local**, debajo de la lista de agentes,
y desde ahí las das de alta. Las que no aparezcan solas, con **Añadir por IP**.

Cómo hacerlo con cada marca está en el
[tutorial de red local](/blog/connect-printers-local-network-agent).

## Mantenerlo al día

No tienes que hacer nada: **el agente se actualiza solo**. Cuando sale una
versión nueva, la descarga, comprueba que es nuestra y se reinicia con ella. La
guarda en su carpeta de datos, así que sigue en esa versión aunque reinicies la
app o el TrueNAS.

Por eso TrueNAS sigue diciendo **Up to date** y la línea `image:` del YAML no
cambia: es la versión con la que se instaló, no la que está corriendo. La que
corre te la enseña BolloPrint, junto al agente.

Solo si BolloPrint te avisa alguna vez de que un agente necesita una
**actualización manual**: abre **Apps → Installed → bolloprint-agent → Edit**,
cambia **solo la versión** del final de la línea `image:` por la que enseña
BolloPrint en **Nuevo agente → TrueNAS** y pulsa **Save**. Sigue vinculado, con
las mismas impresoras y su historial.

![Edit App YAML en TrueNAS: lo único que hay que cambiar es la versión del final de la línea image](/blog/media/2026-11-03-truenas-agent/08-truenas-edit-yaml.png)

:::warning No lo borres para actualizar
Borrar la app borra también su carpeta de datos. Si la vuelves a instalar
después, es un agente **nuevo** que hay que vincular. Para actualizar, usa
siempre **Edit**.
:::

## Moverlo o quitarlo

- **A otro equipo, o en una instalación de cero:** es un agente nuevo. Instálalo
  y vincúlalo como arriba, añade tus impresoras con él (pasan con su historial)
  y elimina el agente antiguo en BolloPrint.
- **Para quitarlo:** elimina primero el agente en BolloPrint (**Configuración →
  Impresoras → Agente local**, menú **⋮** del agente → **Eliminar**). En unos
  segundos su página vuelve a ofrecer **Vincular con BolloPrint**. Después borra
  la app en TrueNAS (**Apps → Installed → bolloprint-agent → Delete**).

Si algo no se comporta como cuenta este artículo, la página
[Agente en TrueNAS](/help/agente-en-truenas) del manual tiene una tabla con lo
que hacer: un puerto ocupado, una app que no arranca, un agente que sale
desconectado.

Que disfrutes de tener tus impresoras a la vista, con tu TrueNAS haciendo de puente.

![Bollo, la mascota de BolloPrint, junto al logo de TrueNAS](/blog/media/2026-11-03-truenas-agent/10-bollo.webp "60%")

## Documentación relacionada

- [Agente en TrueNAS](/help/agente-en-truenas): la referencia completa, con lo que hacer si algo falla
- [El agente local](/help/el-agente-local): qué es y qué impresoras conecta
- [Impresoras por red local](/help/impresoras-por-red-local): dar de alta cada marca cuando el agente ya está en línea
- [Agente en Docker](/help/agente-en-docker): si prefieres ponerlo en cualquier ordenador con Docker
