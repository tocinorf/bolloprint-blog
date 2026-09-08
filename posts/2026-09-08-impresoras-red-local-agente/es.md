---
slug: conectar-impresoras-red-local-agente-bolloprint
title: Conectar tus impresoras por red local: desplegar el agente paso a paso
description: Prusa, Elegoo, Klipper, FlashForge y Bambu con cámara y mandos. Desplegamos el agente en Docker y damos de alta la flota, con los detalles de cada marca.
date: 2026-09-08
updated: 2026-09-08
tags: [tutoriales]
draft: true
---

Por red local, BolloPrint habla con tus impresoras **directamente en tu taller**,
sin pasar por la nube de ningún fabricante. Es la vía que funciona con casi todas
las marcas, la que trae **cámara**, y la única con la que puedes **pausar,
reanudar o cancelar** desde BolloPrint.

A cambio hay que instalar una cosa: el **agente local**, un programa pequeño que
corre en un equipo del taller. Con **uno solo basta para toda la flota**.

En este tutorial lo montamos entero. De ejemplo, un taller con cuatro máquinas de
tres marcas distintas: una **Prusa MK4S**, una **Elegoo Saturn 4 Ultra**, una
**QIDI Q1 Pro** (que por dentro es Klipper) y una **Bambu Lab P1S** que ya
teníamos conectada por la nube.

![Placeholder — Settings → Printers, bloque Local agent sin agentes](/blog/media/2026-09-08-impresoras-red-local-agente/01-local-agent-vacio.png)

## Antes de empezar

- [ ] Entras en BolloPrint como **Admin** o **Propietario**.
- [ ] Tienes un **equipo que esté siempre encendido** en el taller: un NAS
      (Synology, QNAP…), un mini-PC, una Raspberry Pi o un servidor que ya
      tengas.
- [ ] Ese equipo tiene **Docker** (o **Portainer**, que es Docker con pantalla).
- [ ] Está **en la misma red que las impresoras**. No es imprescindible, pero sí
      lo más cómodo — luego vemos por qué.

Consume muy poco: entre **10 y 20 MB de memoria** con varias impresoras
conectadas.

:::info 💡 El agente no abre tu red a nadie
Es **él quien nos llama a nosotros**. No hay que abrir puertos en el router, ni
tener IP fija, ni tocar el cortafuegos. Funciona detrás de un router doméstico
normal, e incluso con las fibras que no dan IP pública.
:::

:::info 💡 Lo ideal es que esté en la MISMA red que las impresoras
Si el agente está en una red y las impresoras en otra (VLANs separadas, red de
invitados, wifi aparte), **no deja de funcionar**: lo que se pierde es el
**descubrimiento automático**, porque ese aviso de «estoy aquí» no cruza de una
red a otra. Las impresoras se añaden entonces a mano por su IP y van igual de
bien, con cámara y con mandos. Lo único imprescindible es que las dos redes
puedan hablarse.
:::

## Paso 1 — Crea el agente en BolloPrint

**Settings** → pestaña **Printers** → bloque **Local agent**.

En **New agent**, ponle un nombre en **Agent name**. Un consejo que se agradece
el día que tengas dos: **nómbralo por dónde está, no por qué es**. `Ground floor`
o `Nave 2` te dicen algo dentro de seis meses; `Agente 1` no.

En nuestro ejemplo: `Taller planta baja`.

Pulsa **Create and generate code**.

![Placeholder — New agent con el nombre escrito y el botón Create and generate code](/blog/media/2026-09-08-impresoras-red-local-agente/02-new-agent.png)

## Paso 2 — Copia el código de conexión

Aparece el **código del agente**. Cópialo ahora.

:::warning 🔐 El código se enseña UNA sola vez
No caduca, pero no lo volvemos a mostrar. Si lo pierdes no pasa nada grave: usa
**Rotate code** y vuelve a desplegar con el nuevo.
:::

![Placeholder — modal con el código del agente y el aviso de que se muestra una vez](/blog/media/2026-09-08-impresoras-red-local-agente/03-codigo-agente.png)

## Paso 3 — Despliega el agente en tu equipo

Justo debajo tienes **How to deploy it**, con tres pestañas: **Docker Compose**,
**Kubernetes** y **Portainer**. Copia el bloque de tu sistema con el botón
**Copy**.

:::warning ⚠️ Copia el bloque desde la pantalla, no de este artículo
En la pantalla va **la versión del agente que toca en cada momento**. El ejemplo
de aquí abajo es para que veas la pinta que tiene, no para pegarlo tal cual.
:::

