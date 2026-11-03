---
slug: whats-new-september-november-2026
title: "¡BolloPrint se actualiza! Las novedades que te ayudan con tu taller de impresión 3D"
description: "Todo lo nuevo en BolloPrint del 14 de septiembre al 3 de noviembre de 2026: desde el agente local sin contenedores a las facturas legales y el Financiero nuevo."
date: 2026-11-03
tags: [novedades]
cover: 01-bollo.webp
---

Desde mediados de septiembre hemos publicado **41 actualizaciones** de BolloPrint.
Algunas son grandes e importantes cambios. Otras son pequeñas mejoras que hacen tu
día a día más cómodo. Aquí tienes lo más importante.

![En siete semanas: más de 400 mejoras que se notan, más de 250 cambios en pantalla, unos 190 fallos arreglados, 11 países con facturas legales, 9 idiomas en la app y 102 impresoras de 15 marcas](/blog/media/2026-11-03-novedades-otono/02-cifras-es.webp)

## Empezamos por lo más interesante, lo que mejora cómo trabajas

### 1. El agente local, ahora sin saber de contenedores

Sabemos que usar Docker puede ser complicado. Así que ahora es más fácil. Instala
el agente en lo que ya tienes: tu NAS, el ordenador del taller o tu Home Assistant.

![Los logos de Synology, QNAP, Windows, Home Assistant y TrueNAS](/blog/media/2026-11-03-novedades-otono/03-agentes.webp)

| Dónde | Cómo se instala |
|---|---|
| **Synology y QNAP** | Descarga el paquete de tu NAS e instálalo a mano desde su centro de paquetes. |
| **Windows** | Un instalador para el ordenador del taller. |
| **Home Assistant** | El botón «Añadir a Home Assistant» y listo. |
| **TrueNAS** | Pegas la configuración que te damos en sus apps. |

Luego abres su página y pulsas **«Vincular con BolloPrint»**: el dueño del taller
lo confirma con un clic, sin copiar códigos. Como todos los agentes, se actualiza
solo. Docker y Kubernetes siguen funcionando como siempre.

:::info
Lo encuentras en **Configuración → Impresoras → Agente local → «Nuevo agente»**.
[Cómo instalar el agente](/help/el-agente-local)
:::

---

### 2. Tus impresoras, mejor vistas y mejor contadas

- **Cámara en directo** y una foto final de cada impresión en su historial.
- **Cada impresión lo cuenta todo**: cuánto tardó frente a lo previsto, cada bobina con su hueco del AMS, y el nombre del diseño de MakerWorld con su enlace.
- **Lo gastado, de verdad**: una impresión fallida o cancelada ya no se cuenta entera, y las de resina apuntan sus mililitros.
- **Bambu Lab**, por la nube sin contraseña (tu email y un código, y la sesión se renueva sola) y por red local con pausar, reanudar y cancelar desde BolloPrint, con el Modo desarrollador activado.
- **Añadir por IP** es ahora un asistente por marca; ya no hace falta saber qué «protocolo» habla tu máquina.
- **El agente local se actualiza solo**, nunca a mitad de una impresión, y cada marca de impresora mejora por su cuenta.
- **Anycubic** (Kobra 3, S1, 4 y X) y **Creality** con su firmware de fábrica (K1, K2, Ender-3 V3 y Hi) se suman, en beta.

[Ver las impresoras compatibles](/help/impresoras-compatibles)

---

### 3. Migración Smart

Trae clientes, diseños, piezas, productos, pedidos, presupuestos y stock, desde las
carpetas y hojas de cálculo de tu ordenador. BolloPrint lee lo que traes y te
propone cómo encaja; tú lo revisas antes de que entre nada, y si te equivocas, se
deshace.

:::warning
Son tres pasos: **Preparar · Entender · Migrar**. Desde el plan Pro, en Chrome o
Edge de escritorio. En Max y Business, si prefieres, lo hacemos nosotros por ti.
:::

---

### 4. Facturas legales desde el pedido

Emite la factura de un pedido sin salir de BolloPrint: con su numeración, su
impuesto y tu logo. Antes de emitir ves la factura **exactamente como saldrá**, y
si algo falta te decimos qué y dónde corregirlo.

- **Cobros**: pendiente, vencida o pagada, y un ZIP con todas tus facturas.
- **Ventas sin IVA a empresas de la UE**, con la mención legal puesta y el número
  comprobado en VIES.
- **Factura electrónica alemana, QR-bill suiza** y facturas en otra moneda.

Ya disponible en 11 países: Alemania, Austria, Chequia, Chipre, Irlanda,
Luxemburgo, Países Bajos, Polonia (por KSeF), Reino Unido, Suecia y Suiza.

:::warning
**En España todavía no**: llegará cuando tengamos integrado VeriFactu, y te lo
contaremos.
:::

[Ver los países con facturación](/help/paises-con-facturacion)

---

### 5. Presupuestos más profesionales

- El PDF del presupuesto tiene **forma de factura**: número, fecha, validez y, en
  los planes de pago, con tu propio logo.
- **Numeración por año** («2026-00001») y sin huecos, aunque borres uno.
- **Descuento** en € o en %, que sale como una línea más.
- Fichas de cliente **Particular o Empresa**, y unos datos fiscales más sencillos.
- Creación automática de un **pedido al aceptar** el presupuesto.

[Ver los presupuestos](/help/presupuestos)

---

### 6. Un Financiero totalmente nuevo

