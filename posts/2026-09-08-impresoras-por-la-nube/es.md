---
slug: connect-bambu-lab-printers-cloud
title: "Tus Bambu Lab en BolloPrint en cinco minutos (y sin instalar nada)"
description: Conectas tu cuenta de Bambu, esperas un código en el correo y ya. Tus impresoras aparecen solas, con lo que están imprimiendo y todo su historial.
date: 2026-09-08
updated: 2026-10-12
tags: [tutoriales]
cover: 01-portada.webp
draft: true
---

A ver si te suena: tienes tres Bambu trabajando y, para saber cómo van, te
levantas y vas mirando la pantalla de cada una. ¿Habrá terminado la primera? ¿Le
quedará material a la segunda? ¿Y cuántas horas llevas impresas este mes? Ni
idea, claro.

Pues todo eso lo puedes ver desde una sola pantalla, y lo mejor es que **no
tienes que instalar nada**. Le das a BolloPrint tu cuenta de Bambu Lab y tus
impresoras aparecen solas. Te lleva cinco minutos, te lo prometo.

::animation{id="bambu-cloud"}

## ¿Y qué vas a ver, exactamente?

De cada impresora, en vivo: si está encendida, qué está imprimiendo y **por qué
porcentaje va**, cuánto le queda, las temperaturas de la boquilla y de la cama,
qué **materiales** tiene cargados (bandeja a bandeja, si tienes AMS) y los avisos
que dé la propia máquina.

Pero lo que de verdad te va a cambiar el fin de mes es otra cosa: **cada
impresión se queda apuntada**, con lo que tardó, el material que gastó y lo que
te costó. Tú no tienes que apuntar nada.

![La ficha de una impresora imprimiendo, con el progreso y las temperaturas](/blog/media/2026-09-08-impresoras-por-la-nube/06-ficha-impresora.png "42%")

## Antes de empezar, ten esto a mano

Tres cosas. Que entres en BolloPrint como **Propietario** o **Admin** (con otro
rol esta pantalla ni te sale), el **email y la contraseña** de tu cuenta de Bambu
Lab, y el **correo** de esa cuenta abierto, porque Bambu te va a mandar un código.

:::warning ⚠️ ¿Entras en Bambu con Google, Apple o Facebook?
Entonces así no te va a funcionar, porque BolloPrint necesita el **email y la
contraseña**. Si nunca has puesto contraseña porque siempre le das a «Continuar
con Google», créala primero en la web de Bambu Lab y vuelve aquí con ella.
:::

## Vamos a ello

Entra en **Configuración → Impresoras**. Arriba vas a ver tres pestañas: en
**Impresoras** está la lista de todas tus máquinas, vengan por donde vengan; en
**Agente local** se conectan por tu propia red (eso es [otra
historia](/blog/connect-printers-local-network-agent)), y **Bambu Cloud** es la
que nos interesa hoy. Ábrela.

![La pantalla Configuración → Impresoras con sus tres pestañas](/blog/media/2026-09-08-impresoras-por-la-nube/02-tres-pestanas.png)

Ahí escribes el email y la contraseña de tu cuenta de Bambu Lab (ojo, el de esa
cuenta, no otro tuyo) y le das a **Conectar con Bambu Lab**.

![El formulario de Bambu Cloud, con el email de la cuenta escrito y la contraseña por poner](/blog/media/2026-09-08-impresoras-por-la-nube/03-email-password.png)

¿Y la contraseña? Que no te preocupe: **no la guardamos**. Se queda solo en tu
navegador, y solo hasta que termines de verificar.

## El código del correo

En unos segundos te llega un **código de 6 dígitos** desde
`noreply@bambulab.com`. Si no lo ves, **mira en spam**, que cae ahí más de lo que
debería. Lo escribes en la misma pantalla y le das a **Verificar y conectar**.

![El campo del código de 6 dígitos y el botón Verificar y conectar](/blog/media/2026-09-08-impresoras-por-la-nube/04-codigo-verificacion.png)

Dos consejos para no tener que repetirlo: el código **caduca en unos 5 minutos**
(si se te pasa, le das a **Reenviar código**), y **pégalo tal cual venga**, con
sus espacios o sus guiones si los trae, que se limpian solos.

Cuando lo acepta te sale **Cuenta verificada y conectada**. Y ya está, de verdad.

## Tus impresoras, ya dentro

No tienes que dar de alta las impresoras una a una: **todas las de esa cuenta
aparecen solas** en la pestaña **Impresoras**, cada una con su nombre y su número
de serie.