![Placeholder — las tres pestañas de How to deploy it, con Docker Compose activa](/blog/media/2026-09-08-impresoras-red-local-agente/04-deploy-snippets.png)

### Docker Compose

El bloque es un `docker-compose.yml` completo. Solo hay que sustituir **una**
cosa: donde pone `PEGA_AQUI_TU_CODIGO`, tu código.

```yaml
services:
  bolloprint-agent:
    image: ghcr.io/bolloprint/bolloprint-agent:0.4.7
    container_name: bolloprint_agent
    restart: unless-stopped
    network_mode: host
    mem_limit: 512m
    pids_limit: 512
    ulimits:
      nofile:
        soft: 65536
        hard: 65536
    logging:
      driver: json-file
      options:
        max-size: "10m"
        max-file: "3"
    environment:
      BP_AGENT_CODE: PEGA_AQUI_TU_CODIGO
    volumes:
      - identity:/var/lib/bolloprint

volumes:
  identity:
    name: bolloprint_agent_identity
```

Lo guardas en el equipo y arrancas:

```bash
docker compose up -d
```

Dos detalles del manifiesto que conviene no tocar:

- **`network_mode: host`** es lo que permite el descubrimiento automático. Sin
  eso, el contenedor no ve la red del equipo y las impresoras hay que añadirlas
  a mano.
- **El volumen `identity`** guarda la identidad de esta instalación. Viaja con el
  contenedor si lo mueves; si lo borras, tendrás que volver a autorizar el agente
  (no se pierde nada, solo es un clic más).

### Portainer

Mismo contenido, pero el código va como **variable de entorno** del stack en vez
de escrito dentro: en el formulario de Portainer, añade `BP_AGENT_CODE` con tu
código y despliega.

### Kubernetes

El manifiesto trae **dos** valores que sustituir, y el segundo es importante:

- `BP_AGENT_CODE` en el `Secret` — tu código de conexión.
- `BP_AGENT_INSTANCE_ID` — **una cadena aleatoria larga tuya**.

:::danger 🔐 `BP_AGENT_INSTANCE_ID` es una contraseña, no una etiqueta
Es con lo que el agente se identifica al conectarse. **No la compartas y no la
reutilices en otra instalación.** Genera una:

```bash
openssl rand -hex 32
```

En Kubernetes hace falta porque un pod que se reprograma deja atrás su volumen: sin
ese valor fijo, cada reprogramación parecería una instalación nueva.
:::

## Paso 4 — Comprueba que el agente está en línea

En menos de un minuto, en la misma pantalla de BolloPrint, la tarjeta del agente
pasa a **Online**.

![Placeholder — tarjeta del agente en estado Online](/blog/media/2026-09-08-impresoras-red-local-agente/05-agente-online.png)

Si no aparece, mira su registro en el equipo donde corre:

```bash
docker logs bolloprint_agent --tail 50
```

Las tres causas habituales: el código **mal pegado** (con un espacio delante o
detrás), el equipo **sin salida a internet**, o un **cortafuegos** bloqueando la
salida.

## Paso 5 — Añade las impresoras que aparecen solas

El agente **busca impresoras en tu red** por su cuenta cada 15 minutos, y las que
encuentra salen en **Found on the network**, con su marca y su modelo.

En nuestro ejemplo aparecen tres: la Prusa MK4S, la Saturn 4 Ultra y la QIDI.

- **Add** — la das de alta.
- **Ignore** — no es tuya, o no la quieres. Se aparta de la lista.

Algunas tarjetas avisan de que **will ask for the access code**: esa te va a
pedir la contraseña al añadirla.

![Placeholder — Found on the network con tres impresoras detectadas](/blog/media/2026-09-08-impresoras-red-local-agente/06-found-on-network.png)

:::info
Si acabas de encender una impresora y no quieres esperar los 15 minutos, hay un
botón para pedir la búsqueda ahora mismo.
:::

:::info
También puede salir una impresora marcada como **Coming soon**: sabemos qué es,
pero todavía no podemos conectarla. Si es una que necesitas, **dínoslo** — el
orden en que las añadimos lo marcan los talleres que las tienen.
:::

## Paso 6 — Añade a mano las que no aparecen

Que una impresora no salga en la lista es **normal en dos casos**: cuando el
agente está en **otra red** que las impresoras, y cuando corre sobre **Docker
Desktop** en Windows o Mac (esos sistemas no dejan que el contenedor vea la red
del equipo).

