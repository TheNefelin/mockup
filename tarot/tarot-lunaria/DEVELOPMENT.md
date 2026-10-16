# Esencias Arcanas · Mockup landing de tarot

Mockup de página para un servicio de **lecturas de tarot en línea**. Dirección
de arte **místico nocturno**: cielo estrellado en movimiento, negro índigo y
dorado, serif de display. Proyecto independiente del de Drakar.

> Marca, textos, precios y contacto son **de ejemplo** (mockup sin fines
> comerciales). Reemplazables por los datos reales del cliente.

## Objetivo y contenido

- Presentar el servicio y a la lectora.
- Mostrar 3 tipos de lectura sin agenda compleja.
- Explicar cómo funciona la sesión.
- Ofrecer contenido (diario) para confianza y posicionamiento.
- Convertir en un formulario corto o contacto por WhatsApp/correo.

## Stack y dependencias (CDN)

| Recurso | CDN | Uso |
| --- | --- | --- |
| Tailwind CSS | `https://cdn.tailwindcss.com` | Utilidades de estilos (runtime) |
| Google Fonts | `https://fonts.googleapis.com/css2?family=Cormorant+Garamond:wght@500;600;700&family=Jost:wght@300;400;500;600&display=swap` | Cormorant Garamond (display) + Jost (texto) |
| JS vanilla | script embebido en `index.html` | Formulario demo, año, control del video, reveal con IntersectionObserver |

No se usa DaisyUI: el estilo es propio y liviano.

## Librerías JS usadas y compatibilidad con Angular

1. **Vanilla JS (embebido)** — sin dependencias; IIFE + `addEventListener` +
   `IntersectionObserver`, sin globales que choquen con Angular.
2. **Tailwind CSS (runtime JS)** — solo estilos.

> Nota Angular: en la versión final se reemplaza el runtime de Tailwind por el
> build de PostCSS dentro del CLI. No hay librería JS acoplada a este mockup.

## Recursos remotos (dependencia de internet)

- **Video de fondo:** Pexels video `28870775` (versión 1280x720, ~varios MB).
- **Poster del video:** Pexels foto `2890467` (cielo estrellado).
- **Presentación:** Pexels foto `31584091`.
- **Diario (3):** Pexels fotos `36789977`, `30160855`, `3088369`.

Todo se sirve desde `images.pexels.com` y `videos.pexels.com`. En producción se
recomienda **descargar y versionar** los recursos para no depender de terceros y
optimizar peso/encoding.

## Comparación de los dos proyectos de este espacio

| | Drakar (`drakar/drakar-cinematic`) | Tarot (`tarot/tarot-lunaria/`) |
| --- | --- | --- |
| Tema | transporte y mudanzas | lecturas de tarot |
| Fondo | imagen de puerto nocturno | video de cielo estrellado |
| Paleta | noche + ámbar | índigo-negro + dorado |
| Tipografía | Cinzel + Manrope | Cormorant Garamond + Jost |
| Recurso clave | hero fotográfico | video decorativo con fallback |

## Secciones del mockup

1. **Nav** fija → Lecturas · Cómo funciona · Diario · Reservar.
2. **Hero** con video de fondo, titular y 2 CTA.
3. **Presentación** — quién lee las cartas + imagen.
4. **Lecturas** — 3 tiradas (carta del día, tres, cruz completa).
5. **Proceso** — 4 pasos, de la reserva a la síntesis escrita.
6. **Diario** — 3 artículos con imagen.
7. **Contacto** — formulario de reserva + WhatsApp/correo/horario.
8. **Footer**.

## Accesibilidad, video y movimiento

- El video es **decorativo y silenciado** (`autoplay muted loop playsinline`), con
  `poster` y una imagen base detrás como respaldo si el video no carga.
- `prefers-reduced-motion`: pausa y oculta el video (queda la imagen base), y
  desactiva el fade, el reveal y el scroll suave.
- El reveal no oculta contenido si JavaScript está desactivado (clase `.js`).
- Formulario y enlaces con foco visible y contraste suficiente sobre el fondo oscuro.

## Cómo abrir

Abrir `index.html` directamente en el navegador (necesita internet para CDN,
imágenes y video). No requiere build ni servidor.

## Limitaciones conocidas

- No se inspeccionó en navegador real desde el entorno de generación; se verificó
  estructura, enlaces y contraste de forma estática.
- El video pesa varios MB; para producción conviene recomprimir o servir una
  versión más liviana (o reemplazarlo por la imagen fija).
- Precios, marca y datos de contacto son ficticios (mockup).
