---
slug: how-bolloprint-works
title: "Diseño, Pieza, Variante, Producto: el mapa de BolloPrint en cinco minutos"
description: Las cuatro cosas que hay detrás de cada pedido, qué pregunta responde cada una y por qué son cuatro y no una sola ficha. Con un soporte para móvil de ejemplo, de principio a fin.
date: 2026-10-09
updated: 2026-10-12
tags: [tutoriales]
cover: 01-el-mapa.webp
draft: true
---

Entra un pedido: **dos soportes para móvil, en blanco**.

Y antes de que muevas un dedo, BolloPrint ya sabe tres cosas: **lo que te cuesta**
fabricarlos, **lo que te deja** venderlos y **dónde están los ficheros** para
imprimirlos.

¿Cómo lo sabe? Porque detrás de esa línea del pedido hay cuatro cosas que
preparaste una sola vez: un **Diseño**, una **Pieza**, una **Variante** y un
**Producto**. Son las cuatro palabras que más vas a ver en BolloPrint. Aquí te
contamos qué es cada una, por qué son cuatro y no una, y cómo acaban en un pedido.

::animation{id="how-it-works"}

## Cuatro preguntas, cuatro cosas

La forma más fácil de no confundirlas es pensar en la pregunta que responde cada
una:

| | Responde a… | Lo que guarda |
|---|---|---|
| **Diseño** | ¿Qué es? | Los ficheros 3D (STL, 3MF…), las fotos y tus notas. Ni coste ni precio. |
| **Pieza** | ¿Cómo lo fabrico? | El material, el color, el acabado, el peso y el tiempo. **Tiene coste.** |
| **Variante** | ¿A cuánto lo vendo? | El precio y el margen. **Es lo que entra en un pedido.** |
| **Producto** | ¿Cómo lo enseño? | El nombre, las fotos y la descripción. Agrupa las variantes. |

Si te quedas solo con esta tabla, ya tienes la mitad del artículo.

## Lo montamos: un soporte para móvil

Vamos a preparar el soporte del pedido, en el mismo orden en que lo harías tú.

**1. El Diseño.** Subes el STL del soporte y un par de fotos. Eso es el Diseño: el
modelo y nada más. Todavía no has decidido en qué lo vas a imprimir, así que no
tiene coste.

**2. Las Piezas.** Ahora decides cómo lo fabricas. Lo quieres en **PLA negro** y en
**PETG blanco**: son dos Piezas del mismo Diseño. Cada una tiene su material, su
peso y su tiempo de impresión, así que cada una tiene **su coste**, y BolloPrint lo
calcula solo.

![El detalle del diseño del soporte, con sus dos piezas debajo: PLA negro y PETG blanco](/blog/media/2026-10-09-como-funciona-bolloprint/02-diseno-y-piezas.png)

:::info 💡 Una Pieza siempre cuelga de un Diseño
Por eso no hay una lista de Piezas suelta: las encuentras dentro del Diseño al que
pertenecen.
:::

**3. Las Variantes.** Ahora decides a cuánto lo vendes. Creas la Variante «Negro
PLA» a **12,90 €** y la Variante «Blanco PETG» a **15,90 €**. Cada una sabe de qué
Pieza está hecha, así que sabe lo que cuesta, y con el precio calcula sola **el
margen**.

**4. El Producto.** Por último, lo que ve el cliente: el Producto «Soporte para
móvil ajustable», con su nombre, sus fotos y su descripción. Dentro van las dos
Variantes, como las opciones de color de cualquier tienda online. Es lo que
publicas, por ejemplo, en Etsy.

![Las variantes del soporte en pestañas, con la de PETG blanco abierta: su coste, su margen, su precio y la pieza de la que está hecha](/blog/media/2026-10-09-como-funciona-bolloprint/03-producto-y-variantes.png)

## ¿Por qué cuatro y no una ficha?

Es la pregunta que se hace todo el mundo, y la respuesta es sencilla: **cada una de
las cuatro cosas cambia por un motivo distinto.**

- El **Diseño** cambia cuando corriges el modelo.
- La **Pieza**, cuando cambias de material o te sube el coste por hora.
- La **Variante**, cuando tocas el precio.
- El **Producto**, cuando cambias las fotos o la descripción.

Si todo viviera en una sola ficha, corregir el STL te obligaría a tocarlo en cada
color que vendes. Separado, lo corriges una vez, en el Diseño, y vale para todo lo
que cuelga de él.

