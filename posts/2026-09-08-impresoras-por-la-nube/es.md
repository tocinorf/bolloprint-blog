---
slug: connect-bambu-lab-printers-cloud
title: "Conecta tus impresoras Bambu Lab a BolloPrint en cinco minutos"
description: Sin instalar nada. Conectas tu cuenta de Bambu y tus máquinas aparecen solas, con lo que están imprimiendo y todo su historial.
date: 2026-09-08
updated: 2026-10-12
tags: [tutoriales]
cover: 01-portada.webp
draft: true
---

Tienes tres Bambu trabajando y, para saber cómo van, te levantas y miras la
pantalla de cada una. ¿Ha terminado la primera? ¿Le queda material a la segunda?
¿Cuántas horas llevas impresas este mes?

Hay una forma de verlo todo desde una sola pantalla, y **no hay que instalar
nada**. Conectas tu cuenta de Bambu Lab a BolloPrint y tus máquinas aparecen
solas. Cinco minutos.

::animation{id="bambu-cloud"}

## Esto es lo que vas a tener

De cada impresora, en vivo y sin tocar nada:

- si está encendida y conectada;
- qué está imprimiendo, el **porcentaje** y lo que le queda;
- las temperaturas de boquilla y cama;
- los **materiales** cargados, bandeja a bandeja, si tienes AMS;
- los avisos de la propia máquina.

Y además, lo que de verdad cambia las cosas a fin de mes: **cada impresión queda
registrada**, con su duración, su material y su coste. Sin apuntar nada a mano.

![La ficha de una impresora imprimiendo, con el progreso y las temperaturas](/blog/media/2026-09-08-impresoras-por-la-nube/06-ficha-impresora.png "42%")

## Lo que necesitas

- Entrar en BolloPrint como **Propietario** o **Admin**. Con otro rol esta
  pantalla no te sale.
- Tu cuenta de **Bambu Lab**, con su **email y su contraseña**.
- Poder abrir el **correo** de esa cuenta: Bambu te va a mandar un código.

:::warning ⚠️ Si entras en Bambu con Google, Apple o Facebook, esto no te va a funcionar
BolloPrint necesita el **email y la contraseña** de tu cuenta de Bambu. Si nunca
has puesto contraseña porque siempre pulsas «Continuar con Google», créala
primero en la web de Bambu Lab y vuelve aquí con ella.
:::

## Paso 1 — Abre la pantalla de impresoras

Ve a **Configuración → Impresoras**. Verás tres pestañas:

- **Impresoras** — la lista de todas tus máquinas, vengan por donde vengan.
- **Agente local** — para conectar por tu red. Eso es [otro tutorial](/blog/connect-printers-local-network-agent).
- **Bambu Cloud** — la que nos interesa hoy.

Abre **Bambu Cloud**.

![La pantalla Configuración → Impresoras con sus tres pestañas](/blog/media/2026-09-08-impresoras-por-la-nube/02-tres-pestanas.png)

## Paso 2 — Escribe tu email y tu contraseña de Bambu

Los de tu cuenta de Bambu Lab —ese email, no otro tuyo— y pulsa **Conectar con
Bambu Lab**.

![El formulario de Bambu Cloud, con el email de la cuenta escrito y la contraseña por poner](/blog/media/2026-09-08-impresoras-por-la-nube/03-email-password.png)

:::info 💡 Tu contraseña no se guarda
Se queda **solo en tu navegador**, y solo hasta que termines de verificar.
:::

## Paso 3 — Mete el código que te llega por correo

Bambu te manda un **código de 6 dígitos** desde `noreply@bambulab.com`. **Mira
también en spam**, cae ahí más de lo que debería.

Escribe los seis dígitos en la misma pantalla y pulsa **Verificar y conectar**.

![El campo del código de 6 dígitos y el botón Verificar y conectar](/blog/media/2026-09-08-impresoras-por-la-nube/04-codigo-verificacion.png)

Dos detalles que te ahorran un segundo intento: **el código caduca en unos 5
minutos** —si tardas, pulsa **Reenviar código**— y **pégalo entero tal como
venga**, que si trae espacios o guiones se limpian solos.

Cuando lo acepta, verás **Cuenta verificada y conectada**.

## Paso 4 — Ya están ahí

No hay que dar de alta las impresoras una a una. **Todas las máquinas de esa
cuenta aparecen solas** en la pestaña **Impresoras**, cada una con su nombre y su
número de serie.

