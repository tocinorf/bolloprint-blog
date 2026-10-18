---
slug: organize-your-3d-printing-catalog
title: "De archivos STL a productos en tu tienda: cómo organizar tu catálogo de impresión 3D"
description: Aprende a estructurar tus archivos STL, calcular costes por pieza y crear variantes de productos para tu tienda de impresión 3D sin complicaciones.
date: 2026-10-15
tags: [tutoriales]
cover: 01-portada.webp
draft: true
---

Si imprimes en 3D para vender, seguro que conoces esta escena: decenas de carpetas
en el ordenador con archivos llamados `llavero_V2_FINAL_definitivo.stl`, sin
recordar cuánto filamento gastaba esa versión ni qué perfil de laminado usaste. Y
cuando entra un pedido en Etsy, calculas tus costes a ojo y esperas no perder
dinero.

En un taller o una granja de impresión 3D, el lío técnico y el comercial se cruzan
si no los separas. Por eso BolloPrint los trata por separado. En esta guía te
explicamos cómo encajan **Diseños, Piezas, Productos y Variantes**, para que pases
de un montón de archivos sueltos a un catálogo ordenado.

::animation{id="how-it-works"}

## Separa lo técnico de lo comercial

Uno de los errores más habituales al gestionar un taller es tratar un archivo STL
como si fuera el producto que vendes. En la práctica, un mismo modelo 3D se puede
imprimir en distintos materiales, llevar varias partes o venderse en packs.

Por eso BolloPrint organiza tu catálogo en tres niveles.

### Diseños: la biblioteca técnica

El **Diseño** es el contenedor de tus archivos de origen: los STL, OBJ o proyectos
3MF, junto con las fotos del modelo y tus notas internas.

- **Piensa en el Diseño como el plano o la idea.** No lleva tiempos ni gramos de
  filamento, porque un mismo STL se puede imprimir a distintas escalas o con
  distintos materiales.

![El diseño «Keyring BolloPrint», con su archivo STL, su foto, sus notas internas y sus dos piezas: de 5 cm y de 10 cm](/blog/media/2026-10-15-organizar-catalogo/02-diseno.png)

### Piezas: el objeto físico

Una **Pieza** es el resultado de coger un Diseño y darle una configuración de
impresión concreta: el material y su consumo (por ejemplo, PLA negro), las medidas
y el tiempo de impresión.

- **Un Diseño, varias Piezas.** Con el mismo STL puedes imprimir una figura en dos
  tamaños, 5 cm y 10 cm: ese Diseño tendrá dos Piezas, «Llavero pequeño» y «Llavero
  grande». Lo mismo vale para colores o materiales distintos.
- **Tu archivo laminado hace las cuentas.** Si subes a la Pieza el archivo del
  laminador (`.gcode`, `.gcode.3mf`, `.bgcode` o `.goo` de resina), BolloPrint lee
  el peso y el tiempo de impresión y te los propone. Al aplicarlos, calcula lo que
  te cuesta fabricar exactamente esa pieza. También puedes escribir o corregir los
  datos a mano.

:::info 💡 Un 3MF de proyecto no sirve aquí
El laminador necesita haber laminado la placa para saber el peso y el tiempo. Un
`.3mf` de proyecto no los lleva: va en el Diseño. A la Pieza súbele el
`.gcode.3mf` que exporta el laminador.
:::

### Productos y Variantes: lo que ve y compra tu cliente

El **Producto** es tu escaparate: lo que publicas en tu tienda o en un marketplace
como Etsy. La **Variante** es la opción concreta que elige el cliente.

- **Una Variante puede tener una o varias Piezas**, cada una con su cantidad.
- **Por ejemplo:** tu Producto es «Figura de Bollo», nuestro perro. Una Variante
  puede ser «Verde», otra «Naranja» y otra el pack «Verde + Naranja», con las dos
  Piezas dentro. Puedes combinar materiales, tamaños, acabados o lotes como
  quieras.

![La variante Green+Orange, con sus dos piezas dentro, una naranja y otra verde, y su coste, su margen y su precio](/blog/media/2026-10-15-organizar-catalogo/04-variante-pack.png)

- **El margen sale solo.** Como cada Variante sabe de qué Piezas está hecha,
  BolloPrint compara tu precio de venta con el coste real de producción y te
  enseña el margen. Si cambias el precio, el margen se actualiza, y al revés.

![La variante Green, con una sola pieza: coste de 7,06 €, margen del 70 % y precio de 23,54 €](/blog/media/2026-10-15-organizar-catalogo/03-variante.png)

## ¿Tienes prisa? Usa la Creación Express

Si estás empezando o tienes cientos de modelos por subir, configurar Diseños, Piezas
y Productos uno a uno lleva su tiempo.

Para eso está la **Creación Express**, el botón **Crear rápido** del catálogo. En una
sola pantalla subes tu archivo 3D, indicas el material, el peso, el tiempo y el
precio, y BolloPrint crea de una vez el Diseño, la Pieza, el Producto y su Variante.
El resultado es el mismo que si lo hicieras paso a paso, así que después puedes
afinar lo que quieras.

![El formulario de Creación Express: el archivo 3D, las fotos, el material, el peso, el tiempo, los colores, el coste y el precio](/blog/media/2026-10-15-organizar-catalogo/05-creacion-express.webp "50%")

## Tus etiquetas pasan solas al producto

Otro detalle que te ahorra trabajo: las **etiquetas** de un Diseño pasan solas a sus
Productos.

Si etiquetas un Diseño como «Llaveros» o «Figuras», cuando añades sus Piezas a una
Variante, esas etiquetas se suman al Producto. Y si vendes en Etsy, al publicar el
anuncio te aparecen ya puestas como *tags*, que ayudan a que te encuentren. Etsy
admite hasta 13, de 20 caracteres como máximo, y puedes retocarlas antes de
publicar.

## Empieza a ordenar tu catálogo

Tener el catálogo bien organizado no es solo cuestión de orden: es la forma de
saber cuánto te cuesta cada pieza, cuánto ganas en cada pedido y poder hacer
crecer tu taller sin perder el control.

Si quieres ver con más detalle cómo configurar tu catálogo o crear variantes
avanzadas, échale un vistazo a la
[documentación del catálogo](/help/catalogo). Y si te preguntas de dónde sale el
coste de cada Pieza, lo contamos en
[qué cuesta de verdad una pieza impresa](/blog/calculate-your-3d-printing-costs).

Descubre [cómo controlar la producción de tu taller con BolloPrint](/features), tu
software para granjas de impresión 3D.

## Documentación relacionada

- [Catálogo](/help/catalogo): los niveles del catálogo, en la referencia
- [Diseños](/help/disenos): los archivos, las fotos y las etiquetas
- [Piezas](/help/piezas): el material, el archivo laminado y el coste
- [Productos y Variantes](/help/productos-y-variantes): el precio, el margen y las piezas de cada variante
- [Creación Express](/help/creacion-express): todo de una vez
- [Etiquetas](/help/etiquetas): cómo se crean y se gestionan
