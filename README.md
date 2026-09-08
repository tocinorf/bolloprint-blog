# bolloprint-blog

Contenido del blog de [bolloprint.com/blog](https://bolloprint.com/blog).

**Publicar es hacer commit aquí.** No hay que desplegar la web: se entera sola en
unos minutos. Si tienes prisa, en el Admin (*Blog → Forzar reescaneo*) lo aplicas
al momento.

## Escribir un artículo

Una carpeta por artículo, un fichero por idioma:

```
posts/2026-09-15-mi-articulo/
├── es.md      ← el original (obligatorio)
├── en.md      ← muy recomendable
└── fr.md      de.md  it.md  pt.md   (opcionales)
```

El nombre de la carpeta es solo un identificador interno: **no** aparece en la
URL. Lo que sale en la URL es el `slug`, y es distinto en cada idioma a
propósito, porque la palabra clave dentro de la dirección ayuda a posicionar.

Cada fichero empieza con su cabecera:

```markdown
---
slug: organizar-pedidos-granja-impresion-3d
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
| `slug` | sí | Lo que va en la URL. Minúsculas, números y guiones. **Distinto por idioma.** |
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
  web descarta uno y lo avisa en el Admin.
- **Un artículo sin versión en inglés** solo existirá en los idiomas que tenga.
  Es válido, pero pierdes la dirección sin prefijo.
- Si publicas y no aparece, míralo en el Admin (*Blog*): los artículos
  descartados salen ahí con el motivo.

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

**Las imágenes son las mismas en todos los idiomas** — hay una sola carpeta
`assets/` por artículo, no una por idioma. Las capturas de producto se hacen una
vez, con la interfaz en inglés, y valen para las seis versiones. Lo que sí
cambia por idioma es el texto alternativo, que va en el `![...]`.

| Regla | Por qué |
|---|---|
| Formatos: `png`, `jpg`, `jpeg`, `webp`, `avif`, `gif` | SVG no, porque es XML ejecutable y esto es un repo abierto |
| Nombre en minúsculas, sin espacios ni carpetas dentro de `assets/` | Acaba en una URL, y macOS y Linux no tratan igual las mayúsculas |
| Máximo **3 MB** por imagen | El blog entero vive en memoria del proceso de la web |
| Numéralas (`01-`, `02-`…) | Salen ordenadas en la carpeta, que es como se revisan |

Una imagen que incumpla algo de esto **no se publica**, y el motivo aparece en el
Admin (*Blog*) junto a los artículos descartados.
