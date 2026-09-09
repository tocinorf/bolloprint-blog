---
slug: conectar-impresora-bambu-lab-nube-bolloprint
title: Cómo conectar tus impresoras Bambu Lab a BolloPrint por la nube
description: Paso a paso, en cinco minutos y sin instalar nada. Incluye los dos fallos que hacen perder media tarde a casi todo el mundo.
date: 2026-09-08
updated: 2026-09-08
tags: [tutoriales]
draft: false
---

Si tienes impresoras **Bambu Lab** y quieres verlas dentro de BolloPrint —qué
están imprimiendo, cuánto les queda, qué material llevan y el historial de cada
trabajo— la vía más rápida es la nube. **No hay que instalar nada**: conectas tu
cuenta de Bambu y las máquinas aparecen solas.

En este tutorial lo hacemos entero. De ejemplo usaremos un taller pequeño con
tres máquinas en la misma cuenta de Bambu: **dos A1 y una P1S**.

:::info
Esta guía cubre solo la vía de la nube, que es de **solo lectura**. Si lo que
quieres es cámara y poder pausar o cancelar desde BolloPrint, lo tuyo es el
agente local — está en el [otro tutorial](/blog/conectar-impresoras-red-local-agente-bolloprint).
:::

![Settings → Printers, sección Bambu Lab sin cuenta conectada](/blog/media/2026-09-08-impresoras-por-la-nube/01-settings-printers-bambu-vacio.png)

## Antes de empezar: cinco minutos de comprobaciones

Repasa esto primero. Estos cuatro puntos son la causa de casi todos los intentos
fallidos:

- [ ] Entras en BolloPrint como **Admin** o **Propietario**. Los demás roles no
      ven esta pantalla.
- [ ] Tienes una cuenta de Bambu Lab con **email y contraseña propias**.
- [ ] Tus impresoras están **vinculadas a esa cuenta** y encendidas con internet.
- [ ] Tienes a mano el **correo** de esa cuenta: Bambu te va a mandar un código.

:::warning ⚠️ Si entras en Bambu con Google, Apple o Facebook, esto no te va a funcionar
BolloPrint necesita el **email y la contraseña** de la cuenta de Bambu. Si nunca
has puesto contraseña porque siempre entras con «Continuar con Google», créala
primero en la web de Bambu Lab y vuelve aquí con ella.
:::

:::warning ⚠️ El fallo que más tiempo hace perder: la contraseña recién creada
Cuando te acabas de crear una contraseña y **no la has usado nunca**, la cuenta
de Bambu puede tener **pendiente la verificación del correo**. Bambu no lo dice.
Responde `Incorrect Bambu Lab account or password` —«contraseña incorrecta»— y te
deja veinte minutos convencido de que te has equivocado al teclear.

**La solución:** entra una vez en la web de Bambu Lab con ese email y esa
contraseña, completa lo que te pida, y vuelve. Si te ha pasado esto, es
exactamente esto.
:::

:::warning ⚠️ Y uno más: la verificación en dos pasos
Si tu cuenta de Bambu tiene **MFA activado**, la conexión no se puede completar y
verás `Your Bambu Lab account has two-step verification (MFA) enabled`. Hay que
desactivarla en Bambu para poder conectar la cuenta.
:::

## Paso 1 — Abre la pantalla de impresoras

En el menú de usuario, **Settings** → pestaña **Printers**.

Esa pantalla tiene tres bloques, y conviene saber para qué sirve cada uno desde
el principio:

| Bloque | Para qué es |
|---|---|
| **Bambu Lab** | Conectar la cuenta del fabricante. Es lo que vamos a hacer aquí. |
| **Local agent** | Desplegar el agente para conectar por red local. Otro tutorial. |
| **Printer management** | La lista de **todas** tus máquinas, vengan por donde vengan. |

![los tres bloques de Settings → Printers](/blog/media/2026-09-08-impresoras-por-la-nube/02-tres-bloques.png)

## Paso 2 — Escribe tu email y tu contraseña de Bambu

En el bloque **Bambu Lab**, rellena:

- **Bambu account email** — el email de la cuenta de Bambu. No otro tuyo.
- **Bambu Lab Password** — la contraseña de esa cuenta.

Y pulsa **Connect with BambuLab**.

En nuestro ejemplo: `taller@ejemplo.com` y su contraseña. El botón cambia a
`Connecting…` un par de segundos.

![formulario con email y contraseña rellenos](/blog/media/2026-09-08-impresoras-por-la-nube/03-email-password.png)

:::info
La contraseña **se queda solo en tu navegador**, en esta sesión, hasta que
termines de verificar o canceles. No se guarda en ningún otro sitio.
:::

## Paso 3 — Mete el código de 6 dígitos

Bambu te manda un correo con un **código de 6 dígitos**. Remitente habitual:
`noreply@bambulab.com` — **mira también en spam**, cae ahí más de lo que debería.

En la misma pantalla aparece ahora **Step 2 — Email Code**. Escribe o pega los
seis dígitos en **Verification Code (6 digits)** y pulsa **Verify and connect**.

![campo del código de 6 dígitos y botón Verify and connect](/blog/media/2026-09-08-impresoras-por-la-nube/04-codigo-verificacion.png)

Tres cosas que te ahorran un segundo intento:

1. **No cierres la pestaña ni te vayas de la pantalla** antes de verificar. Si
   sales, hay que empezar de cero.
2. **El código caduca en unos 5 minutos.** Si tardas, pulsa **Resend code** y usa
   el nuevo.
3. **Pega el código entero tal como venga en el correo.** Si trae espacios o
   guiones, se limpian solos. Si el campo se queda raro, bórralo y pega otra vez.

Cuando lo acepta, verás **Account verified and connected**.

