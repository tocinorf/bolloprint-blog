---
slug: connect-bambu-lab-printers-cloud
title: "Conecta tus impresoras Bambu Lab a BolloPrint en cinco minutos"
description: Sin instalar nada. Conectas tu cuenta de Bambu Lab, confirmas un código y tus impresoras aparecen solas, con lo que están imprimiendo y todo su historial.
date: 2026-09-08
updated: 2026-10-12
tags: [tutoriales]
cover: 01-portada.webp
---

Si tienes varias Bambu trabajando, seguramente conoces la rutina: para saber cómo
van, te acercas a cada una y miras su pantalla. ¿Ha terminado la primera? ¿Le
queda material a la segunda? ¿Cuántas horas llevas impresas este mes?

Todo eso lo puedes tener en una sola pantalla y **sin instalar nada**. Conectas
tu cuenta de Bambu Lab a BolloPrint y tus impresoras aparecen solas. Son unos
cinco minutos.

::animation{id="bambu-cloud"}

## Qué vas a ver de cada impresora

En tiempo real y sin tocar nada:

- si está encendida y conectada;
- qué está imprimiendo, el **porcentaje** que lleva y lo que le queda;
- las temperaturas de la boquilla y de la cama;
- los **materiales** cargados, bandeja a bandeja, si tienes AMS;
- los avisos de la propia máquina.

Y lo que más se nota a fin de mes: **cada impresión queda registrada**, con su
duración, su material y su coste. No tienes que apuntar nada.

![La ficha de una impresora imprimiendo, con el progreso y las temperaturas](/blog/media/2026-09-08-impresoras-por-la-nube/06-ficha-impresora.png "42%")

## Lo que necesitas

Antes de empezar, ten a mano estas tres cosas:

- Acceso a BolloPrint como **Propietario** o **Admin**. Con otro rol esta
  pantalla no aparece.
- El **email y la contraseña** de tu cuenta de Bambu Lab.
- El **correo** de esa cuenta abierto: Bambu te enviará un código.

:::warning ⚠️ Si entras en Bambu con Google, Apple o Facebook
BolloPrint necesita el **email y la contraseña** de la cuenta. Si nunca has
creado una contraseña porque siempre usas «Continuar con Google», créala primero
en la web de Bambu Lab y vuelve después.
:::

## Abre la pantalla de impresoras

Todo se hace desde un mismo sitio: **Configuración → Impresoras**. Ahí verás tres
pestañas:

- **Impresoras**: la lista de todas tus máquinas, vengan por donde vengan.
- **Agente local**: para conectarlas por tu propia red. Lo explicamos en
  [otro artículo](/blog/connect-printers-local-network-agent).
- **Bambu Cloud**: la que necesitas ahora.

Abre **Bambu Cloud**.

![La pantalla Configuración → Impresoras con sus tres pestañas](/blog/media/2026-09-08-impresoras-por-la-nube/02-tres-pestanas.png)

## Escribe el email y la contraseña de Bambu

Usa los de tu cuenta de Bambu Lab (ese email, no otro tuyo) y pulsa **Conectar
con Bambu Lab**.

![El formulario de Bambu Cloud, con el email de la cuenta escrito y la contraseña por poner](/blog/media/2026-09-08-impresoras-por-la-nube/03-email-password.png)

:::info 💡 Tu contraseña no se guarda
Se queda **solo en tu navegador**, y únicamente hasta que terminas la verificación.
:::

## Confirma el código del correo

Bambu te enviará un **código de 6 dígitos** desde `noreply@bambulab.com`. Si no
lo ves, **revisa la carpeta de spam**: suele acabar ahí. Escríbelo en la misma
pantalla y pulsa **Verificar y conectar**.

![El campo del código de 6 dígitos y el botón Verificar y conectar](/blog/media/2026-09-08-impresoras-por-la-nube/04-codigo-verificacion.png)

Dos detalles te ahorran un segundo intento:

- El código **caduca en unos 5 minutos**. Si se te pasa, pulsa **Reenviar código**.
- Puedes **pegarlo tal como llega**: los espacios o guiones se limpian solos.

Cuando lo acepta, verás **Cuenta verificada y conectada**.

## Tus impresoras ya están dentro

No hace falta darlas de alta una a una: **todas las impresoras de esa cuenta
aparecen solas** en la pestaña **Impresoras**, cada una con su nombre y su número
de serie.

![La lista de impresoras con las máquinas de Bambu recién aparecidas](/blog/media/2026-09-08-impresoras-por-la-nube/05-impresoras-aparecidas.png)

