---
slug: filament-inventory-from-a-photo
title: "Tu inventario de filamento con una foto: así se añaden bobinas y resinas en BolloPrint"
description: Haz fotos a las etiquetas de tus bobinas y frascos de resina y BolloPrint los añade a tu inventario. Te contamos cómo funciona y cómo se mueve después el stock con tus pedidos, el punto de venta y los eventos.
date: 2026-11-22
tags: [tutoriales]
draft: true
---

Llega el pedido de filamento: diez bobinas, cuatro marcas, seis colores. Toca
darlas de alta en el inventario, una a una: buscar la marca, el material, el
color, el peso… Y si no lo haces en ese momento, a la semana ya no sabes cuántas
bobinas de PETG negro te quedan.

Por eso en BolloPrint ahora puedes **añadir filamentos y resinas con una foto de
su etiqueta**. Haces las fotos, BolloPrint las lee y tú solo confirmas lo que no
esté claro. En esta guía te contamos cómo funciona paso a paso y, ya que estamos,
cómo se mueve después ese stock cuando vendes.

## Primero, qué guarda tu inventario

En **Inventario** BolloPrint separa dos cosas:

- **El material**: tus bobinas de **Filamento**, tus frascos de **Resina** y los
  **Suministros** (cajas, imanes, argollas de llavero…). Es lo que compras.
- **El Stock**: las **piezas ya impresas** que tienes guardadas, listas para
  montar un producto o venderlas.

«Añadir con foto» sirve para el material: filamentos y resinas.

## Añadir con foto, paso a paso

### 1. Haz las fotos

En **Inventario → Filamento** (o **Resina**) pulsa **Añadir con foto**.

- **En el ordenador**, arrastra las fotos a la ventana o haz clic en ella para
  elegirlas.
- **En el móvil**, elige **Hacer fotos** para usar la cámara o **Desde la
  galería** si ya las tienes hechas.

Puedes hacer **hasta 50 fotos de una vez**: todas las bobinas que acaban de
llegar, en una sola revisión. Arriba de la cámara te recordamos qué tiene que
salir en la foto: la **marca**, la **referencia**, el **color** y el **peso**.

:::info 💡 Fotos nítidas a la primera
Si la foto sale movida, BolloPrint te lo dice al momento para que la repitas.
Hay **linterna** para los rincones oscuros del taller y, si tu móvil enfoca mejor
con su propia cámara, el botón **Usar la cámara del móvil** la abre y las fotos
van al mismo montón.
:::

Un truco: puedes hacer las fotos con el móvil en el almacén y revisarlas después
en el ordenador. La revisión se guarda sola y la sigues en el dispositivo que
quieras.

### 2. BolloPrint lee las etiquetas

Mientras haces fotos, se van subiendo y BolloPrint las lee una a una. No hace
falta que esperes con la ventana abierta: abajo verás «Subiendo fotos de
etiquetas · 2 de 6» y puedes seguir trabajando en otra parte de la app. Si se va
la conexión, las fotos pendientes se suben solas cuando vuelve.

### 3. Revisa solo lo que hace falta

Cuando terminan, se abre **Revisar las fotos**. Cada foto sale con su estado:

- **Seguro**: BolloPrint sabe qué material es. No tienes que hacer nada.
- **No seguro**: ha encontrado varios candidatos y te pregunta **¿Cuál de estos
  es?** Por ejemplo, cuando el mismo filamento se vende en bobinas de 1 kg y de
  250 g y en la etiqueta no se ve el peso.
- **Falta la marca**: se lee el material, pero no el fabricante. Lo eliges de la
  lista.
- **Foto sin datos**: no se lee lo suficiente. Puedes **Cambiar foto** o buscar el
  material con lo que se haya leído.
- **Repetida**: dos fotos de la misma etiqueta. BolloPrint te dice cuál es la
  otra y la descartas.

Con **Revisar** vas pasando solo por las dudosas; las seguras se quedan en la
lista. En cada material ves lo que se ha leído de la etiqueta y cuántas unidades
vas a sumar: «En tu inventario: 2 → 3». Si has comprado tres bobinas iguales,
ajustas la cantidad con **+** y **−** sin hacer tres fotos.

¿No es el que sale? **Buscar otro** abre el catálogo de materiales. La búsqueda
es tolerante: «PLA+ 2.0», «pla 2.0» y «PLA+2.0» encuentran lo mismo, y puedes
escribir el color en tu idioma («blanco», «seda»…).

### 4. Añade todo de una vez

Nada entra en tu inventario hasta el final. Cuando lo tienes, pulsa **Añadir** y
todos los materiales identificados se suman de golpe. Si alguno se ha quedado sin
identificar, BolloPrint te avisa antes: puedes volver a revisarlo o añadir el
resto y dejarlo fuera.