![«Account verified and connected»](/blog/media/2026-09-08-impresoras-por-la-nube/05-cuenta-verificada.png)

## Paso 4 — Tus impresoras ya están ahí

No hay que darlas de alta una a una. En cuanto la cuenta queda conectada, las
máquinas de esa cuenta aparecen solas en **Printer management**.

En nuestro ejemplo aparecen las tres: `A1 - Taller`, `A1 mini` y `P1S`, cada una
con su número de serie y su estado.

![Printer management con las tres impresoras recién aparecidas](/blog/media/2026-09-08-impresoras-por-la-nube/06-printer-management.png)

### El contador de impresoras activas

Arriba de esa lista hay un contador tipo `3/6`: **impresoras activas** de las que
incluye tu plan. Cada máquina activa ocupa una plaza.

- Con el interruptor de cada fila las apagas y enciendes. Una impresora
  **inactiva** no cuenta para el límite y no nos conectamos a ella, pero **sigue
  en la lista** con su nombre y todo su historial.
- Si conectas una flota entera y no hay plazas para todas, **las que sobran
  entran desactivadas** en vez de romperte el plan. Tú eliges cuáles enciendes.

## Qué vas a ver a partir de ahora

Ve a **Printers** —la sección, no la de ajustes— y ahí tienes el taller entero.
De cada máquina:

- Si está **encendida y conectada**.
- Qué está imprimiendo, el **porcentaje** y el tiempo que le queda.
- Temperaturas de **boquilla**, **cama** y **cámara**, según el modelo.
- Los **materiales** cargados bandeja a bandeja, si tienes AMS.
- La **imagen del laminado** del trabajo en curso.
- El **historial completo**: cada impresión, con su duración, su material y su
  resultado. Sin apuntar nada a mano.

![tarjeta de una P1S imprimiendo, con progreso y temperaturas](/blog/media/2026-09-08-impresoras-por-la-nube/07-tarjeta-impresora.png)

## Qué NO vas a poder hacer por esta vía

Esto es lo importante de la nube, y mejor saberlo ahora que buscar el botón
durante media hora:

| | |
|---|---|
| **Solo lectura** | No se puede pausar, reanudar ni cancelar desde BolloPrint. Es el propio firmware de Bambu, que ignora las órdenes que no vengan de sus programas. Preferimos no enseñar un botón que la máquina no va a obedecer. |
| **Sin cámara** | Por la nube no llega la imagen de la cámara. Sí llega la **imagen del laminado**, que es la vista previa del trabajo, no lo que está pasando dentro. |
| **Depende de internet dos veces** | Necesita internet en tu taller **y** que la nube de Bambu funcione. Si falla cualquiera de las dos, la impresora aparece desconectada aunque esté imprimiendo perfectamente. |
| **La sesión caduca** | Cada cierto tiempo hay que volver a conectar la cuenta. Lo verás avisado en esta misma pantalla. |

Y una que vale para todas las vías: **BolloPrint no envía trabajos a imprimir**.
El fichero se sigue mandando desde tu laminador. Lo que hacemos es leer lo que la
máquina está haciendo y registrarlo.

## Si algo no conecta

| Lo que ves | Qué suele ser |
|---|---|
| `Incorrect Bambu Lab account or password` y estás seguro de la contraseña | La cuenta tiene el correo pendiente de verificar. Entra una vez en la web de Bambu con esas credenciales y vuelve. |
| `Incorrect Bambu Lab account or password` y entras a Bambu con Google o Apple | Esa vía no sirve aquí. Crea una contraseña en la web de Bambu y usa esa. |
| `There's no Bambu Lab account with that email` | El email no es el de la cuenta de Bambu. Revisa con cuál entras en la app. |
| `Your Bambu Lab account has two-step verification (MFA) enabled` | Hay que desactivar la verificación en dos pasos en Bambu. |
| `Too many attempts` | Espera unos minutos antes de volver a intentarlo. |
| No llega el código | Mira en spam. Comprueba que el email es el de la cuenta de Bambu. Pulsa **Resend code**. |
| `The verification code is wrong or has expired` | Habrá caducado: dura unos 5 minutos. Pide otro y pégalo entero. |

## Desvincular la cuenta

En el mismo bloque, **Unlink account**. Las impresoras que llegaban solo por esa
cuenta pasan a **sin conexión**: siguen en la lista con su número, su nombre y
todo su historial, y vuelven en cuanto las conectes otra vez, por la vía que sea.

**No se borra nada nunca.** Una impresora se identifica por su **número de
serie**, no por su dirección IP, así que puede cambiar de red, de sitio o de
código de acceso y sigue siendo la misma máquina con el mismo historial.

## El siguiente paso: cámara y control

Si te ha sabido a poco —quieres ver el interior, o poder cancelar una impresión
que ha salido mal sin ir hasta la máquina— la vía es el **agente local**.

Y lo mejor: una Bambu que ya tienes por la nube **se puede pasar al agente sin
perder nada**. Conserva su número, su nombre y todo su historial, y deja de
contar dos veces en tu plan. BolloPrint te lo propone solo cuando la añades.

Lo tienes paso a paso en el siguiente tutorial: [conectar impresoras por red
local con el agente](/blog/conectar-impresoras-red-local-agente-bolloprint).

## Documentación relacionada

- [Conectar impresoras](/help/conectar-impresoras) — las dos vías y cuál te conviene
- [Impresoras por la nube](/help/impresoras-por-la-nube) — la referencia completa de esta pantalla
- [Impresoras por red local](/help/impresoras-por-red-local) — la otra vía
- [Tipos de conexión](/help/tipos-de-conexion) — qué permite cada familia de impresora
- [Impresoras compatibles](/help/impresoras-compatibles) — busca aquí tu modelo
