---
slug: connect-printers-local-network-agent
title: "Conecta tus impresoras por tu propia red: el agente local, paso a paso"
description: Bambu Lab, Prusa, Elegoo, Anycubic, FlashForge, Snapmaker, Klipper… Un agente pequeño en un equipo del taller, toda tu flota dentro de BolloPrint y sin tocar el router.
date: 2026-10-12
updated: 2026-10-16
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
- **Se actualiza solo**: cuando sale una versión nueva, la instala él.

::animation{id="local-agent"}

## Dónde instalarlo

El agente vive en **cualquier equipo del taller que no apagues**: un NAS, un
mini-PC, una Raspberry Pi o el PC del taller. Solo necesita que esté **siempre
encendido** y que tenga **Docker**.

Lo ideal es que esté **en la misma red que las impresoras**, porque así las
encuentra él solo. Si no es posible, las añades a mano y funcionan igual.

## Crea el agente en BolloPrint

Empieza en BolloPrint. Ve a **Configuración → Impresoras**. Verás tres pestañas:
**Impresoras** (todas tus máquinas, lleguen por donde lleguen), **Agente local** y
**Bambu Cloud**. Abre **Agente local** y pulsa **Nuevo agente**.

Ponle un nombre que te siga diciendo algo dentro de seis meses: **nómbralo por
dónde está, no por lo que es**. «Planta baja» o «Nave 2» sirven; «Agente 1», no.
Luego pulsa **Crear agente**.

![La pestaña Agente local, con dos agentes en línea y el botón Nuevo agente](/blog/media/2026-09-08-impresoras-red-local-agente/02-nuevo-agente-es.png)

## Copia la plantilla

Al crearlo, BolloPrint te muestra una **plantilla**: un texto que ya lleva
**escrito** todo lo tuyo, las claves de tu agente y la versión que toca. No hay
nada que sustituir ni que rellenar.

Elige el formato que uses (**Docker Compose** es el habitual), pulsa **Copiar** y,
cuando la tengas a salvo, **Guardar**.

![La plantilla de despliegue del agente nuevo, con el botón Copiar](/blog/media/2026-09-08-impresoras-red-local-agente/03-plantilla-es.png "75%")

:::warning 🔐 Cópiala ahora: las claves solo se muestran una vez
No las guardamos, así que no podemos volver a enseñártelas. Si pierdes la
plantilla, no pasa nada: abre el agente con **Editar** (en su menú **⋮**), ve a la
pestaña **Despliegue** y pulsa **Regenerar claves**. Si todavía no se ha
conectado nunca, no se corta nada.
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

## Si te atascas, pulsa «Instalar»

Mientras el agente no se haya conectado ni una vez, su fila dice **Sin
instalar**. No es un error: no se ha caído nada, solo falta instalarlo.

En esa misma fila tienes el botón **Instalar**. Al pulsarlo se despliegan los
pasos que acabas de leer, en corto, con un enlace a la **Ayuda**, otro a este
**Artículo del blog** y un botón para preguntarnos en **Discord**. Si no guardaste
la plantilla, el paso 3 te lleva directo a generar una nueva.

![Un agente sin instalar con el panel Instalar abierto: los tres pasos, la ayuda y Discord](/blog/media/2026-09-08-impresoras-red-local-agente/04-instalar-es.png)

## Comprueba que está en línea

Vuelve a BolloPrint: en menos de un minuto, el agente pasa a **En línea**, con el
nombre del equipo donde corre y la versión que lleva.

![El agente en estado En línea](/blog/media/2026-09-08-impresoras-red-local-agente/05-en-linea-es.png)

Si no lo hace, casi siempre es por una de tres causas: la plantilla se **pegó a
medias**, el equipo **no tiene internet** o un **cortafuegos** bloquea la salida.
Si quieres ver qué cuenta el propio agente, ábrelo con **Editar**: la pestaña
**Estado** lo detalla.

## Tus impresoras aparecen solas

Desde ese momento, el agente **busca impresoras en tu red** por su cuenta cada 15
minutos. Cuando encuentra alguna, te avisa encima de las pestañas y la ves al
final de **Impresoras por red local**, con su marca y su modelo. Tú decides:

- **Añadir**: la das de alta y empieza a informar.
- **Ignorar**: no es tuya o no la quieres aquí.

![Una impresora detectada por el agente, con los botones Ignorar y Añadir, y encima Buscar ahora y Añadir por IP](/blog/media/2026-09-08-impresoras-red-local-agente/06-encontradas-es.png)

Si acabas de encender una máquina y no quieres esperar, pulsa **Buscar ahora**.
Si una impresora te va a pedir un código, la propia fila te lo avisa («pedirá el
código de acceso»), para que lo tengas a mano.

## Si alguna no aparece, añádela tú

Que una impresora no aparezca sola es **normal** en dos casos:

- **Está en otra red.** Los avisos de las impresoras no pasan de una red a otra.
- **El agente funciona en Windows o Mac.** Ahí Docker corre en una máquina
  virtual.

No pierdes nada por ello: la añades tú y funciona exactamente igual, con cámara y
con mandos si esa máquina los tiene. Pulsa **Añadir por IP**. Son tres pasos.

### 1. Elige la marca

Elige la marca de tu impresora: cada una tiene su tarjeta, y las que tienen logo
van primero. No hace falta que sepas cómo se comunica tu máquina; de eso nos
encargamos nosotros. Si eliges **Elegoo**, te preguntamos **¿Qué Elegoo tienes?**,
porque tiene varias familias. **Klipper** y **Otra de resina (ChituBox)** están al
final, en **Genéricas**, para un montaje propio o una marca que no sale en la lista.

Si dudas de si tu modelo vale, abajo tienes **¿No lo tienes claro? Mira la lista
de compatibles**; y si tu impresora no está, cuéntanoslo en Discord.

![El primer paso de Añadir impresora por IP: las marcas que se pueden conectar](/blog/media/2026-09-08-impresoras-red-local-agente/08-anadir-marca-es.png)

### 2. Escribe sus datos

Solo lo imprescindible:

- **¿Qué agente la conecta?**, si tienes más de uno. Solo puedes elegir uno que
  esté en línea.
- **IP de la impresora**. La ves en la pantalla de la impresora (Ajustes → Red) o
  en tu router.
- **El código de la impresora**, si esa marca lo pide. El campo se llama como lo
  llama el fabricante: en una Bambu, **Código de acceso LAN**.
- **Nombre**, si quieres darle uno tuyo. Es opcional.

El **modelo y el número de serie no los escribes**: el agente se los pregunta a la
impresora. Los campos obligatorios llevan un **asterisco rojo** y se marcan en rojo
mientras están vacíos. Al final, el recuadro **Recuerda** te dice qué tienes que
preparar en esa marca antes de conectar.

![El segundo paso: el agente, la IP, el código de acceso LAN obligatorio y el recuadro Recuerda](/blog/media/2026-09-08-impresoras-red-local-agente/09-anadir-datos-es.png)

### 3. Conecta

Pulsa **Conectar** y verás cómo avanza: el agente recibe la petición, busca la
impresora en esa dirección y se conecta. Cuando termina, verás **«Conectada. Ya
está en tu lista de impresoras.»**

![El tercer paso: la impresora conectada y ya en la lista](/blog/media/2026-09-08-impresoras-red-local-agente/10-anadir-conexion-es.png)

Si algo falla, te lo decimos **en palabras normales**: qué está pasando y qué
revisar (que no hay nada respondiendo en esa IP, que la impresora rechaza el
código…). Con **Volver** corriges el dato y lo intentas otra vez. El mensaje
original de la impresora queda plegado en **Ver detalle técnico**: si nos
escribes, cópianos eso y lo vemos antes.

:::info 💡 Resérvale la IP en el router
Si el router le cambia la dirección a una impresora, la volvemos a buscar sola,
pero estará caída un rato. Reservarle la dirección evita ese hueco. Es un ajuste
del router, no de BolloPrint.
:::

## Qué te pide cada marca

Aquí es donde surgen más dudas. Es lo mismo que te recuerda el paso 2, en resumen:

| Marca | Qué tienes que hacer en la máquina | Cámara | ¿Puedes pausar y cancelar? |
|---|---|---|---|
| **Bambu Lab** | Activar el **Modo LAN** en su pantalla (Ajustes → Red) y usar el **código de acceso LAN** que te enseña | Sí | Sí, si además activas el **Modo desarrollador** |
| **Prusa** (beta: MK4, MK3.5, MK3.9, MINI, XL, CORE One) | Activar **PrusaLink** y usar la **contraseña** que muestra (no es la de Prusa Connect) | Todavía no | Sí |
| **Elegoo** (Saturn, Mars, Jupiter, Centauri Carbon) y **otras de resina (ChituBox)** | Nada, no piden contraseña | En los modelos que la traen | Sí |
| **Elegoo Centauri Carbon 2** | Nada; solo si le pusiste un código en su pantalla, escríbelo | Sí | Todavía no |
| **Anycubic** (beta: Kobra 3, Kobra S1, Kobra 4, Kobra X) | Activar el **Modo LAN** (Ajustes → Red). Con él, la impresora deja de usar la nube y la app de Anycubic | Todavía no | Todavía no |
| **FlashForge** (beta: Adventurer 5M, 5M Pro, AD5X, Creator 5) | Activar **LAN Only** y usar el código de verificación de su menú de red | Sí | Todavía no |
| **Snapmaker** (U1) | Nada | Sí | Sí |
| **Klipper** (QIDI, Sovol, Voron, RatRig, Creality K1…) | Normalmente nada: solo si pusiste una clave de API en Moonraker | Sí, si tienes webcam en tu Klipper | Sí |

:::warning ⚠️ Bambu Lab: el código de acceso cambia
Cada vez que activas o desactivas el Modo LAN o el Modo desarrollador, Bambu
**genera un código nuevo**. Si una Bambu que funcionaba bien deja de conectar de
repente, nueve de cada diez veces es por esto: mira otra vez el código en su
pantalla y actualízalo en BolloPrint. Y ten en cuenta que el **Modo
desarrollador** la desconecta de Bambu Cloud: desde ese momento la verás solo por
el agente.
:::

:::info 💡 ¿No encuentras tu modelo en la tabla?
Consulta las [impresoras compatibles](/help/impresoras-compatibles). Si lleva
**Klipper** por dentro (cualquier máquina de montaje propio o modificada), es
compatible aunque la marca no aparezca en ninguna lista.
:::

## Lo que ganas con el agente local

Con el agente en marcha, obtienes:

- **Casi todas las marcas**: Bambu Lab, Prusa, Elegoo, Anycubic, FlashForge,
  Snapmaker y todo lo que lleva Klipper. La nube no lo ofrece, porque solo existe
  para Bambu Lab.
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
dos locales o dos redes separadas. En ese caso, al **Añadir por IP** te pregunta
cuál la conecta.

### ¿Qué pasa si apago el equipo o sale una versión nueva?

Al encenderlo, el agente vuelve solo. También se actualiza solo: cuando sale una
versión nueva, la descarga y se reinicia con ella, sin que tengas que tocar la
plantilla. Solo tendrás que hacer algo si te avisamos en pantalla.

### ¿Por qué no puedo pulsar «Añadir por IP»?

Porque ninguno de tus agentes está conectado, y debajo del botón te lo dice. Si
todavía no lo has instalado, usa **Instalar** en su fila; si ya funcionaba,
comprueba que el equipo esté encendido y con internet.

:::info 💡 ¿Necesitas ayuda?
Escríbenos desde la [página de contacto](/contact) o abre un hilo en
[nuestro Discord](/help/soporte-por-discord). Si nos dices qué impresoras tienes,
te decimos exactamente qué hacer con cada una.
:::

Que disfrutes de tener toda tu flota a la vista, estés donde estés.

![Bollo, la mascota de BolloPrint, con gafas de taller, delante de una granja de impresoras 3D trabajando](/blog/media/2026-09-08-impresoras-red-local-agente/07-bollo.webp "60%")

## Documentación relacionada

- [Conectar impresoras](/help/conectar-impresoras): las dos vías y cuál te conviene
- [El agente local](/help/el-agente-local): la referencia completa
- [Desplegar el agente](/help/desplegar-el-agente): el detalle técnico, si lo necesitas
- [Tipos de conexión](/help/tipos-de-conexion): qué permite cada familia de impresora
- [Impresoras compatibles](/help/impresoras-compatibles): busca aquí tu modelo