Si te ayuda pensarlo así: el Diseño es la receta, la Pieza es el plato cocinado y la
Variante es lo que aparece en la carta, con su precio.

### La prueba: un pack

Imagina que también vendes un **organizador de cables**, y se te ocurre un pack: el
soporte negro y el organizador juntos, a 19,90 €.

No hay que preparar nada nuevo. Creas una Variante «Pack oficina» con **dos Piezas
dentro**: la del soporte negro y la del organizador. BolloPrint suma lo que cuestan
las dos y, con el precio, te saca el margen del pack.

![La variante Pack oficina, hecha de dos piezas; y la pieza del soporte negro, usada a la vez por la variante suelta y por el pack](/blog/media/2026-10-09-como-funciona-bolloprint/04-variante-de-dos-piezas.webp)

Fíjate en lo que acaba de pasar: **la Pieza del soporte negro ahora la usan dos
Variantes**, la suelta y el pack. Si mañana te sube el PLA, cambias esa Pieza una
sola vez, y BolloPrint te avisa de qué Variantes la usan para que revises su
precio. Esa es justo la razón de que Pieza y Variante sean cosas distintas.

Y sirve igual para vender varias del mismo: un «Pack x3» es una Variante con tres
veces la misma Pieza.

![El bloque Piezas que componen la variante, con las dos piezas del pack](/blog/media/2026-10-09-como-funciona-bolloprint/05-piezas-de-la-variante.png)

## El pedido cierra el círculo

Volvamos al pedido del principio.

Cuando creas un pedido, lo que añades **es una Variante**: buscas «soporte», eliges
«Blanco PETG», pones 2 unidades, y el precio se rellena solo.

Y como esa Variante sabe de qué Piezas está hecha, la línea del pedido ya trae todo
lo demás:

- **lo que cuesta y lo que deja**, porque las Piezas tienen coste y la Variante tiene
  precio;
- **el material, el color y el peso**, que salen de sus Piezas;
- y **los ficheros para imprimir**: desde la línea, la opción **Diseños** te lleva
  a los modelos 3D de cada Pieza.

Cuando ya lo tienes impreso, marcas la línea como **impresa**, y el pedido sigue su
camino por Producción.

![Un pedido con dos líneas, el soporte blanco y el pack, y al lado las piezas que hay que imprimir para servirlo](/blog/media/2026-10-09-como-funciona-bolloprint/06-del-pedido-a-la-impresora.webp)

Esto es lo que te ahorran las cuatro cosas: no apuntas el coste de cada pedido, no
buscas el STL en una carpeta y no recalculas el margen a mano. Lo preparaste una
vez, y cada pedido lo hereda.

![Las líneas de un pedido, con el menú abierto en la opción Diseños](/blog/media/2026-10-09-como-funciona-bolloprint/07-lineas-del-pedido.png)

## ¿Todo esto cada vez? No

Si te parece mucho trabajo para un solo soporte, tranquilo: para eso está la
**Creación Express**. Le das el STL, el material, el color y el precio en un solo
formulario, y BolloPrint crea de golpe el Diseño, la Pieza, la Variante y el
Producto.

Lo mejor es que el resultado es exactamente el mismo que si lo hubieras hecho paso a
paso. Así que el día que quieras añadir otro color o montar un pack, todo está ya en
su sitio.

![El formulario de Creación Express, con el fichero, el material, el color y el precio](/blog/media/2026-10-09-como-funciona-bolloprint/08-creacion-express.png)

:::info 💡 ¿Dudas?
Escríbenos desde la [página de contacto](/contact) o abre un hilo en
[nuestro Discord](/help/soporte-por-discord). Si nos cuentas qué vendes, te
ayudamos a montarlo.
:::

## Documentación relacionada

- [Catálogo](/help/catalogo) — los cuatro niveles, en la referencia
- [Diseños](/help/disenos) — los ficheros, las fotos y las etiquetas
- [Piezas](/help/piezas) — el material y cómo se calcula el coste
- [Productos y Variantes](/help/productos-y-variantes) — el precio, el margen y las piezas de cada variante
- [Pedidos](/help/pedidos) — de la venta a la entrega
- [Creación Express](/help/creacion-express) — los cuatro de una vez
- [Qué cuesta de verdad una pieza impresa](/blog/calculate-your-3d-printing-costs) — de dónde sale el coste de cada Pieza
