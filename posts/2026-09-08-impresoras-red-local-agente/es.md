---
slug: connect-printers-local-network-agent
title: "Conecta tus impresoras por tu propia red: el agente local, paso a paso"
description: Prusa, Elegoo, Klipper, FlashForge, Bambu… Un agente pequeño en un equipo del taller, toda tu flota dentro de BolloPrint y sin tocar el router.
date: 2026-09-08
updated: 2026-10-12
tags: [tutoriales]
cover: 01-portada.webp
draft: true
---

Tus impresoras están en el taller. Tú, no siempre. Y cada vez que quieres saber
si una sigue imprimiendo, si ha salido bien o si le queda material, tienes que
estar delante.

Que estén en tu red no significa que tengas que estar tú. Para eso está el
**agente local**: un programa pequeño que vive en un equipo de tu taller, habla
con tus impresoras por tu propia red y le va contando a BolloPrint lo que ve.

- **No tocas el router.** Nada de abrir puertos, ni IP fija, ni cortafuegos.
- **Súper ligero.** Cualquier equipo que tengas ya encendido le sirve.
- **Uno para toda la flota**, por grande que sea.

::animation{id="local-agent"}

## Dónde lo pones

En **cualquier equipo del taller que no apagues**: un NAS, un mini-PC, una
Raspberry Pi, el PC del taller. Solo le pides dos cosas: que esté **siempre
encendido** y que tenga **Docker**.

Mejor aún si está **en la misma red que las impresoras**, porque así las
encuentra él solo. Si no puede, las añades a mano y funcionan exactamente igual.

## Paso 1 — Créalo en BolloPrint

Ve a **Configuración → Impresoras**, abre la pestaña **Agente local** y pulsa
**Nuevo agente**.

Ponle un nombre que te diga algo dentro de seis meses. Un consejo: **nómbralo por
dónde está, no por lo que es**. «Planta baja» o «Nave 2» te sirven; «Agente 1»,
no.

![La pestaña Agente local, con el botón de Nuevo agente](/blog/media/2026-09-08-impresoras-red-local-agente/02-nuevo-agente.png)

## Paso 2 — Copia la plantilla

Al crearlo, BolloPrint te enseña una **plantilla**: un texto que ya lleva dentro
todo lo tuyo —las claves de tu agente y la versión que toca— **ya escrito**. No
hay nada que sustituir ni que rellenar.

Elige el formato que uses (**Docker Compose** es el normal) y pulsa **Copiar**.

![La plantilla de despliegue, con el botón de copiar](/blog/media/2026-09-08-impresoras-red-local-agente/03-plantilla.png)

:::warning 🔐 Cópiala ahora: solo se enseña una vez
Las claves no caducan, pero no las volvemos a mostrar. Si pierdes la plantilla no
pasa nada grave: abres el agente y usas **Regenerar claves** para sacar una nueva.
:::

## Paso 3 — Pégala donde lo vayas a arrancar

Esto ya es en tu equipo, no en BolloPrint. Depende de dónde lo pongas:

**En un NAS Synology.** Instala **Container Manager** desde el **Centro de
paquetes**. Ve a **Proyecto → Crear**, pega la plantilla y dale a crear. Sin
escribir un solo comando.

**En Windows o Mac.** Instala **Docker Desktop**, guarda la plantilla en una
carpeta como `docker-compose.yml` y levántalo desde esa carpeta con
`docker compose up -d`.

**En Linux.** Instala **Docker** con el gestor de paquetes de tu distribución,
guarda la plantilla como `docker-compose.yml` y, desde esa carpeta,
`docker compose up -d`.

¿Usas **Portainer**? Pegas la misma plantilla en un stack y a desplegar.

:::info 💡 En Windows y Mac, las impresoras no se descubren solas
Ahí Docker corre dentro de una máquina virtual, que no ve los avisos que las
impresoras mandan a tu red. El agente funciona igual, pero las impresoras las
añades tú, como en el paso 6.
:::

## Paso 4 — Comprueba que está en línea

Vuelve a BolloPrint. En menos de un minuto, el agente pasa a **En línea**.

![El agente en estado En línea](/blog/media/2026-09-08-impresoras-red-local-agente/04-agente-online.png)

Si no aparece, casi siempre es una de estas tres: la plantilla **pegada a medias**,
el equipo **sin internet**, o un **cortafuegos** bloqueando la salida.

## Paso 5 — Tus impresoras aparecen solas

El agente **busca impresoras en tu red** por su cuenta, cada 15 minutos. Las que
encuentra salen en una lista con su marca y su modelo, y tú decides:

- **Añadir** — la das de alta y empieza a informar.
- **Ignorar** — no es tuya, o no la quieres aquí.

![Las impresoras encontradas en la red, con los botones de añadir e ignorar](/blog/media/2026-09-08-impresoras-red-local-agente/05-encontradas.png)

Si acabas de encender una máquina y no quieres esperar, hay un botón **Buscar
ahora**.

Algunas te van a pedir una **contraseña** al añadirlas. Depende de la marca, y lo
vemos en un momento.

## Paso 6 — Si alguna no aparece, la añades tú

Que una impresora no salga sola es **normal** en dos casos:

- **Está en otra red.** Los avisos de las impresoras no cruzan de una red a otra,
  así que no se descubren solas.
- **El agente corre en Windows o Mac.** Docker corre ahí en una máquina virtual,
  y tampoco se descubren solas.

**No pierdes nada por ello.** La añades tú y va exactamente igual, con cámara y
con mandos si esa máquina los tiene. Pulsas **Añadir por IP** y pones el tipo de
impresora, su dirección en tu red y, si la pide, su contraseña.

