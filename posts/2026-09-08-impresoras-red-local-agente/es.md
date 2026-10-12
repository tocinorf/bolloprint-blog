---
slug: connect-printers-local-network-agent
title: "Conecta tus impresoras por tu propia red: el agente local, paso a paso"
description: Prusa, Elegoo, Klipper, FlashForge, Bambu… Un agente pequeño en un equipo del taller, toda tu flota dentro de BolloPrint y sin tocar el router.
date: 2026-10-12
tags: [tutoriales]
cover: 01-portada.webp
---

Tus impresoras están en el taller, pero tú no siempre. Y para saber si una sigue
imprimiendo, si ha salido bien o si le queda material, tienes que estar delante.

Para eso está el **agente local**: un programa pequeño que funciona en un equipo
de tu taller, habla con tus impresoras por tu propia red y le cuenta a BolloPrint
lo que ve.

- **No tocas el router**: ni puertos abiertos, ni IP fija, ni cortafuegos.
- **Es muy ligero**: le sirve cualquier equipo que ya tengas encendido.
- **Con uno basta para toda la flota**, sea del tamaño que sea.

::animation{id="local-agent"}

## Dónde instalarlo

El agente vive en **cualquier equipo del taller que no apagues**: un NAS, un
mini-PC, una Raspberry Pi o el PC del taller. Solo necesita que esté **siempre
encendido** y que tenga **Docker**.

Lo ideal es que esté **en la misma red que las impresoras**, porque así las
encuentra él solo. Si no es posible, las añades a mano y funcionan igual.

## Crea el agente en BolloPrint

Empieza en BolloPrint. Ve a **Configuración → Impresoras**, abre la pestaña
**Agente local** y pulsa **Nuevo agente**.

Ponle un nombre que te siga diciendo algo dentro de seis meses: **nómbralo por
dónde está, no por lo que es**. «Planta baja» o «Nave 2» sirven; «Agente 1», no.

![La pestaña Agente local, con el botón de Nuevo agente](/blog/media/2026-09-08-impresoras-red-local-agente/02-nuevo-agente.png)

## Copia la plantilla

Al crearlo, BolloPrint te muestra una **plantilla**: un texto que ya lleva
**escrito** todo lo tuyo, las claves de tu agente y la versión que toca. No hay
nada que sustituir ni que rellenar.

Elige el formato que uses (**Docker Compose** es el habitual) y pulsa **Copiar**.

![La plantilla de despliegue, con el botón de copiar](/blog/media/2026-09-08-impresoras-red-local-agente/03-plantilla.png)

:::warning 🔐 Cópiala ahora: solo se muestra una vez
Las claves no caducan, pero no las volvemos a mostrar. Si pierdes la plantilla,
abre el agente y usa **Regenerar claves** para obtener una nueva.
:::

## Pega la plantilla en tu equipo

Esto ya se hace en tu equipo, no en BolloPrint, y depende de dónde lo instales:

- **NAS Synology**: instala **Container Manager** desde el **Centro de paquetes**,
  ve a **Proyecto → Crear**, pega la plantilla y créalo. Sin escribir ningún
  comando.
- **Windows o Mac**: instala **Docker Desktop**, guarda la plantilla en una
  carpeta como `docker-compose.yml` y, desde esa carpeta, ejecuta
  `docker compose up -d`.
- **Linux**: instala **Docker** con el gestor de paquetes de tu distribución,
  guarda la plantilla como `docker-compose.yml` y ejecuta ahí
  `docker compose up -d`.
- **Portainer**: pega la misma plantilla en un stack y despliégalo.

:::info 💡 En Windows y Mac, las impresoras no se descubren solas
Ahí Docker corre dentro de una máquina virtual, que no ve los avisos que las
impresoras envían a tu red. El agente funciona igual, pero las impresoras las
añades tú, como se explica más abajo.
:::

## Comprueba que está en línea

Vuelve a BolloPrint: en menos de un minuto, el agente pasa a **En línea**.

![El agente en estado En línea](/blog/media/2026-09-08-impresoras-red-local-agente/04-agente-online.png)

Si no lo hace, casi siempre es por una de tres causas: la plantilla se **pegó a
medias**, el equipo **no tiene internet** o un **cortafuegos** bloquea la salida.

## Tus impresoras aparecen solas

Desde ese momento, el agente **busca impresoras en tu red** por su cuenta cada 15
minutos. Las que encuentra aparecen en una lista con su marca y su modelo, y tú
decides:

- **Añadir**: la das de alta y empieza a informar.
- **Ignorar**: no es tuya o no la quieres aquí.

![Las impresoras encontradas en la red, con los botones de añadir e ignorar](/blog/media/2026-09-08-impresoras-red-local-agente/05-encontradas.png)

Si acabas de encender una máquina y no quieres esperar, pulsa **Buscar ahora**.
Algunas marcas piden una **contraseña** al añadir la impresora; lo vemos más
abajo.

## Si alguna no aparece, añádela tú

Que una impresora no aparezca sola es **normal** en dos casos:

- **Está en otra red.** Los avisos de las impresoras no pasan de una red a otra.
- **El agente funciona en Windows o Mac.** Ahí Docker corre en una máquina
  virtual.