![La lista de impresoras con las máquinas de Bambu recién aparecidas](/blog/media/2026-09-08-impresoras-por-la-nube/05-impresoras-aparecidas.png)

Arriba hay un contador tipo `3 / 6 activas`: las impresoras que incluye tu plan.
Con el interruptor de cada fila enciendes y apagas las que quieras. Una apagada
no cuenta para el límite, pero **sigue en la lista con todo su historial**.

Y si conectas una flota entera y no hay plazas para todas, las que sobran entran
**desactivadas** en vez de romperte el plan.

## Qué NO vas a poder hacer por aquí

Mejor saberlo ahora que buscar el botón durante media hora:

- **Es solo lectura.** Por la nube no se puede pausar, reanudar ni cancelar
  desde BolloPrint: Bambu solo acepta esas órdenes por tu red local, y con la
  impresora en un modo especial. Lo vemos al final.
- **No hay cámara.** Por la nube no llega. Sí llega la imagen del laminado del
  trabajo, que es la vista previa, no lo que está pasando dentro.
- **Depende de internet dos veces:** del tuyo y del de Bambu. Si falla
  cualquiera, la impresora aparece desconectada aunque esté imprimiendo
  perfectamente.
- **La sesión caduca de vez en cuando** y hay que volver a conectar la cuenta.
  Te avisamos en pantalla.

Y una que vale para todas las vías: **BolloPrint no manda trabajos a imprimir**.
El fichero lo sigues enviando desde tu laminador. Lo que hacemos es leer lo que
la máquina hace y registrarlo.

## Si no consigues conectar

| Lo que ves | Qué suele ser |
|---|---|
| «Cuenta o contraseña de Bambu Lab incorrectos» y estás seguro de que es la buena | **Es el fallo que más tiempo hace perder.** Si acabas de crear esa contraseña y no la has usado nunca, la cuenta tiene el correo pendiente de verificar y Bambu no te lo dice. Entra **una vez** en la web de Bambu con esas credenciales, completa lo que te pida, y vuelve. |
| «Cuenta o contraseña de Bambu Lab incorrectos» y entras a Bambu con Google o Apple | Esa vía no sirve aquí. Crea una contraseña en la web de Bambu. |
| «No existe una cuenta de Bambu Lab con ese correo» | El email no es el de la cuenta de Bambu. Mira con cuál entras en su app. |
| Te habla de verificación en dos pasos | Hay que desactivarla en Bambu para poder conectar la cuenta. |
| No llega el código | Mira en spam y pulsa **Reenviar código**. |
| No acepta el código | Habrá caducado. Pide otro y pégalo entero. |

## ¿Quieres más? Prueba el agente local

La nube te lo enseña todo, pero no te deja tocar nada, y solo existe para Bambu
Lab. Si quieres más, lo tuyo es el **agente local**: un programa pequeño en un
equipo de tu taller que habla con las impresoras por tu propia red. Con uno basta
para toda la flota, y te da:

- **casi todas las marcas**: Prusa, Elegoo, Klipper, QIDI, Sovol, FlashForge,
  Voron…;
- **cámara**, en directo mientras la miras y con una foto final guardada en cada
  impresión;
- **pausar, reanudar y cancelar** desde BolloPrint, sin ir hasta la máquina;
- y **aguanta los cortes de internet**: sigue leyendo tus impresoras y te lo
  cuenta todo al volver.

:::info 💡 Para mandar órdenes a una Bambu
La impresora tiene que estar en **Modo LAN** y en **Modo desarrollador**. Los dos
se activan en su pantalla.
:::

Lo tienes paso a paso en el siguiente tutorial:
[conectar tus impresoras por red local](/blog/connect-printers-local-network-agent).

:::info 💡 ¿Dudas?
Escríbenos desde la [página de contacto](/contact) o abre un hilo en
[nuestro Discord](/help/soporte-por-discord).
:::

## Documentación relacionada

- [Conectar impresoras](/help/conectar-impresoras) — las dos vías y cuál te conviene
- [Impresoras por la nube](/help/impresoras-por-la-nube) — la referencia completa de esta pantalla
- [Impresoras compatibles](/help/impresoras-compatibles) — busca aquí tu modelo
- [Tipos de conexión](/help/tipos-de-conexion) — qué permite cada familia de impresora