En ninguno de los dos pierdes nada. Añadida a mano funciona **exactamente igual**,
con cámara y con mandos si esa máquina los tiene. Solo es un paso más.

Pulsa **Add printer** y rellena:

| Campo | Qué poner |
|---|---|
| **Protocol** | El tipo de impresora. La lista solo ofrece los que podemos conectar. |
| **Address** | La IP de la impresora. Si usa un puerto distinto del habitual, escríbelo detrás: `192.168.1.50:5000` |
| **LAN access code** / **API key** | Solo si esa familia lo pide. |
| **Model** | Cómo sabemos si deposita filamento o cura resina, y qué vista darle: `Saturn 4 Ultra`, `MK4S`, `Q1 Pro`… |
| **Name** | Opcional. El que quieras darle tú. |

**El número de serie no lo tecleas tú**: el agente lo averigua solo. Verás
`Looking for the printer…` y, en cuanto la máquina responde, entra en la lista.

![Placeholder — formulario Add printer by IP con los campos rellenos](/blog/media/2026-09-08-impresoras-red-local-agente/07-add-printer-ip.png)

:::info 💡 Resérvale la IP en el router
Si el router le cambia la dirección a la impresora, la volvemos a buscar sola,
pero estará caída un rato. Reservarle la IP por MAC —o ponerle IP fija— evita ese
hueco.
:::

## Lo que pide cada marca

Aquí es donde se atasca la gente, así que vamos marca por marca.

### 🎋 Bambu Lab

1. En la **pantalla de la impresora**, activa el **Modo LAN**. Eso hace que la
   máquina enseñe su **código de acceso** (*Settings → Network → Access code*).
2. Ese código es el que va en **LAN access code**.
3. Si además quieres **pausar, reanudar y cancelar**, activa también el **Modo
   desarrollador** en la impresora. Solo para leerla no hace falta.

:::warning ⚠️ El código de acceso CAMBIA
Cada vez que activas o desactivas el Modo LAN o el Modo desarrollador, Bambu
**genera un código nuevo**. Si una Bambu que iba bien deja de conectar de golpe,
es esto el 90% de las veces: vuelve a mirar el código en la pantalla y actualízalo
en BolloPrint.
:::

Dos cosas más de esta marca:

- **La serie X1 necesita una microSD puesta** para imprimir en modo LAN. Es un
  requisito de Bambu, no nuestro.
- **Las A1 y las P1 admiten muy pocas conexiones a la vez.** Si tienes la app del
  móvil o el laminador abiertos contra la impresora, la máquina acepta nuestra
  conexión y luego no envía nada: la verás como **connected but sending no data**.
  Cierra la app o el laminador y vuelve.

### 🟠 Prusa (PrusaLink)

- Vale para **MK4, MK3.5, MK3.9, MINI, XL y CORE One**. Las **MK3S y anteriores
  no**: esas no hablan por red por sí solas.
- Pide la **contraseña que muestra la propia impresora** en su menú.
- **La cámara todavía no.** No es que la de Prusa no sirva: es un aparato
  independiente, con su propia dirección de red, que no sabe a qué impresora
  pertenece. Vincularla a mano está previsto y aún no está disponible.
- Sí llega la **imagen del laminado** de lo que está imprimiendo.

### 🔧 Klipper (QIDI, Creality serie K, Sovol, Voron, RatRig, Snapmaker U1…)

- Es el tipo que **más máquinas cubre**, porque no es una marca: es el firmware
  que llevan por dentro muchísimas impresoras y todas las de montaje propio.
- **Normalmente no pide contraseña.** El campo **API key** solo hace falta si tú
  configuraste `[authorization]` en tu Moonraker. Si tu impresora acepta
  conexiones de tu red sin clave, déjalo vacío.
- **La cámara sale de tu propia configuración**: si tienes una webcam dada de
  alta en Klipper, la usamos; si no, no hay.

:::info 💡 Si tu impresora no está en la lista de compatibles
**Cualquier máquina con Klipper y su interfaz web (Mainsail o Fluidd) accesible
desde otro equipo de tu red entra hoy**, sea de la marca que sea. Es la puerta
por la que entran las impresoras modificadas.
:::

### 🧪 Elegoo de resina y placas ChituBox (SDCP)

- Cubre la gama de resina de Elegoo —Mars, Saturn, Jupiter— y máquinas de otras
  marcas con la misma placa.