No pierdes nada por ello: la añades tú y funciona exactamente igual, con cámara y
con mandos si esa máquina los tiene. Pulsa **Añadir por IP** e indica el tipo de
impresora, su dirección en tu red y, si la pide, su contraseña.

![El formulario de añadir una impresora por su IP](/blog/media/2026-09-08-impresoras-red-local-agente/06-anadir-por-ip.png "62%")

:::info 💡 Resérvale la IP en el router
Si el router le cambia la dirección a una impresora, la volvemos a buscar sola,
pero estará caída un rato. Reservarle la dirección evita ese hueco. Es un ajuste
del router, no de BolloPrint.
:::

## Qué te pide cada marca

Aquí es donde surgen más dudas. En resumen:

| Marca | Qué tienes que hacer en la máquina | Cámara | ¿Puedes pausar y cancelar? |
|---|---|---|---|
| **Bambu Lab** | Activar el **Modo LAN** en su pantalla y usar el **código de acceso** que te enseña | Sí | Sí, si además activas el **Modo desarrollador** |
| **Prusa** (MK4, MK3.5, MK3.9, MINI, XL, CORE One) | Usar la **contraseña** que muestra la propia impresora | Todavía no | Sí |
| **Klipper** (QIDI, Sovol, Voron, RatRig, Creality K1…) | Normalmente nada: suele conectarse sin contraseña | Sí, si tienes webcam en tu Klipper | Sí |
| **Elegoo de resina** (Mars, Saturn, Jupiter) | Nada, no pide contraseña | En los modelos que la traen | Sí |
| **Elegoo Centauri Carbon 2** | Solo si tú le pusiste código en su pantalla | Sí | Todavía no |
| **FlashForge** (Adventurer 5M, 5M Pro, AD5X, Creator 5) | Activar **LAN Only** y usar el código de su pantalla | Sí | Todavía no |

:::warning ⚠️ Bambu Lab: el código de acceso cambia
Cada vez que activas o desactivas el Modo LAN, Bambu **genera un código nuevo**.
Si una Bambu que funcionaba bien deja de conectar de repente, nueve de cada diez
veces es por esto: mira otra vez el código en su pantalla y actualízalo en
BolloPrint.
:::

:::info 💡 ¿No encuentras tu modelo en la tabla?
Consulta las [impresoras compatibles](/help/impresoras-compatibles). Si lleva
**Klipper** por dentro (cualquier máquina de montaje propio o modificada), es
compatible aunque la marca no aparezca en ninguna lista.
:::

## Lo que ganas con el agente local

Con el agente en marcha, obtienes:

- **Casi todas las marcas**: Prusa, Elegoo, Klipper, QIDI, Sovol, FlashForge,
  Voron… La nube no lo ofrece, porque solo existe para Bambu Lab.
- **Cámara**: en directo mientras tienes la página abierta, una foto cuando
  quieras y una foto final guardada en el historial de cada impresión. No es
  videovigilancia: no se graba nada.
- **Mandos**: pausar, reanudar y cancelar desde BolloPrint, sin ir hasta la
  máquina, en las que lo permiten (mira la tabla de arriba). En Bambu Lab, con la
  impresora en **Modo LAN** y **Modo desarrollador**.
- **Resistencia a los cortes de internet**: si se cae tu línea, el agente **sigue
  leyendo las impresoras y guarda lo que pasa**. Al volver la conexión lo envía
  todo, y no pierdes esas horas de historial.
- **Independencia del fabricante** y de que su nube siga funcionando.

Lo que no permite ninguna vía es **mandar trabajos a imprimir**: el fichero lo
sigues enviando desde tu laminador.

## Preguntas frecuentes

Las dudas que más nos llegan.

### ¿Tengo que abrir puertos en el router?

No. Ni puertos, ni IP fija, ni reglas de cortafuegos. Funciona detrás de un router
doméstico normal.

### ¿Hace falta un agente por impresora?

No. **Uno solo lleva la flota entera.** Solo tiene sentido tener varios si tienes
dos locales o dos redes separadas.

### ¿Qué pasa si apago el equipo o sale una versión nueva?

Al encenderlo, el agente vuelve solo. También se actualiza solo: cuando sale una
versión nueva, la descarga y se reinicia con ella. Solo tendrás que hacer algo si
te avisamos en pantalla.

:::info 💡 ¿Necesitas ayuda?
Escríbenos desde la [página de contacto](/contact) o abre un hilo en
[nuestro Discord](/help/soporte-por-discord). Si nos dices qué impresoras tienes,
te decimos exactamente qué hacer con cada una.
:::

Que disfrutes de tener toda tu flota a la vista, estés donde estés.

![Bollo, la mascota de BolloPrint, con gafas de taller, delante de una granja de impresoras 3D trabajando](/blog/media/2026-09-08-impresoras-red-local-agente/07-bollo.webp)

## Documentación relacionada

- [Conectar impresoras](/help/conectar-impresoras): las dos vías y cuál te conviene
- [El agente local](/help/el-agente-local): la referencia completa
- [Desplegar el agente](/help/desplegar-el-agente): el detalle técnico, si lo necesitas
- [Tipos de conexión](/help/tipos-de-conexion): qué permite cada familia de impresora
- [Impresoras compatibles](/help/impresoras-compatibles): busca aquí tu modelo
