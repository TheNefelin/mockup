# Desarrollo

> Memoria del proyecto. Aquí viven las decisiones y el estado. Mantener al día.

## Arquitectura

Colección de **mockups HTML estáticos** (sin build). Cada mockup vive en su
propia carpeta con un `index.html` y, cuando aplica, un `DEVELOPMENT.md`. Tres
familias:

- `drakar/` — transporte y mudanzas (5 variantes).
- `tarot/` — lecturas de tarot, marca **Esencias Arcanas** (2 variantes).
- `console/` — demo de terminal DOS.

La raíz contiene el sitio publicado: `index.html` (índice), `404.html`,
`robots.txt` y `.nojekyll`. La carpeta `harness/` son las reglas y skills de
openCode; no forman parte del sitio.

## Publicación

El sitio se sirve con **GitHub Pages** usando **GitHub Actions** (OIDC), no una
rama de despliegue. El workflow `.github/workflows/pages.yml` se dispara con cada
push a `main` y con `workflow_dispatch`; tiene dos jobs: `build` (checkout →
`configure-pages` → `upload-pages-artifact`) y `deploy` (`deploy-pages`, con
`needs: build`). Requiere habilitarlo una vez en *Settings → Pages → Source:
GitHub Actions*.

Los jobs están separados a propósito: subir el artefacto y desplegarlo en el
mismo job provoca una condición de carrera conocida (`deploy-pages` lista los
artefactos antes de que la subida esté visible) que falla de forma intermitente
con *"No artifacts named github-pages were found"*. Con `needs: build` el
artefacto ya está finalizado cuando `deploy-pages` lo busca.

`.nojekyll` ya no es relevante en este flujo: con Pages vía Actions no se ejecuta
Jekyll y `upload-pages-artifact` omite los archivos ocultos por defecto. Se
conserva por compatibilidad con `robots.txt`/enlaces, no por necesidad.

## Decisiones técnicas

| Fecha | Decisión | Motivo | Alternativas descartadas |
|---|---|---|---|
| 2026-10-16 | Publicar con Pages desde la raíz (`main` /) | Las variantes ya viven en la raíz; conserva los enlaces relativos | `/docs` (rompe rutas o exige mover contenido); rama `gh-pages` (requiere copia/despliegue aparte) |
| 2026-10-16 | Marca del proyecto de tarot: **Esencias Arcanas** (antes «Lunaria»), usada como servicio sin nombre de persona | Unificar la marca y corregir la ortografía | Mantener «Lunaria» |
| 2026-10-16 | El `README.md` raíz funciona como índice de la colección | Era la plantilla del Harness, sin personalizar | — |

## Estado

- [x] Harness local (reglas + skill `ui-ux-mockup`)
- [x] Cinco variantes DRAKAR
- [x] Dos variantes de tarot (Esencias Arcanas)
- [x] Demo de consola DOS
- [x] Índice raíz + `404.html` + `robots.txt` + `.nojekyll`
- [x] `README.md` como índice de la colección

## Pendientes

- Ninguno por ahora. La publicación inicial en GitHub la ejecuta la persona a
  cargo del repositorio; no es una tarea de este proyecto.

## Problemas conocidos

- Los activos de los mockups (imágenes/video y fuentes) se cargan desde CDN
  (Pexels, Google Fonts, Tailwind): requieren internet.
- El Harness siembra `README.md`, `DEVELOPMENT.md` y `SKILL.md`; un
  `install.ps1 -Update` podría sobrescribirlos. Verificar antes del próximo refresh.

## Deuda técnica

- Las carpetas conservan nombres heredados (`tarot-lunaria`) aunque la marca
  cambió a «Esencias Arcanas».
- Varios mockups usan cifras y datos de contacto de ejemplo (mockup).
