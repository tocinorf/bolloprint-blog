---
slug: install-bolloprint-agent-synology
title: Instalar el agente de BolloPrint en un Synology
description: Si tienes un Synology en el taller, ahí va el agente. Un paquete de DSM que se instala desde el Centro de paquetes y se vincula con un clic. Sin Docker, sin códigos que copiar y sin tocar el router.
date: 2026-11-02
updated: 2026-11-02
tags: [tutoriales]
draft: true
---

Si tienes un Synology en el taller, ya tienes dónde poner el agente de
BolloPrint. Está encendido día y noche, está en la misma red que las impresoras
y ya hace funcionar el resto de tus pequeños servicios.

El agente viene como **paquete de DSM**: se instala como cualquier otra
aplicación de Synology y aparece en el menú principal de DSM. Sin Docker, sin
Container Manager, sin textos que pegar y sin códigos que copiar. Calcula diez
minutos.

:::info
Esto va solo de **instalar el agente en un Synology**. Qué es el agente, qué
marcas admite y cómo das de alta cada impresora está en el
[tutorial de red local](/blog/connect-printers-local-network-agent). Cuando
termines aquí, sigue por ahí.
:::

:::warning El paquete para Synology está en beta
Funciona, pero aún puede cambiar algún paso. Si algo de tu pantalla no cuadra
con lo que lees aquí, cuéntanoslo.
:::

## Por qué en el NAS y no en tu portátil

Porque el agente solo sirve si está despierto. Si lo pones en el ordenador que
apagas al irte, esas horas no las ves: ni qué imprimió, ni cuánto tardó, ni si
se paró a las tres de la mañana. El NAS ya está encendido de todas formas.

Lo demás viene de regalo: está en la red de las impresoras, que es lo que le
permite encontrarlas solo, y es ligero: el NAS sigue con todo lo demás
como siempre.

:::info 💡 No, no vas a tener que tocar el router
El agente **llama hacia fuera**, a BolloPrint, igual que cuando abres una página
web. Nunca recibe conexiones de internet: nada de abrir puertos, ni IP fija, ni
reglas de cortafuegos. Funciona igual detrás de un router doméstico o de una
fibra con CGNAT.
:::

## Lo que necesitas antes de ponerte

Mejor mirarlo ahora que a mitad:

- **DSM 7 o posterior.** Lo ves en **Panel de control → Centro de
  información**. Con DSM 6 no funciona.
- **El procesador de tu NAS.** En el mismo **Centro de información**. Intel o
  AMD son de 64 bits; si es ARM, la ficha de tu modelo en la web de Synology
  dice si es de 64 o de 32 bits. Lo necesitas para elegir la descarga.
- **Un usuario administrador de DSM.** Solo los administradores pueden instalar
  paquetes y abrir la página del agente.
- **Ser dueño del taller en BolloPrint.** Al vincular el agente solo salen los
  talleres de los que eres dueño.
- **El NAS y las impresoras en la misma red.** En redes separadas (VLANs) el
  agente funciona igual, pero tendrás que añadir cada impresora por su IP.

## 1. Descarga el paquete

En BolloPrint, ve a **Configuración → Impresoras → Agente local → Nuevo agente**
y elige **Synology**.

Hay un botón de descarga por tipo de procesador: **Intel o AMD (64 bits)**,
**ARM (64 bits)** y **ARM (32 bits)**. Pulsa el tuyo. Se descarga un fichero que
acaba en `.spk`: es un paquete de DSM.

<!-- SCREENSHOT: 01-new-agent-synology.png — la misma captura que en en.md (interfaz en inglés). -->

Fíjate en lo que **no** hay en esa pantalla: ni código, ni clave, nada que
crear. El agente nace cuando lo vinculas, en el paso 3.

## 2. Instálalo desde el Centro de paquetes

Abre DSM en el navegador y entra en el **Centro de paquetes**. Arriba a la
derecha, pulsa **Instalación manual**, luego **Examinar**, elige el `.spk` que
acabas de descargar y pulsa **Siguiente**.

<!-- SCREENSHOT: 02-manual-install.png — la misma captura que en en.md. -->

DSM te avisa de que el paquete no lo publica Synology. Acéptalo para seguir.

El asistente te enseña un solo ajuste: el **puerto de la página del agente**,
con **8257** ya puesto. Déjalo así salvo que DSM te diga que está ocupado; en
ese caso, pon **8364**. Pulsa **Siguiente** y, en el resumen, **Hecho**.

<!-- SCREENSHOT: 03-install-wizard.png — la misma captura que en en.md. -->

Al minuto el paquete sale **En ejecución** y **BolloPrint Agent** aparece en el
menú principal de DSM.

:::info 💡 «Este paquete no es compatible con tu modelo»
Has bajado el paquete de otro procesador. Vuelve a BolloPrint y descarga el
otro.
:::

## 3. Vincúlalo con tu taller

Este es el paso que sustituye al antiguo «copia este código y pégalo allí».