![El formulario de añadir una impresora por su IP](/blog/media/2026-09-08-impresoras-red-local-agente/06-anadir-por-ip.png "62%")

:::info 💡 Resérvale la IP en el router
Si el router le cambia la dirección a una impresora, la volvemos a buscar sola,
pero estará caída un rato. Reservarle la dirección evita ese hueco. Es un ajuste
del router, no de BolloPrint.
:::

## Qué te pide cada marca

Aquí es donde se atasca la gente. Lo resumimos:

| Marca | Qué tienes que hacer en la máquina | Cámara | ¿Puedes pausar y cancelar? |
|---|---|---|---|
| **Bambu Lab** | Activar el **Modo LAN** en su pantalla y usar el **código de acceso** que te enseña | Sí | Sí, si además activas el **Modo desarrollador** |
| **Prusa** (MK4, MK3.5, MK3.9, MINI, XL, CORE One) | Usar la **contraseña** que muestra la propia impresora | Todavía no | Sí |
| **Klipper** (QIDI, Sovol, Voron, RatRig, Creality K1…) | Normalmente nada: suele conectarse sin contraseña | Sí, si tienes webcam en tu Klipper | Sí |
| **Elegoo de resina** (Mars, Saturn, Jupiter) | Nada, no pide contraseña | En los modelos que la traen | Sí |
| **Elegoo Centauri Carbon 2** | Solo si tú le pusiste código en su pantalla | Sí | Todavía no |
| **FlashForge** (Adventurer 5M, 5M Pro, AD5X, Creator 5) | Activar **LAN Only** y usar el código de su pantalla | Sí | Todavía no |

:::warning ⚠️ Bambu Lab: el código de acceso CAMBIA
Cada vez que activas o desactivas el Modo LAN, Bambu **genera un código nuevo**.
Si una Bambu que iba bien deja de conectar de golpe, es esto nueve de cada diez
veces: mira otra vez el código en su pantalla y actualízalo en BolloPrint.
:::

:::info 💡 ¿No encuentras tu modelo en la tabla?
Mira en [impresoras compatibles](/help/impresoras-compatibles). Y si lleva
**Klipper** por dentro —cualquier máquina de montaje propio o modificada—
entra, aunque la marca no aparezca en ninguna lista.
:::

## Si ya tenías Bambu por la nube, no las dupliques

Cuando el agente encuentra en tu red una máquina que **ya tenías conectada por la
nube**, BolloPrint lo detecta y te lo dice: *«Es "P1S-02", que ya tienes por Bambu
Cloud»*. El botón es **Conectar también por LAN**.

Púlsalo, y no la vas a tener dos veces:

- Sigue siendo **una sola impresora**, con su número, su nombre y todo su
  historial.
- Ocupa **una sola plaza** de tu plan.
- Y gana la **cámara**, que es lo que no tenías por la nube.

![El aviso de que esa impresora ya está en Bambu Cloud, con el botón de conectar también por LAN](/blog/media/2026-09-08-impresoras-red-local-agente/07-tambien-por-lan.png)

:::warning ⚠️ El Modo LAN desconecta la nube de Bambu
Al activarlo, la impresora deja de hablar con la nube de Bambu Lab. A partir de
ahí, BolloPrint la ve por el agente.
:::

## Lo que ganas, en concreto

- **Casi todas las marcas.** Prusa, Elegoo, Klipper, QIDI, Sovol, FlashForge,
  Voron… Esto no lo da la nube, que solo existe para Bambu Lab.
- **Cámara.** Verla en directo mientras tienes la página delante, sacar una foto
  cuando quieras, y una foto final guardada en el historial de cada impresión.
  No es videovigilancia: no se graba nada.
- **Mandos.** Pausar, reanudar y cancelar desde BolloPrint, sin ir hasta la
  máquina, en las que lo permiten (mira la tabla de arriba). En Bambu Lab, con la
  impresora en **Modo LAN** y **Modo desarrollador**.
- **Aguanta los cortes de internet.** Si tu línea se cae, el agente **sigue
  leyendo las impresoras y guarda lo que pasa**. Cuando vuelve, lo manda todo. No
  pierdes esas horas de historial.
- **No dependes del fabricante** ni de que su nube siga funcionando.

Lo que no se puede por ninguna vía: **mandar trabajos a imprimir**. El fichero lo
sigues enviando desde tu laminador.

## Preguntas que nos hacen mucho

**¿Tengo que abrir puertos en el router?** No. Ni puertos, ni IP fija, ni reglas
de cortafuegos. Funciona detrás de un router doméstico normal.

**¿Hace falta un agente por impresora?** No. **Uno solo lleva la flota entera.**
Solo tiene sentido tener varios si tienes dos locales o dos redes separadas.

**¿Y si apago el equipo, o sale una versión nueva?** Al encenderlo, el agente
vuelve solo. Y se actualiza solo: cuando sale una versión nueva la descarga y se
reinicia con ella. Solo si te avisamos en pantalla tendrás que hacer algo tú.

:::info 💡 ¿Te has quedado atascado?
Escríbenos desde la [página de contacto](/contact) o abre un hilo en
[nuestro Discord](/help/soporte-por-discord). Si nos dices qué impresoras tienes,
te decimos exactamente qué hacer con cada una.
:::

## Documentación relacionada

- [Conectar impresoras](/help/conectar-impresoras) — las dos vías y cuál te conviene
- [El agente local](/help/el-agente-local) — la referencia completa
- [Desplegar el agente](/help/desplegar-el-agente) — el detalle técnico, si lo necesitas
- [Tipos de conexión](/help/tipos-de-conexion) — qué permite cada familia de impresora
- [Impresoras compatibles](/help/impresoras-compatibles) — busca aquí tu modelo