Arriba verás un contador del tipo `3 / 6 activas`: son las impresoras que incluye
tu plan. Con el interruptor de cada fila activas o desactivas las que quieras. Una
desactivada no cuenta para el límite, pero **conserva todo su historial**. Y si
conectas una flota entera y no hay plazas para todas, las que no caben entran
desactivadas en lugar de superar el límite de tu plan.

## Qué no puedes hacer por la nube

Conviene saberlo desde el principio para no buscar opciones que no existen:

- **Es solo lectura.** Por la nube no se puede pausar, reanudar ni cancelar
  desde BolloPrint: Bambu solo acepta esas órdenes por tu red local y con la
  impresora en un modo concreto. Lo vemos al final.
- **No hay cámara.** Sí ves la imagen del laminado del trabajo, que es una vista
  previa, no lo que ocurre dentro de la máquina.
- **Depende de dos conexiones a internet**, la tuya y la de Bambu. Si falla
  cualquiera, la impresora aparece desconectada aunque esté imprimiendo con
  normalidad.
- **La sesión caduca de vez en cuando** y hay que volver a conectar la cuenta.
  Te avisamos en pantalla.

Y algo que vale para cualquier forma de conexión: **BolloPrint no envía trabajos
a imprimir**. El fichero lo sigues mandando desde tu laminador; BolloPrint lee lo
que hace la máquina y lo registra.

## Problemas frecuentes

### ¿Por qué Bambu dice que la contraseña es incorrecta si es la buena?

Es el problema más habitual. Aparece **«Cuenta o contraseña de Bambu Lab
incorrectos»** casi siempre con una contraseña recién creada que aún no se ha
usado: la cuenta tiene el correo pendiente de verificar y Bambu no lo indica.
Entra **una vez** en la web de Bambu con ese email y esa contraseña, completa lo
que te pida y vuelve a intentarlo.

### ¿Y si entro en Bambu con Google o Apple?

Por esa vía no se puede. Crea una contraseña en la web de Bambu Lab y usa el
email y esa contraseña.

### ¿Por qué dice que no existe una cuenta con ese correo?

Si aparece **«No existe una cuenta de Bambu Lab con ese correo»**, el email no es
el de tu cuenta de Bambu. Comprueba con cuál entras en su aplicación.

### ¿Qué hago si me pide verificación en dos pasos?

Tendrás que desactivarla en tu cuenta de Bambu para poder conectarla.

### ¿Qué hago si el código no llega o no lo acepta?

Si no llega, revisa la carpeta de spam y pulsa **Reenviar código**. Si no lo
acepta, lo más probable es que haya caducado: pide otro y pégalo completo.

## Si necesitas más: el agente local

La nube te muestra toda la información, pero no te permite actuar sobre las
impresoras, y solo existe para Bambu Lab. Si necesitas más, la opción es el
**agente local**: un programa pequeño que instalas en un equipo de tu taller y
que habla con las impresoras por tu propia red. Con uno basta para toda la flota,
y te da:

- **casi todas las marcas**: Prusa, Elegoo, Klipper, QIDI, Sovol, FlashForge,
  Voron…;
- **cámara**, en directo y con una foto final guardada en cada impresión;
- **pausar, reanudar y cancelar** desde BolloPrint, sin ir hasta la máquina;
- **resistencia a los cortes de internet**: sigue leyendo tus impresoras y envía
  todo cuando vuelve la conexión.

:::info 💡 Para enviar órdenes a una Bambu
La impresora tiene que estar en **Modo LAN** y en **Modo desarrollador**. Los dos
se activan desde su pantalla.
:::

Lo explicamos paso a paso en
[conecta tus impresoras por tu propia red](/blog/connect-printers-local-network-agent).

Si tienes cualquier duda, escríbenos desde la [página de contacto](/contact) o en
[nuestro Discord](/help/soporte-por-discord).

Que disfrutes de tener todas tus impresoras en una sola pantalla.

![Bollo, la mascota de BolloPrint, con gafas de taller, soñando con una impresora 3D](/blog/media/2026-09-08-impresoras-por-la-nube/07-bollo.webp)

## Documentación relacionada

- [Conectar impresoras](/help/conectar-impresoras): las dos formas de hacerlo y cuál te conviene
- [Impresoras por la nube](/help/impresoras-por-la-nube): la referencia completa de esta pantalla
- [Impresoras compatibles](/help/impresoras-compatibles): busca aquí tu modelo
- [Tipos de conexión](/help/tipos-de-conexion): qué permite cada tipo de impresora
