# Mockups

Colección de **mockups HTML estáticos** (sin build ni dependencias de servidor).
Cada carpeta es un mockup independiente que se abre directamente en el navegador.

> **Mockup demostrativo.** Marcas, textos, precios y contactos son de ejemplo.
> Los activos (imágenes/video y fuentes) se cargan desde sus CDN, así que requieren internet.

## Sitio publicado

https://`<usuario>`.github.io/`<repo>`/

> Reemplaza `<usuario>` y `<repo>` por los reales una vez publicado en GitHub Pages
> (y quita el backtick). Si aún no está publicado, elimina esta sección.

## Mockups

### DRAKAR — Transporte y mudanzas

| Mockup | Carpeta | Dirección de arte |
| --- | --- | --- |
| Drakar Cinematic | [`drakar/drakar-cinematic/`](drakar/drakar-cinematic/) | Hero fotográfico de puerto nocturno; oscuro + ámbar |
| Drakar Landing | [`drakar/drakar-landing/`](drakar/drakar-landing/) | Landing de conversión mínima (3 campos); identidad noche/ámbar |
| Drakar Logística | [`drakar/drakar-logistica/`](drakar/drakar-logistica/) | Clara y terrestre, sin metáfora marítima |
| Drakar Nocturno | [`drakar/drakar-nocturno/`](drakar/drakar-nocturno/) | Hero con **video** (ruta nocturna); noche + ámbar |
| Drakar Claro | [`drakar/drakar-claro/`](drakar/drakar-claro/) | Luminosa de señalética/obra; papel cálido + naranja de señal |

### Esencias Arcanas — Tarot en línea

| Mockup | Carpeta | Dirección de arte |
| --- | --- | --- |
| Esencias Arcanas | [`tarot/tarot-lunaria/`](tarot/tarot-lunaria/) | Hero cósmico: cielo estrellado, índigo-negro + dorado |
| Esencias Arcanas Ritual | [`tarot/tarot-ritual/`](tarot/tarot-ritual/) | Mesa de velas, baraja y humo; carbón + cobre + verde botella |

### Varios

| Mockup | Carpeta | Descripción |
| --- | --- | --- |
| Consola DOS | [`console/`](console/) | Terminal estilo DOS con efecto máquina de escribir |

## Vista previa local

Abre `index.html` (en la raíz o en cualquier carpeta) con el navegador. Para servirlo
como lo haría Pages:

```bash
python -m http.server 8000
# luego visita http://localhost:8000/
```

## Publicación (GitHub Pages)

El sitio se publica **desde la raíz del repositorio** (rama `main`, carpeta `/`).

- Se habilita una sola vez en GitHub: **Settings → Pages → Source: Deploy from a branch
  → `main` / `root` (/)**.
- Desde ahí **el despliegue es automático**: cada `git push` a `main` reconstruye y
  republica el sitio. No hace falta escribir un workflow de GitHub Actions.
- **`.nojekyll`** desactiva el procesamiento de Jekyll para que los archivos se sirvan
  tal cual.
- **`robots.txt`** (`Disallow: /`) mantiene los mockups fuera de los buscadores.

Para desplegar el sitio en el futuro (una vez configurado):

```bash
git add .
git commit -m "Actualiza mockups"
git push
```

## Estructura

```
mockup/
├─ index.html            # índice publicado (lista los mockups)
├─ 404.html              # página de error propia
├─ robots.txt            # bloquea indexación
├─ .nojekyll             # desactiva Jekyll en Pages
├─ drakar/
│  ├─ drakar-cinematic/
│  ├─ drakar-landing/
│  ├─ drakar-logistica/
│  ├─ drakar-nocturno/
│  └─ drakar-claro/
├─ tarot/
│  ├─ tarot-lunaria/
│  └─ tarot-ritual/
├─ console/
└─ harness/              # reglas y skills de openCode
```

Cada carpeta de mockup contiene su `index.html` y, cuando aplica, un
`DEVELOPMENT.md` con las decisiones de diseño de esa variante.