![La lista de impresoras con las máquinas de Bambu recién aparecidas](/blog/media/2026-09-08-impresoras-por-la-nube/05-impresoras-aparecidas.png)

Arriba verás un contador del tipo `3 / 6 activas`, que son las impresoras que
entran en tu plan. Con el interruptor de cada fila las enciendes y las apagas
cuando quieras. Una apagada no cuenta para el límite, pero **sigue ahí con todo
su historial**. Y si conectas una flota entera y no tienes plazas para todas,
las que sobran entran apagadas en vez de romperte el plan.

## Lo que la nube no hace (mejor que lo sepas ya)

Te lo cuento ahora para que no te pases media hora buscando un botón que no
existe.

Por la nube **solo puedes mirar**: no puedes pausar, reanudar ni cancelar una
impresión desde BolloPrint. Bambu solo acepta esas órdenes por tu red local y con
la impresora en un modo especial; te lo explico al final. Tampoco hay **cámara**:
lo que sí ves es la imagen del laminado del trabajo, que es la vista previa, no
lo que está pasando dentro de la máquina.

Ten en cuenta también que **dependes de dos conexiones a internet**, la tuya y
la de Bambu. Si falla cualquiera de las dos, la impresora sale desconectada
aunque esté imprimiendo sin problema. Y de vez en cuando **la sesión caduca** y
hay que volver a conectar la cuenta; no te preocupes, que te avisamos en pantalla.

Ah, y una cosa que vale para todo: **BolloPrint no manda trabajos a imprimir**.
El fichero lo sigues enviando desde tu laminador, como siempre. Nosotros leemos
lo que hace la máquina y lo apuntamos.

## ¿Y si no conecta?

Lo que más tiempo hace perder, con diferencia, es esto: te sale **«Cuenta o
contraseña de Bambu Lab incorrectos»** y tienes clarísimo que la contraseña es
la buena. Casi siempre es porque acabas de crearla y no la has usado nunca, así que
la cuenta tiene el correo pendiente de verificar y Bambu no te lo dice. Entra
**una vez** en la web de Bambu con ese email y esa contraseña, completa lo que te
pida y vuelve a intentarlo.

Si te sale lo mismo y es que entras en Bambu con Google o con Apple, ya sabes:
crea una contraseña en su web. Si te dice **«No existe una cuenta de Bambu Lab con
ese correo»**, el email no es el de tu cuenta de Bambu; mira con cuál entras en su
app. Si te habla de **verificación en dos pasos**, tendrás que desactivarla en
Bambu para poder conectar.

¿Que no llega el código? Mira en spam y dale a **Reenviar código**. ¿Que no lo
acepta? Habrá caducado: pide otro y pégalo entero.

## ¿Te sabe a poco? Prueba el agente local

La nube te lo enseña todo, pero no te deja tocar nada, y además solo existe para
Bambu Lab. Si quieres más, lo tuyo es el **agente local**: un programa pequeño
que pones en un equipo de tu taller y que habla con las impresoras por tu propia
red. Con uno tienes de sobra para toda la flota.

Con él entran **casi todas las marcas** (Prusa, Elegoo, Klipper, QIDI, Sovol,
FlashForge, Voron…), tienes **cámara** en directo y una foto final guardada en
cada impresión, puedes **pausar, reanudar y cancelar** desde BolloPrint sin
moverte de la silla, y **aguanta los cortes de internet**: sigue leyendo tus
impresoras y te lo cuenta todo cuando vuelve la conexión.

:::info 💡 Para mandarle órdenes a una Bambu
La impresora tiene que estar en **Modo LAN** y en **Modo desarrollador**. Los dos
se activan desde su pantalla.
:::

Te lo contamos paso a paso aquí:
[conecta tus impresoras por tu propia red](/blog/connect-printers-local-network-agent).

¿Te has quedado con alguna duda? Escríbenos desde la [página de
contacto](/contact) o pásate por [nuestro Discord](/help/soporte-por-discord), que
te echamos una mano.

## Si quieres más detalle

- [Conectar impresoras](/help/conectar-impresoras): las dos formas de hacerlo y cuál te conviene
- [Impresoras por la nube](/help/impresoras-por-la-nube): todo sobre esta pantalla
- [Impresoras compatibles](/help/impresoras-compatibles): busca aquí tu modelo
- [Tipos de conexión](/help/tipos-de-conexion): qué permite cada tipo de impresora
