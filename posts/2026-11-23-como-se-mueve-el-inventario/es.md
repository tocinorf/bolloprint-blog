---
slug: how-your-inventory-keeps-itself-up-to-date
title: "Así se mueve tu inventario en BolloPrint: pedidos, punto de venta y eventos"
description: Vendes una bobina, un llavero o te vas a un evento maker, y tu inventario se mantiene al día solo. Te contamos qué hace BolloPrint con tu stock en cada situación.
date: 2026-11-23
tags: [tutoriales]
cover: 08-stock-del-pedido-en.png
draft: true
---

Tener el inventario al día está bien, pero lo que de verdad ahorra trabajo es
que se mantenga al día solo. Vendes un llavero, cobras una bobina en un mercado,
te llevas media estantería a un evento… y al volver no quieres pasarte la tarde
contando qué queda.

En esta guía te contamos qué hace BolloPrint con tu stock en cada situación.

## Primero, qué guarda tu inventario

En **Inventario** BolloPrint separa dos cosas:

- **El Stock**: las **piezas ya impresas** que tienes guardadas, listas para
  montar un producto o venderlas.
- **El material**: tus bobinas de **Filamento**, tus botes de **Resina** y los
  **Suministros** (cajas, imanes, argollas de llavero…). Es lo que compras,
  ¡aunque también puedes venderlo!

## Ahora también puedes vender tu material

Además de tus productos 3D, ahora puedes añadir **filamento, resina y
suministros** a tus pedidos y presupuestos, y venderlos desde el punto de venta.
¿Un cliente te compra una bobina? Sale de tu inventario como cualquier otra
venta.

## Lo que vendes sale del stock

Cuando guardas un pedido, BolloPrint revisa tu inventario para ver qué tienes y
qué no, y te enseña lo que sale:

- Los **materiales** que vendes: bobinas, botes o suministros.
- Las **piezas** de los productos 3D que vendes. Si un producto está formado por
  varias piezas, salen todas del Stock.

Y tú eliges **Quitar del stock** o **No quitar del stock**.

![Al crear un pedido, lo que sale del stock: una bobina de ABS naranja y un llavero, cada uno como una resta (tienes, se quitan, te quedan), una pieza que hay que imprimir porque no queda, y las opciones Quitar del stock y No quitar del stock](/blog/media/2026-11-23-como-se-mueve-el-inventario/08-stock-del-pedido-en.png "80%")

Si no hay suficiente, BolloPrint quita lo que hay (nunca deja el stock en
negativo) y te dice qué falta: una pieza **hay que imprimirla** y un material
**hay que comprarlo**. No te bloquea nada. Y si una línea sale entera del Stock,
se marca como **impresa**, porque ya no hay que imprimirla.

Además:

- Un **presupuesto** no toca el stock hasta que lo aceptas. Al aceptarlo, te
  pregunta igual que un pedido.
- Si **cancelas** un pedido, vuelve al stock solo lo que había salido de él.
- El stock **nunca cambia el estado del pedido**: marcarlo «Listo para enviar»
  lo decides tú, porque aún puede faltar empaquetarlo.

## Pedidos de Etsy y otros marketplaces

Un pedido que llega solo de tu tienda no tiene a nadie a quien preguntar, así que
entra como **stock por decidir**. La primera vez que lo abres, BolloPrint te
pregunta qué hacer con el stock. Y si el comprador lo cancela en el marketplace,
lo que se había quitado vuelve solo.

## En el punto de venta

En el **Punto de venta** no hay preguntas: cobrar ya es la decisión. Lo que
vendes sale del stock y, si anulas la venta, vuelve. Más en
[Punto de venta](/help/punto-de-venta).

## Lo que te llevas a un evento

Si vas a un mercado o un evento maker, al crear un evento en **Eventos** defines
**qué te llevas**: piezas del Stock y material del inventario. Al guardarlo, deja
de contar en tu stock y queda guardado en el stock del evento. Lo que no tengas
en el Stock se da por impreso para la ocasión.

- Lo que **vendes en el evento** con el punto de venta se descuenta de lo que te
  has llevado, no otra vez de tu inventario.
- Al **cerrar el evento**, indicas lo que vuelve: lo que sobra **vuelve al
  stock** y lo que no vuelve (algo roto, algo regalado) cuenta como **pérdida
  del evento**, a su coste.
- El cierre también te dice si **has vendido productos que no te habías
  llevado**, por ejemplo un encargo que entregarás después.

![Qué te llevas en un evento cerrado: de cada pieza, cuántas te llevaste, cuántas vendiste, cuántas volvieron y cuántas no volvieron](/blog/media/2026-11-23-como-se-mueve-el-inventario/09-que-te-llevas-en.png)

:::info 💡 ¿Lo has impreso a propósito para el evento?
Elige **No tocar el Stock**: lo que te lleves no se quita del inventario, y lo
que sobre se suma al cerrar.
:::

Paso a paso, en la ayuda de Eventos:
[Qué te llevas](/help/eventos#qué-te-llevas) y
[Cerrar el evento](/help/eventos#cerrar-el-evento).

## Todo queda apuntado en el Historial

Cada cambio del inventario queda en **Inventario → Historial**: cuándo, qué, por
qué (un pedido, el punto de venta, un evento, un cambio a mano), cuánto y quién
lo hizo. Desde el menú **⋯** de cada fila, **Ver historial** te enseña solo lo
de ese material o esa pieza. Más en la ayuda del
[Historial](/help/inventario#historial).

Las compras se apuntan a mano, con el **+** de la fila o con «Añadir con foto».
Un gasto del **Financiero** no cambia el inventario: así no se suma dos veces la
misma bobina.

## Empieza con el inventario al día

Todo esto funciona mejor si lo que hay en BolloPrint es lo que hay en tus
estanterías. Si aún no has metido tus bobinas y resinas, hazlo con unas fotos a
las etiquetas: te lo contamos en
[sube tu inventario con una foto](/blog/filament-inventory-from-a-photo). A
partir de ahí, tus pedidos, tu punto de venta y tus eventos lo mantienen al día
por ti.

## Documentación relacionada

- [Inventario](/help/inventario): filamento, resina, suministros y Stock
- [Material a la venta](/help/material-a-la-venta): vender bobinas y suministros
- [Detalles de un pedido](/help/detalles-de-un-pedido): las líneas y el stock
- [Pedidos de marketplaces](/help/pedidos-de-marketplaces): los pedidos que llegan solos
- [Punto de venta](/help/punto-de-venta): vender en persona
- [Eventos](/help/eventos): preparar, vender y cerrar un evento
