# bolloprint-blog

Contenido del blog de [bolloprint.com/blog](https://bolloprint.com/blog).

**Publicar es hacer commit aquí.** No hay que desplegar la web: cada máquina de la
web revisa este repo **cada 15 minutos** por su cuenta, así que un artículo o una
imagen aparece como mucho 15 minutos después del push. No hay botón para
acelerarlo: el Admin no tiene sección de blog.

## Escribir un artículo

Una carpeta por artículo, un fichero por idioma:

```
posts/2026-09-15-mi-articulo/
├── es.md      ← el original (obligatorio)
├── en.md      ← muy recomendable
└── fr.md  de.md  it.md  pt.md  pl.md   (opcionales)
```

El nombre de la carpeta es solo un identificador interno: **no** aparece en la
URL. Lo que sale en la URL es el `slug`, y es **el mismo en los siete idiomas, en
inglés**: lo único que cambia entre versiones es el prefijo de idioma.

```
/blog/order-management-3d-print-farm          ← inglés, sin prefijo
/es/blog/order-management-3d-print-farm
/fr/blog/order-management-3d-print-farm
/pl/blog/order-management-3d-print-farm
```

Así cada artículo se reconoce por su dirección en cualquier idioma y es fácil
llevar el orden.

Cada fichero empieza con su cabecera:

```markdown
---
slug: order-management-3d-print-farm
title: Cómo organizar los pedidos de una granja de impresión 3D
description: Una o dos frases. Es lo que se ve en Google y en la portada del blog.
date: 2026-08-20
updated: 2026-08-20
tags: [tutoriales]
draft: false
---

Aquí el artículo, en markdown normal.
```

| Campo | Obligatorio | Qué es |
|---|---|---|
| `slug` | sí | Lo que va en la URL. Minúsculas, números y guiones, en inglés. **El mismo en todos los idiomas.** |
| `title` | sí | Título del artículo |
| `description` | sí | Resumen de una o dos frases |
| `date` | sí | Fecha de publicación (`AAAA-MM-DD`) |
| `updated` | no | Última revisión |
| `tags` | no | Etiquetas para el filtro de la portada |
| `version` | no | Solo en notas de versión (`v0.14`). Pinta el distintivo de versión en el artículo |
| `cover` | no | Imagen de portada, ruta dentro de `assets/` |
| `draft` | no | `true` = no se publica |

## Reglas que evitan sustos

- **El `slug` no se cambia** una vez publicado. Si cambia, quien tuviera el
  enlace deja de llegar y se pierde el posicionamiento del artículo.
- **Dos artículos no pueden compartir `slug` en el mismo idioma.** Si pasa, la
  web descarta uno y lo avisa en Sentry.
- **Un artículo sin versión en inglés** solo existirá en los idiomas que tenga.
  Es válido, pero pierdes la dirección sin prefijo.
- Si publicas y a los 15 minutos no aparece, míralo en **Sentry** (proyecto de la
  web): cada artículo descartado llega como aviso `Blog: artículo descartado —
  <ruta>` con el motivo, y si la web no pudo descargar el repo, como `Blog: no se
  pudo actualizar`. Ojo: un `draft: true` olvidado **no** avisa (un borrador no es
  un error), así que revisa eso primero.

## Formato

Markdown normal (GFM: tablas, listas de tareas, código). Además hay avisos:

```markdown
:::info
Para un apunte al margen.
:::

:::warning
Para algo que conviene no pasar por alto.
:::
```

## Imágenes

Van **dentro de la carpeta del artículo**, en `assets/`, y se publican con él en
el mismo commit. No hay que desplegar la web para añadir o corregir una captura.

```
posts/2026-09-15-mi-articulo/
├── es.md
├── en.md
└── assets/
    ├── 01-pantalla-inicial.png
    └── 02-formulario.png
```

Se enlazan con **ruta absoluta**, usando el nombre de la carpeta del artículo:

```markdown
![Lo que se ve en la captura](/blog/media/2026-09-15-mi-articulo/01-pantalla-inicial.png)
```

**Hay una sola carpeta `assets/` por artículo**, no una por idioma. Las
ilustraciones sin texto valen para todas las versiones; las capturas de producto
se hacen una por idioma y llevan el código al final del nombre
(`02-formulario-es.png`, `02-formulario-en.png`…). Los idiomas permitidos son
`es`, `en`, `fr`, `de`, `it`, `pt` y `pl`. Si un idioma no tiene aún su captura
(el polaco, de momento), su `.md` enlaza la `-en`. El texto alternativo, que va
en el `![...]`, se traduce siempre.

| Regla | Por qué |
|---|---|
| Formatos: `png`, `jpg`, `jpeg`, `webp`, `avif`, `gif` | SVG no, porque es XML ejecutable y esto es un repo abierto |
| Nombre en minúsculas, sin espacios ni carpetas dentro de `assets/` | Acaba en una URL, y macOS y Linux no tratan igual las mayúsculas |
| Máximo **3 MB** por imagen | El blog entero vive en memoria del proceso de la web |
| Numéralas (`01-`, `02-`…) | Salen ordenadas en la carpeta, que es como se revisan |

Una imagen que incumpla algo de esto **no se publica**, y el motivo llega a Sentry
igual que el de los artículos descartados.