Abre el **menú principal** de DSM (el icono de arriba a la izquierda) y pulsa
**BolloPrint Agent**. Se abre en una pestaña nueva la página del propio agente:
dice que todavía no pertenece a ningún taller y enseña un **código** corto.

![La página del agente, aún sin vincular, con su código y el botón Vincular con BolloPrint](/blog/media/2026-09-10-agente-synology/04-agent-page.png)

Pulsa **Vincular con BolloPrint**. Se abre BolloPrint (inicia sesión si hace
falta) y te pregunta a qué taller va. Luego te enseña el **equipo** —el nombre
de tu NAS y «Synology»— y el **código**. Comprueba que es **el mismo** que
enseñaba la página del agente y pulsa **Añadir al taller**.

<!-- SCREENSHOT: 05-confirm.png — la misma captura que en en.md. -->

Vuelves a la página del agente, que ahora dice **Vinculado a** tu taller.

:::warning 🔐 Confirma solo lo que acabas de pulsar tú
Si alguna vez te llega un enlace para «añadir un agente» que no has pedido,
ciérralo. Un agente solo se vincula desde su propia página, y en un Synology esa
página solo la abre un administrador de tu NAS.
:::

## 4. Comprueba que va

En BolloPrint, **Configuración → Impresoras → Agente local**: ahí está el agente,
con el nombre de tu NAS y el logo de Synology, **En línea**. Esa es la buena:
significa que el circuito entero funciona.

<!-- SCREENSHOT: 06-agent-online.png — la misma captura que en en.md. -->

En un minuto o así empieza a encontrar impresoras en tu red. Salen en
**Impresoras por red local** y las das de alta desde ahí; las que no aparezcan
solas, con **Añadir por IP**. Marca por marca, todo está en el
[tutorial de red local](/blog/connect-printers-local-network-agent).

## Actualizarlo

Actualizar es **instalar el paquete nuevo encima del que tienes**: vuelve a
descargarlo desde el mismo sitio en BolloPrint y, en el **Centro de paquetes →
Instalación manual**, elige el fichero nuevo. DSM ve que ya está instalado y lo
actualiza, sin volver a preguntar el puerto. El agente sigue vinculado al mismo
taller, con las mismas impresoras y todo su historial.

Cuando el paquete esté en el catálogo del Centro de paquetes de Synology, el
propio Centro de paquetes te avisará y actualizar será un clic.

:::warning No lo desinstales para actualizar
Desinstalar borra la identidad del agente: lo que instales después es un agente
**nuevo** que hay que vincular otra vez. Para actualizar, instala siempre
encima.
:::

## Moverlo o empezar de cero

Un agente no se «traslada», pero tampoco hace falta: lo que se mueve son las
impresoras, y se mueven con todo su historial.

1. Instala el paquete en el NAS nuevo y vincúlalo. Aparece como un segundo
   agente.
2. Abre cada impresora con **Editar** en su menú **⋮** y cámbiala al agente
   nuevo.
3. Cuando el antiguo se quede sin impresoras, **elimínalo** desde su fila.

Para quitar el agente del todo: en DSM, **Centro de paquetes → BolloPrint Agent
→ Acción → Desinstalar**, y luego elimina el agente en BolloPrint.

## Si algo no sale

| Lo que ves | Qué suele ser |
|---|---|
| El asistente dice que el puerto 8257 está ocupado | Lo usa otra aplicación del NAS. Pon 8364 y sigue. |
| «No es compatible con tu modelo» | El paquete de otro procesador. Descarga el que toca. |
| Al abrir BolloPrint Agent te pide iniciar sesión en DSM | Ábrelo desde el menú principal de DSM, con la sesión de un administrador. |
| La página dice que el agente no responde | El paquete está parado o arrancando. En el Centro de paquetes, **Acción → Ejecutar**, y espera unos segundos. |
| Al vincular no sale tu taller | Solo salen los talleres de los que eres **dueño**. Pide al dueño que lo vincule. |
| Tras reiniciar el NAS tarda en volver | Dale unos minutos: arranca con DSM y reintenta solo hasta que el NAS tiene internet. |
| No encuentra ninguna impresora | ¿Misma red? Si no, añádelas por IP. Si tienes el cortafuegos de DSM activado, permite los puertos de BolloPrint Agent (sale en la lista de aplicaciones al crear una regla). |

## ¿Prefieres Docker?

Si tu NAS ya usa Container Manager y prefieres tenerlo todo en contenedores, el
agente también funciona como contenedor. Los pasos están en
[Desplegar el agente](/help/desplegar-el-agente). Para la mayoría de talleres el
paquete es más sencillo: es una aplicación de DSM como cualquier otra y se
vincula con un clic.

## Para seguir leyendo

- [Agente en Synology](/help/agente-en-synology) — la guía completa: instalar, actualizar, mover, desinstalar y qué hacer si algo falla
- [El agente local](/help/el-agente-local) — qué hace, varios agentes y diagnóstico
- [Impresoras por red local](/help/impresoras-por-red-local) — dar de alta las máquinas
- [Impresoras compatibles](/help/impresoras-compatibles) — busca aquí tu modelo
