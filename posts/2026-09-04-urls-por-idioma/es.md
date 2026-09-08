---
slug: novedades-v0-14-una-url-por-idioma
title: "Novedades v0.14: cada idioma tiene ya su propia dirección"
description: BolloPrint.com hablaba seis idiomas pero Google solo veía uno. Lo hemos arreglado, y de paso hemos desbloqueado 174 páginas del manual.
version: v0.14
date: 2026-09-04
updated: 2026-09-04
tags: [novedades]
draft: false
---

Hasta esta versión, `bolloprint.com/pricing` mostraba los seis idiomas en **la
misma dirección**: el servidor miraba el idioma de tu navegador y te servía el
tuyo. Para una persona funcionaba bien. Para un buscador, no.

Google rastrea sin idioma preferido, así que siempre recibía la versión inglesa
y era la única que indexaba. Las otras cinco no es que posicionaran mal: **no
existían** para el buscador, porque no tenían una URL a la que apuntar.

## Qué cambia

Cada idioma estrena dirección propia. El inglés se queda donde estaba —así
ninguna URL existente cambia— y los otros cinco llevan el idioma en la ruta:

- `bolloprint.com/pricing` — inglés
- `bolloprint.com/es/pricing` — español
- `bolloprint.com/fr/pricing` — francés

Y así con los seis. Entre ellas se declaran como traducciones, de forma que no
compiten entre sí: el buscador entiende que son la misma página en otro idioma y
le enseña a cada usuario la suya.

:::info
Si compartes un enlace, ahora llega en el idioma en el que tú lo viste. Antes
cada persona lo abría en el suyo, que no siempre era el que tú querías enseñar.
:::

## Lo que más se nota

El manual de usuario son 29 documentos traducidos a seis idiomas — **174
páginas** — que hasta ahora se indexaban como 29, en inglés. Ese contenido ya
estaba escrito y traducido; solo le faltaba una dirección donde vivir.

## Y algo que no cambia

Las páginas de acceso y de cuenta siguen exactamente igual, detectando tu idioma
como siempre. No se indexan, así que no necesitaban dirección propia: menos
superficie tocada, menos que pueda romperse.
