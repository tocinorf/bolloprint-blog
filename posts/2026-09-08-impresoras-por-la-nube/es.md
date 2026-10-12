---
slug: connect-bambu-lab-printers-cloud
title: "Conecta tus impresoras Bambu Lab a BolloPrint en cinco minutos"
description: Conectas tu cuenta de Bambu, confirmas un código que te llega por correo y tus impresoras aparecen solas, con lo que están imprimiendo y todo su historial.
date: 2026-09-08
updated: 2026-10-12
tags: [tutoriales]
cover: 01-portada.webp
draft: true
---

Si tienes varias Bambu trabajando, seguramente conoces la rutina: para saber cómo
van, te acercas a cada una y miras su pantalla. ¿Ha terminado la primera? ¿Le
queda material a la segunda? ¿Cuántas horas llevas impresas este mes? Son
preguntas sencillas, pero responderlas te obliga a estar delante.

Todo eso lo puedes tener en una sola pantalla, y **sin instalar nada**. Basta con
conectar tu cuenta de Bambu Lab a BolloPrint: tus impresoras aparecen solas y el
proceso lleva unos cinco minutos.

::animation{id="bambu-cloud"}

## Qué vas a ver

De cada impresora, en tiempo real: si está encendida, qué está imprimiendo, **el
porcentaje que lleva** y lo que le queda, las temperaturas de la boquilla y de la
cama, los **materiales** cargados (bandeja a bandeja, si tienes AMS) y los avisos
de la propia máquina.

Lo más útil, sin embargo, llega a fin de mes: **cada impresión queda
registrada**, con su duración, el material que ha gastado y lo que te ha costado.
No tienes que apuntar nada.

![La ficha de una impresora imprimiendo, con el progreso y las temperaturas](/blog/media/2026-09-08-impresoras-por-la-nube/06-ficha-impresora.png "42%")

## Antes de empezar

Necesitas tres cosas: entrar en BolloPrint como **Propietario** o **Admin** (con
otro rol esta pantalla no aparece), el **email y la contraseña** de tu cuenta de
Bambu Lab y acceso al **correo** de esa cuenta, porque Bambu te enviará un código.

:::warning ⚠️ Si entras en Bambu con Google, Apple o Facebook
BolloPrint necesita el **email y la contraseña** de la cuenta. Si nunca has
creado una contraseña porque siempre usas «Continuar con Google», créala primero
en la web de Bambu Lab y vuelve después.
:::

## Conecta tu cuenta

Entra en **Configuración → Impresoras**. Verás tres pestañas: **Impresoras**, con
la lista de todas tus máquinas, vengan por donde vengan; **Agente local**, para
conectarlas por tu propia red (lo explicamos en [otro
artículo](/blog/connect-printers-local-network-agent)), y **Bambu Cloud**, que es
la que necesitas ahora. Ábrela.

![La pantalla Configuración → Impresoras con sus tres pestañas](/blog/media/2026-09-08-impresoras-por-la-nube/02-tres-pestanas.png)

Escribe el email y la contraseña de tu cuenta de Bambu Lab (el email de esa
cuenta, no otro) y pulsa **Conectar con Bambu Lab**.

![El formulario de Bambu Cloud, con el email de la cuenta escrito y la contraseña por poner](/blog/media/2026-09-08-impresoras-por-la-nube/03-email-password.png)

La contraseña **no se guarda**: se queda solo en tu navegador, y únicamente hasta
que terminas la verificación.

## Confirma el código

Bambu te enviará un **código de 6 dígitos** desde `noreply@bambulab.com`. Si no
lo encuentras, **revisa la carpeta de spam**, porque suele acabar ahí. Escríbelo
en la misma pantalla y pulsa **Verificar y conectar**.

![El campo del código de 6 dígitos y el botón Verificar y conectar](/blog/media/2026-09-08-impresoras-por-la-nube/04-codigo-verificacion.png)

Dos detalles evitan tener que repetirlo: el código **caduca en unos 5 minutos**
(si se te pasa, pulsa **Reenviar código**), y puedes **pegarlo tal como llega**,
con espacios o guiones incluidos, porque se limpian solos.

Cuando lo acepta, verás **Cuenta verificada y conectada**.

## Tus impresoras ya están dentro

No hace falta dar de alta las impresoras una a una: **todas las de esa cuenta
aparecen solas** en la pestaña **Impresoras**, cada una con su nombre y su número
de serie.