- **No pide contraseña ninguna.** Conviene saberlo: cualquiera en tu red puede
  leer esa impresora, no solo nosotros.
- Cámara en los modelos que la traen.

### 🟢 Elegoo Centauri Carbon 2

- Es de la misma marca que las de resina pero funciona distinto, por eso está
  aparte en la lista de protocolos.
- Pide contraseña **solo si tú le pusiste un código** en la pantalla de la
  máquina.
- **Su cámara admite una sola conexión a la vez.** Si alguien la está mirando
  desde el móvil, nuestra foto de ese momento falla — y es lo correcto: quien
  está delante de la máquina tiene preferencia.

### 🔵 FlashForge

- Vale para **Adventurer 5M, 5M Pro, AD5X y Creator 5**. La generación anterior
  (Guider, Finder, Adventurer 3 y 4) todavía no.
- Activa **LAN Only** en la máquina y usa el **código de comprobación** que
  aparece en su pantalla.

## Unificar una Bambu que ya tenías por la nube

Esta es la parte que casi nadie espera y que conviene no saltarse.

Cuando añades al agente una máquina que **ya tenías conectada por la nube**,
BolloPrint lo detecta y te lo dice: *«This printer is already connected»*. Te
ofrece **Move it to the agent**, y eso:

- conserva su **número**, su **nombre** y **todo su historial** de impresiones;
- deja de **contar dos veces** en tu plan;
- a cambio, deja de estar conectada por la nube — que es justo lo que quieres,
  porque por el agente ganas cámara y mandos.

![Placeholder — aviso «This printer is already connected» con el botón Move it to the agent](/blog/media/2026-09-08-impresoras-red-local-agente/08-mover-al-agente.png)

:::warning ⚠️ Si no la unificas, son dos impresoras
Para BolloPrint serían dos máquinas distintas y ocuparían **dos plazas** de tu
plan. Cuando salga ese aviso, léelo: es justo eso lo que te está proponiendo
evitar.
:::

## Instalaciones pendientes de autorizar

La primera vez que arrancas el agente con su código, entra directo. **A partir de
ahí, cualquier instalación nueva que use ese mismo código espera tu visto bueno**:
aparece en **Installations awaiting authorisation**, con el nombre del equipo
desde el que se conecta.

Es normal y esperado cuando:

- mueves el agente a otra máquina,
- borras su volumen de datos y lo vuelves a crear,
- lo reinstalas desde cero.

Pulsa **Authorise** si reconoces el equipo. Al autorizar uno, el anterior deja de
tener acceso.

:::danger 🔐 Si aparece una instalación que NO has puesto tú
No la autorices: significa que alguien más tiene tu código. Usa **Rotate code** y
vuelve a desplegar el agente con el nuevo. El código anterior sigue valiendo
**24 horas**, así que te da tiempo a actualizar el despliegue con calma.
:::

## Qué significa cada estado

**El agente:**

| Estado | Qué está pasando |
|---|---|
| **Online** | Conectado y trabajando. |
| **No recent signal** | Lleva un rato sin dar señales. Suele ser el equipo apagado o sin internet. |
| **Offline** | No está. |
| **Safe mode** | Ha arrancado y ha conectado, pero no está gestionando impresoras. Te dice el motivo. |
| **Buffer** | Lo que ha guardado mientras no podía enviarlo. Si dice «messages dropped», hubo un corte tan largo que no cupo todo. |
| **Update your agent** | Hay una versión más reciente. Vuelve a copiar el bloque de la pantalla y reinicia el contenedor. |

**Cada impresora:**

| Estado | Qué está pasando |
|---|---|
| **Online** | Todo bien: el agente la ve y recibe sus datos. |
| **connected but sending no data** | Ha conectado y la máquina no cuenta nada. Casi siempre: admite pocas conexiones a la vez y ya tiene otra abierta (la app del móvil, el laminador). |
| **Nothing answers at that address** | Comprueba que está encendida y en la misma red que el agente. |
| **It answers but refuses the connection** | Código de acceso equivocado, o modo LAN desactivado en la impresora. |
| **Not visible** | El problema no es de la impresora: es su agente, que no responde. La máquina puede estar perfectamente. |

![Placeholder — tarjeta del agente con Link to each printer y varios estados](/blog/media/2026-09-08-impresoras-red-local-agente/09-estados-impresoras.png)

## Lo que ganas, en concreto

Una vez montado, esto es lo que tienes y que por la nube no tendrías:

- **Mandos**: pausar, reanudar y cancelar la impresión en curso, en las máquinas
  que lo permiten.
- **Cámara**: una foto del interior **cada 3 minutos aproximadamente**, mientras
  la máquina imprime o está en pausa. Al acabar el trabajo se queda la última
  foto asociada a esa impresión. No es videovigilancia: es ver de un vistazo si
  aquello sigue bien.
- **Aguante ante los cortes de internet**: si tu línea se cae, el agente **sigue
  leyendo las impresoras y guarda lo que pasa**. Cuando vuelve, lo envía todo. No
  pierdes el historial de esas horas.
- **Independencia del fabricante**: ni de que su nube funcione, ni de que
  mantenga el servicio abierto.

Lo que sigue sin poder hacerse, por ninguna vía: **enviar trabajos a imprimir**.
El fichero se manda desde tu laminador, como siempre.

## ¿Uno o varios agentes?

**Un agente aguanta una flota entera.** No hace falta uno por impresora ni uno
por sala. Dicho eso, hay tres motivos legítimos para tener varios:

- **Redes separadas** — una VLAN para producción y otra para oficina. Un agente
  en cada una descubre las suyas sin que añadas nada a mano.
- **Locales distintos** — dos naves, dos talleres. Cada sitio con el suyo, y todo
  se ve junto en BolloPrint.
- **Un agente saturado** — si la flota crece mucho y lo notas justo, reparte.

Mover una impresora de un agente a otro es **cambiar un desplegable** en su ficha.

:::warning ⚠️ Un código por equipo
Lo que **no** debes hacer es usar el mismo código en dos máquinas: la segunda se
quedará esperando autorización y, si la autorizas, **la primera pierde el acceso**.
Para dos equipos, dos agentes.
:::

## Cuando algo no va

| Síntoma | Qué mirar |
|---|---|
| El agente no aparece nunca | ¿Se pegó el código entero y sin espacios delante o detrás? ¿El equipo llega a internet? ¿Hay un cortafuegos bloqueando la salida? |
| Pide autorización en cada reinicio | Le falta el volumen de identidad, o el contenedor no puede escribir en él. Revisa el bloque de despliegue tal cual aparece en la pantalla. |
| No detecta ninguna impresora | ¿Están el agente y las impresoras en la misma red? Si no, o si usas Docker Desktop, es lo esperado: añádelas por IP y funcionarán igual. |
| **connected but sending no data** | Cierra la app del móvil o el laminador que tenga esa máquina abierta. |
| **It answers but refuses the connection** | Código de acceso equivocado o modo LAN desactivado. En Bambu, recuerda que el código **cambia** al tocar esos modos. |
| Todas las impresoras de golpe **Not visible** | No es la flota, es el agente. Mira su tarjeta de estado. |

El primer sitio donde mirar, siempre:

```bash
docker logs bolloprint_agent --tail 50
```

## Preguntas que nos hacen mucho

**¿Guarda algo en mi disco?** No guarda datos de impresión. Solo un fichero de
identidad, para reconocerse a sí mismo tras un reinicio y no tener que pedirte
autorización cada vez.

**¿Y si apago el equipo?** No pasa nada. Al encenderlo, el agente vuelve solo y
sin pedirte nada.

**¿Tengo que abrir puertos en el router?** No. Ni puertos, ni IP fija, ni reglas
de cortafuegos. La conexión sale de tu red hacia fuera, como cuando abres una
página web.

**¿Hay que reiniciar el agente al añadir una impresora?** No. Cuando das de alta
una máquina desde BolloPrint, el agente se entera **solo, en segundos**.

**¿Y si revoco un agente?** Deja de conectarse al instante y sus impresoras pasan
a desconectadas. **El historial se conserva**, y las impresoras se quedan con su
dirección y su código guardados: pasarlas a otro agente es un cambio por
impresora, no volver a teclear la flota.

## Documentación relacionada

- [Impresoras por red local](/help/impresoras-por-red-local) — la referencia de esta pantalla
- [El agente local](/help/el-agente-local) — instalación, identidad, varios agentes y diagnóstico
- [Tipos de conexión](/help/tipos-de-conexion) — qué permite cada familia de impresora
- [Impresoras compatibles](/help/impresoras-compatibles) — busca aquí tu modelo
- [Conectar impresoras](/help/conectar-impresoras) — las dos vías y cuál te conviene
- [Impresoras por la nube](/help/impresoras-por-la-nube) — la otra vía, para Bambu Lab