Seis pestañas donde ver tus ingresos, tus gastos, tus impuestos y tu beneficio en
el periodo que quieras (mensual, trimestral, anual…).

Sube tus gastos con nuestro agente de IA y archiva las facturas de tus proveedores
para ver en qué gastas tu dinero de un vistazo. Controla los impuestos que tienes
que pagar en cada periodo.

:::info
**Lo mejor:** exporta estos datos para tu gestoría en un ZIP con solo un clic.
:::

[Ver el Financiero](/help/financiero)

---

### 7. «Avisos»: los problemas de tu taller, de un vistazo

Una impresora parada con un error, una tienda de Etsy desconectada, un cobro que no
ha pasado, el almacenamiento casi lleno… Solo te avisamos de lo que de verdad pide
algo, y cada aviso se cierra solo cuando lo arreglas.

Puedes silenciar un aviso unos días o para siempre. Los rojos, los que paran algo
importante, solo se los mostramos en rojo a quien puede arreglarlo; el resto del
equipo los ve con un «Avísale al dueño».

---

### 8. Exporta tu inventario, en Excel o en PDF

Ahora puedes sacar un listado de lo que tienes en tu almacén: stock, filamentos,
resinas, suministros…

| Formato | Qué te llevas |
|---|---|
| **Excel** | Un libro con un resumen y una hoja por sección, con filtros, totales y lo que se ha quedado sin stock en rojo. |
| **PDF** | Un documento por sección, con tu logo, las fotos de tus piezas y los colores de cada bobina. |

En todos los planes, y siempre con todas las filas, no solo las que tienes en
pantalla.

---

### 9. En tu idioma y a tu manera

BolloPrint ya habla **🇵🇱 polaco, 🇳🇱 neerlandés y 🇨🇿 checo**. Con estos, sumamos nueve
idiomas en total.

Las fechas y los importes se escriben **como en el país de tu taller**, en
pantalla, en el PDF y en los correos.

Y hay un **Inicio nuevo** que empieza por lo urgente, con «Crear nuevo» para un
pedido, un presupuesto o una creación rápida, y «Primeros pasos» con su barra de
progreso.

## Y además, porque los pequeños cambios también se notan

| Dónde | Qué cambia |
|---|---|
| **Pantallas** | Mientras algo carga ves su forma, nunca una lista vacía falsa; si falla, un «Reintentar». Los filtros son iguales en todos los listados, también en el móvil. |
| **Subidas** | Cada archivo enseña su progreso y se reintenta solo tras un corte de red. Los ficheros laminados pueden pesar hasta 5 GB. |
| **Costes** | 29 familias de filamento y 9 de resina, con precios por kilo actualizados; los márgenes, con una barra de colores y un ejemplo. |
| **Clientes** | El listado busca y ordena por cualquier columna, y un cliente sin alias se ve por su nombre completo. |
| **Etsy** | Importar un anuncio es hasta 8 veces más rápido, entran los pedidos con dos variaciones y, antes de sincronizar un anuncio, ves valor por valor lo que va a cambiar. Configuración → Marketplaces es ahora una galería, con una página por tienda. |
| **Envíos** | Transportistas y canales de venta propios para Austria, Alemania, Reino Unido, Polonia, Chequia y Países Bajos. |
| **Manual y blog** | El manual pasa de 49 a 70 páginas, en los nueve idiomas, y en el blog hay seis artículos nuevos: del agente local a qué cuesta de verdad una pieza. |
| **El día a día** | La app aguanta mejor los picos, vuelve sola tras un corte de red, el traductor de Chrome ya no la rompe y una impresora cuyo agente se apaga a mitad ya no deja impresiones fantasma. |

## Dónde estamos

| Qué | Dónde y cuánto |
|---|---|
| 🧾 **Facturas legales en 11 países** | 🇩🇪 Alemania · 🇦🇹 Austria · 🇨🇿 Chequia · 🇨🇾 Chipre · 🇮🇪 Irlanda · 🇱🇺 Luxemburgo · 🇳🇱 Países Bajos · 🇵🇱 Polonia · 🇬🇧 Reino Unido · 🇸🇪 Suecia · 🇨🇭 Suiza |
| 🌍 **Un taller se abre desde 53 países de Europa** | Con su moneda, sus impuestos y sus transportistas. Se paga en euros, libras, złotys o coronas checas. |
| 🖨️ **102 modelos de impresora, de filamento y de resina** | Bambu Lab · Prusa · Elegoo · FlashForge · Anycubic · Creality · QIDI · Snapmaker · Voron · RatRig · Sovol · Artillery · Longer · Phrozen · Two Trees |
| ✅ **10 comprobados por nosotros en máquina real** | Bambu Lab A1, A2L, P1P, P1S, P2S, X1 Carbon, X2D, H2C, H2D y H2S. |

## ¿Echas algo en falta?

Cuéntanoslo en
[info@bolloprint.com](mailto:info@bolloprint.com) o en nuestro
[canal de Discord](/help/soporte-por-discord). Lo leemos todo. Mucho de lo que ves
aquí salió de mensajes como el tuyo.

Si quieres más detalles de cómo funciona, lo tienes todo en el [manual](/help).

Y no paramos, seguimos trabajando cada día para hacer de BolloPrint la mejor
herramienta para tu taller de impresión 3D.

![Bollo, la mascota de BolloPrint, con gafas de taller y su cinturón de herramientas, sobre un plano](/blog/media/2026-11-03-novedades-otono/01-bollo.webp "60%")