### ¿Y si tu filamento no está en el catálogo?

Puede pasar con una marca pequeña o un color recién salido. Si BolloPrint sabe
qué es pero aún no está en el catálogo de materiales, te lo dice y pide que lo
añadan, con la foto y un número de caso. **No tienes que hacer nada.** Y si no lo
reconoce, desde la propia foto puedes **Pedir que lo añadan**.

:::info 🔒 Planes Pro y Max
«Añadir con foto» está en los planes **Pro** y **Max**. Las fotos de las
etiquetas no ocupan espacio de tu plan: se borran al terminar la revisión.
:::

## Y después, ¿cómo se mueve el stock?

Tener el inventario al día está bien, pero lo que de verdad ahorra trabajo es
que se mantenga al día solo. Esto es lo que hace BolloPrint con tu stock en cada
situación.

### También puedes vender material

En pedidos, presupuestos y el punto de venta puedes añadir, además de tus
productos 3D, **filamento, resina y suministros** como líneas del pedido. ¿Un
cliente te pide una bobina? Sale de tu inventario como cualquier otra venta.

### Lo que vendes sale del stock

Al guardar un pedido, BolloPrint calcula qué sale del inventario:

- Las **líneas de material** quitan sus bobinas, frascos o suministros.
- Los **productos 3D** quitan las **piezas** de las que están hechos. Si un
  producto lleva tres piezas y vendes dos, salen seis piezas del Stock.

Antes de tocar nada, te lo enseña como una resta, **Tienes − Se quitan = Te
quedan**, y eliges **Quitar del stock** o **No quitar del stock**.

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

### Pedidos de Etsy y otros marketplaces

Un pedido que llega solo de tu tienda no tiene a nadie a quien preguntar, así que
entra como **stock por decidir**. La primera vez que lo abres, BolloPrint te
pregunta qué hacer con el stock. Y si el comprador lo cancela en el marketplace,
lo que se había quitado vuelve solo.

### En el punto de venta

En el **Punto de venta** no hay preguntas: cobrar ya es la decisión. Lo que
vendes sale del stock y, si anulas la venta, vuelve.

### Lo que te llevas a un evento

Si vas a un mercado o un evento maker, en **Eventos** preparas **qué te llevas**:
piezas del Stock y material del inventario. Al guardarlo, eso sale del stock y
queda «en el evento». Lo que no tengas en el Stock se da por impreso para la
ocasión.

- Lo que **vendes en el evento** con el punto de venta se descuenta de lo que te
  has llevado, no otra vez de tu inventario.
- Al **cerrar el evento**, indicas lo que vuelve: lo que sobra **vuelve al
  stock** y lo que no vuelve (algo roto, algo regalado) cuenta como **pérdida
  del evento**, a su coste.
- El cierre también te dice si **has vendido productos que no te habías
  llevado**, por ejemplo un encargo que entregarás después.

:::info 💡 ¿Ya lo has impreso todo a propósito para el evento?
Elige **No tocar el Stock**: lo que te lleves no se quita del inventario, y lo
que sobre se suma al cerrar.
:::

### Todo queda apuntado en el Historial

Cada cambio del inventario queda en **Inventario → Historial**: cuándo, qué, por
qué (un pedido, el punto de venta, un evento, un cambio a mano), cuánto y quién
lo hizo. Desde el menú **⋯** de cada fila, **Ver historial** te enseña solo lo
de ese material o esa pieza.

Las compras se apuntan a mano, con el **+** de la fila o con «Añadir con foto».
Un gasto del **Financiero** no cambia el inventario: así no se suma dos veces la
misma bobina.

## Empieza por la próxima caja que te llegue

La próxima vez que llegue un paquete de filamento, no lo dejes para luego: abre
**Inventario**, pulsa **Añadir con foto** y haz las fotos antes de guardar las
bobinas. En un par de minutos tienes el inventario al día y, a partir de ahí,
tus pedidos, tu punto de venta y tus eventos lo mantienen al día por ti.

Si te preguntas cuánto te cuesta de verdad cada pieza con ese filamento, lo
contamos en
[qué cuesta de verdad una pieza impresa](/blog/calculate-your-3d-printing-costs).

## Documentación relacionada

- [Inventario](/help/inventario): filamento, resina, suministros y Stock
- [Material a la venta](/help/material-a-la-venta): vender bobinas y suministros
- [Detalles de un pedido](/help/detalles-de-un-pedido): las líneas y el stock
- [Pedidos de marketplaces](/help/pedidos-de-marketplaces): los pedidos que llegan solos
- [Punto de venta](/help/punto-de-venta): vender en persona
- [Eventos](/help/eventos): preparar, vender y cerrar un evento