![La lista de impresoras con las máquinas de Bambu recién aparecidas](/blog/media/2026-09-08-impresoras-por-la-nube/05-impresoras-aparecidas.png)

En la parte superior verás un contador del tipo `3 / 6 activas`: son las
impresoras que incluye tu plan. Con el interruptor de cada fila puedes activarlas
o desactivarlas cuando quieras. Una desactivada no cuenta para el límite, pero
**conserva todo su historial**. Y si conectas una flota completa y no hay plazas
para todas, las que no caben entran desactivadas, sin que tu plan se vea
afectado.

## Lo que no puedes hacer por la nube

Conviene saberlo desde el principio para no buscar opciones que no existen.

Por la nube **solo puedes consultar**: no puedes pausar, reanudar ni cancelar una
impresión desde BolloPrint. Bambu solo acepta esas órdenes a través de tu red
local y con la impresora en un modo concreto, que explicamos al final. Tampoco
hay **cámara**; lo que sí ves es la imagen del laminado del trabajo, que es una
vista previa, no lo que ocurre dentro de la máquina.

Además, **dependes de dos conexiones a internet**: la tuya y la de Bambu. Si
falla cualquiera de las dos, la impresora aparece desconectada aunque esté
imprimiendo con normalidad. Y de vez en cuando **la sesión caduca** y hay que
volver a conectar la cuenta; en ese caso te avisamos en pantalla.

Por último, algo que se aplica a cualquier forma de conexión: **BolloPrint no
envía trabajos a imprimir**. El fichero lo sigues mandando desde tu laminador;
BolloPrint lee lo que hace la máquina y lo registra.

## Si no consigue conectar

El problema más habitual es este: aparece **«Cuenta o contraseña de Bambu Lab
incorrectos»** aunque la contraseña es la correcta. Casi siempre ocurre con una
contraseña recién creada que todavía no se ha usado: la cuenta tiene el correo
pendiente de verificar y Bambu no lo indica. Entra **una vez** en la web de Bambu
con ese email y esa contraseña, completa lo que te pida y vuelve a intentarlo.

Si el mensaje es el mismo y entras en Bambu con Google o con Apple, la solución
es crear una contraseña en su web. Si aparece **«No existe una cuenta de Bambu
Lab con ese correo»**, el email no corresponde a tu cuenta de Bambu: comprueba
con cuál entras en su aplicación. Y si te pide **verificación en dos pasos**,
tendrás que desactivarla en Bambu para poder conectar la cuenta.

Si el código no llega, revisa la carpeta de spam y pulsa **Reenviar código**. Si
no lo acepta, probablemente ha caducado: solicita otro y pégalo completo.

## Si necesitas más: el agente local

La nube te muestra toda la información, pero no te permite actuar sobre las
impresoras, y solo está disponible para Bambu Lab. Si necesitas más, la opción es
el **agente local**: un programa pequeño que instalas en un equipo de tu taller y
que se comunica con las impresoras por tu propia red. Con uno solo cubres toda la
flota.

Con el agente puedes conectar **casi todas las marcas** (Prusa, Elegoo, Klipper,
QIDI, Sovol, FlashForge, Voron…), tienes **cámara** en directo y una foto final
guardada en cada impresión, puedes **pausar, reanudar y cancelar** desde
BolloPrint sin ir hasta la máquina, y **sigue funcionando aunque se corte
internet**: continúa leyendo tus impresoras y envía todo cuando vuelve la
conexión.

:::info 💡 Para enviar órdenes a una Bambu
La impresora tiene que estar en **Modo LAN** y en **Modo desarrollador**. Los dos
se activan desde su pantalla.
:::

Lo explicamos paso a paso en
[conecta tus impresoras por tu propia red](/blog/connect-printers-local-network-agent).

Si tienes cualquier duda, escríbenos desde la [página de contacto](/contact) o en
[nuestro Discord](/help/soporte-por-discord).

## Documentación relacionada

- [Conectar impresoras](/help/conectar-impresoras): las dos formas de hacerlo y cuál te conviene
- [Impresoras por la nube](/help/impresoras-por-la-nube): la referencia completa de esta pantalla
- [Impresoras compatibles](/help/impresoras-compatibles): busca aquí tu modelo
- [Tipos de conexión](/help/tipos-de-conexion): qué permite cada tipo de impresora
