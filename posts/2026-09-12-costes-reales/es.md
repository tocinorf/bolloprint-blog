---
slug: calculate-your-3d-printing-costs
title: "Qué cuesta de verdad una pieza impresa (y cómo calcularlo sin complicaciones)"
description: Esa pieza de 1,60 € de filamento te cuesta 9,36 €. Te enseñamos a repartir los gastos de tu taller entre tus horas de impresión para que BolloPrint lo aplique solo a cada pieza.
date: 2026-10-15
updated: 2026-10-16
tags: [tutoriales]
cover: 01-portada.webp
---

Una pieza de 6 horas y 80 gramos de PLA. ¿Cuánto te cuesta?

Si has pensado «80 gramos a 20 € el kilo, **1,60 €**», has calculado solo el
**material**. En un taller normal, eso es **una parte pequeña** de lo que
realmente te cuesta la pieza.

En un taller de tres impresoras, con la pieza pintada y embalada, la cuenta
completa es esta:

| | |
|---|---|
| Material | 1,60 € |
| 6 horas de impresora | 5,16 € |
| Acabado (pintada) | 2,00 € |
| Costes extra (embalaje) | 0,60 € |
| **Coste real de la pieza** | **9,36 €** |

**Casi seis veces más.** La diferencia no es un redondeo: es el alquiler, la luz,
el desgaste de las impresoras, la gestoría y las piezas que salen mal. Todo eso
lo pagas; la cuestión es si lo estás cobrando.

Aquí verás cómo llevar esos gastos al coste de cada pieza. **Se configura una
vez** y después se aplica solo a cada pieza que crees.

::animation{id="part-cost"}

## De dónde sale ese 5,16 €

La idea es sencilla: sumas **todo lo que te cuesta el taller al mes** y lo
divides entre **las horas que de verdad imprimes**. Así obtienes lo que te cuesta
**una hora de impresora**, y solo queda multiplicarlo por las horas de la pieza.

Con los números del ejemplo:

- **Horas:** tres impresoras, diez horas al día, veinticinco días al mes →
  **750 horas**.
- **Gastos:** entre alquiler, gestoría, software y la amortización de las
  máquinas se van unos **516 € al mes**. Repartido: 0,69 € la hora. Con la luz,
  los **gastos fijos por hora** quedan en **0,72 €**.
- **Recargos:** un 5 % de mantenimiento, un 10 % de tasa de fallo y un 5 % de
  imprevistos lo llevan a **0,86 € la hora**. Por seis horas, 5,16 €.

Esa es exactamente la cuenta que hace la sección **Costes** de BolloPrint, en
**Configuración → Costes**. Solo la ven el **Propietario** y los **Admins**.

![La sección Costes dentro de Configuración](/blog/media/2026-09-12-costes-reales/02-seccion-costes.png)

Si acabas de empezar, la tarea **Calcula lo que te cuesta cada pieza** de
**Primeros pasos**, en el **Inicio**, te lleva por estas mismas pantallas, una
detrás de otra, y marca en verde cada una en cuanto la guardas.

## Las horas que imprimes de verdad

Empieza por las horas: es el número que más gente calcula mal y el que más
cambia el resultado. Está en **Coste por hora → Horas de impresión**, y son tres
campos:

**Impresoras × Horas al día × Días al mes**

Pon **lo que pasa de verdad, no el máximo teórico**. Si tienes tres impresoras
pero de media trabajan ocho horas al día, son ocho. No veinticuatro.

Es tentador poner un número alto, porque cuanto más alto, más barata sale la
hora. Pero los gastos los pagas igual, y lo que no repartas entre las piezas lo
pagas tú a fin de mes.

![La pestaña de Horas de impresión, con los tres campos y el resultado](/blog/media/2026-09-12-costes-reales/03-horas-impresion.png)

## Lo que te cuesta el taller

Con las horas definidas, toca anotar los gastos. En la pestaña **Gastos fijos** los vas
añadiendo; BolloPrint los ordena por tipo y de cada uno te pide solo lo que
necesita:

| Tipo | Qué le pones |
|---|---|
| **Coste fijo** | Alquiler, internet, gestoría, seguros… el importe al mes |
| **Impresora** | Lo que te costó y en cuántos años la amortizas |
| **Software** | La suscripción al laminador, a BolloPrint, a lo que uses |
| **Nóminas** | El sueldo y cuánta gente |
| **Electricidad** | Los kW que consume una impresora y lo que te cobran el kWh |

No hace falta que sea exacto al céntimo: vale más un número razonable hoy que el
número perfecto el año que viene.

:::warning ⚠️ No metas el mismo gasto dos veces
Los importes **al mes** describen **todo el taller**: el alquiler se pone una
sola vez. Los que van **por hora impresa** —como la electricidad por consumo—
describen **una sola impresora**: ahí pon el consumo de una máquina media, no el
de toda la nave.
:::

Abajo del todo tienes la cuenta hecha, la misma del principio:

> **gastos del mes ÷ tus horas de impresión = lo que te cuesta una hora «en limpio»**

Son tus **gastos fijos por hora**: 0,72 € en el ejemplo.

![Los gastos del taller en la pestaña Gastos fijos, agrupados por tipo, y la cuenta que da 0,72 € la hora](/blog/media/2026-09-12-costes-reales/03b-gastos-fijos.png)

## Lo que sabes que va a pasar

Los gastos fijos dejan fuera lo que ocurre sin una factura fija: se rompen boquillas,
y **alguna pieza sale mal y hay que repetirla**.

Para eso está la pestaña **Coste por hora**, que suma unos porcentajes a los
gastos fijos por hora: mantenimiento, tasa de fallo e imprevistos.

La tasa de fallo es la más importante, y la que más gente se salta. Si de cada
diez piezas una acaba en la basura, **las nueve buenas están pagando la mala**.
Si no la incluyes aquí, la pagas tú.

El resultado es tu **coste por hora**: 0,86 € en el ejemplo. Ese es tu
número real, y es el que se aplica a cada pieza.

:::info 💡 El margen de beneficio no va aquí
Aquí solo van **costes**. Cuánto quieres ganar se decide después, en el producto,
porque es una decisión comercial.
:::

![Los recargos de mantenimiento, tasa de fallo e imprevistos sobre los gastos fijos por hora, hasta 0,86 € la hora](/blog/media/2026-09-12-costes-reales/03c-coste-por-hora.png)

## El material y los extras

Queda la parte más sencilla, en **Valores por defecto**:

- **El precio de cada material**, por kilo. Es **por tipo**, no por familia: el
  PLA y el TPU no cuestan lo mismo.
- **Los acabados**: cuánto recargas si la pieza va postprocesada o pintada.
- **Los costes extra**: embalaje, tornillería, imanes, insertos, mano de obra.
  De cada uno eliges si se cobra **por unidad** o **por placa**.
- **Los márgenes**: el que quieres por defecto, y desde qué porcentaje te
  avisamos en rojo o en naranja.

:::info 💡 Si tienes el material en el inventario, manda el inventario
Estos precios son de referencia, para cuando no hay nada detrás. Si la pieza sale
de una bobina dada de alta con su coste real, usamos ese.
:::

![Valores por defecto: los márgenes con sus avisos de color y el precio de cada material por kilo](/blog/media/2026-09-12-costes-reales/03d-valores-por-defecto.png)

## Y así llega a tu pieza

Los cuatro pasos anteriores acaban en un solo número: **lo que te cuesta una hora
de impresora**. A partir de ahí, cada pieza es una suma:

> sus **horas × tu coste por hora**
> **+** el **material** que lleva
> **+** el **acabado**, si va postprocesada o pintada
> **+** los **costes extra** que le añadas

Conviene entender un detalle, porque explica por qué compensa llenar la cama:
**la cuenta se hace por placa, no por pieza**. BolloPrint calcula lo que cuesta
la placa entera y lo **reparte entre las piezas que salen de ella**. Por eso, de
los costes extra, los que marcas **por placa** se cobran una sola vez —imprimas
las piezas de una en una o de veinte en veinte— y los de **por unidad** se cobran
en cada pieza.

Además, cada pieza **guarda el coste por hora con el que se calculó**. Es
intencionado: así el coste de lo que imprimiste el año pasado sigue siendo el de
entonces. Por eso existe el botón **Recalcular**, que verás un poco más abajo.

## Ahora ya tienes tu número

Para ver el resultado, ve a **Costes → Resumen**. El bloque **Ejemplo** coge una
placa de muestra y te enseña la cuenta entera **con tus valores**: cuánto es
material, cuánto impresión, cuánto acabado y cuánto sale la pieza.

![El bloque de Ejemplo con el desglose completo de una pieza](/blog/media/2026-09-12-costes-reales/04-ejemplo-coste.png)

## Cuando cambien tus gastos

Tus números no serán siempre los mismos: sube la luz, compras otra impresora o
cambias de local. Al actualizarlos, **las piezas que ya tenías no cambian
solas**. Es a propósito: cada pieza guarda el coste con el que se calculó, y no
querrías que se reescribiera el de todo lo que hiciste el año pasado.

Cuando quieras aplicarlo a todo, en **Resumen** tienes un contador de piezas
**por recalcular** y el botón **Recalcular**. Tú decides cuándo.

:::info 💡 No te toca los precios de venta
Recalcular actualiza el **coste** y el precio *sugerido*. El que tú hayas puesto a
mano se queda. Lo que vas a ver moverse es el indicador de **margen**.
:::

## ¿Me compro otra impresora?

Con tus costes configurados, puedes responder a esta pregunta con números. En
**Escenarios de coste** cambias las impresoras, las horas o los días y ves qué
le pasaría a tu coste por hora. Solo simula: no cambia nada de tu configuración.

Lo que mejor enseña es que **la curva deja de bajar**. Pasar de una impresora a
cinco divide el coste por hora casi entre cinco. Pasar de veinte a cien apenas lo
mueve, porque hay gastos —como la luz— que se pagan en cada hora impresa y no se
reparten entre nadie.

![Los escenarios de coste, con la curva del coste por hora](/blog/media/2026-09-12-costes-reales/05-comparador.png)

Configurarlo son cuatro pantallas y un rato de una tarde. A cambio, cada pieza
que crees llevará su coste real, y sabrás si estás ganando dinero sin hacer la
cuenta a mano.

:::info 💡 ¿Te ayudamos con tus números?
Si no sabes por dónde empezar, escríbenos desde la [página de contacto](/contact)
o en [nuestro Discord](/help/soporte-por-discord). Ya lo hemos hecho unas cuantas
veces.
:::

Que tus números salgan siempre a cuenta.

![Bollo, la mascota de BolloPrint, con gafas de taller, pensativo entre operaciones escritas con tiza](/blog/media/2026-09-12-costes-reales/07-bollo.webp "60%")

## Documentación relacionada

- [Costes](/help/costes): la referencia completa de la sección
- [Piezas](/help/piezas): cómo se calcula el coste de cada pieza
- [Productos y Variantes](/help/productos-y-variantes): del coste al precio de venta
- [Inventario](/help/inventario): para que el material salga de su coste real
