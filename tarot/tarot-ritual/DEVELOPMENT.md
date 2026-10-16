# Esencias Arcanas Ritual · Mockup variante de tarot

Variante **Ritual** del mockup de tarot: misma propuesta de negocio que
`../tarot-lunaria/index.html` (lecturas de tarot en línea de la marca **Esencias Arcanas**) con una
dirección de arte distinta. Donde la versión original explora lo **cósmico**
(video de cielo estrellado, índigo-negro + dorado), esta variante lleva el
misticismo a la **mesa de trabajo**: velas, tela, baraja y humo.

## Diferencia de dirección de arte

| | tarot (Esencias Arcanas) | tarot-ritual |
| --- | --- | --- |
| Concepto | cosmos / noche estrellada | mesa / ritual de velas |
| Fondo del hero | video de cielo estrellado | imagen fija de baraja + vela con brillo CSS |
| Paleta | índigo-negro + dorado | carbón cálido + cobre/latón + verde botella |
| Tipografía | Cormorant Garamond + Jost | Fraunces + Nunito Sans |
| Composición del hero | centrado | asimétrico, texto a la izquierda + panel de imagen |
| Tarjetas de lecturas | cards planas | cartas de tarot con marco interior y numeral romano |
| Ornamentos | glifos celestes (☾ ✦ ✶) | glifos alquímicos/planetarios (⚶ ☉ ☽ ☿ ♀) |
| Retratos | rectangulares | marco en arco (hornacina) |

Se conserva: la marca, los textos, las tiradas y precios, el stack y el objetivo
de conversión.

## Stack y dependencias (CDN)

| Recurso | CDN | Uso |
| --- | --- | --- |
| Tailwind CSS | `https://cdn.tailwindcss.com` | Utilidades de estilos (runtime) |
| Google Fonts | `https://fonts.googleapis.com/css2?family=Fraunces:...&family=Nunito+Sans:...` | Fraunces (display) + Nunito Sans (texto) |
| JS vanilla | script embebido en `index.html` | Formulario demo, año, reveal con IntersectionObserver |

No se usa DaisyUI: el estilo es propio y liviano.

## Librerías JS usadas y compatibilidad con Angular

1. **Vanilla JS (embebido)** — sin dependencias; IIFE + `addEventListener` +
   `IntersectionObserver`, sin globales que choquen con Angular.
2. **Tailwind CSS (runtime JS)** — solo estilos.

> Nota Angular: en la versión final se reemplaza el runtime de Tailwind por el
> build de PostCSS dentro del CLI. No hay librería JS acoplada a este mockup.

## Movimiento y medios

- **Sin video.** El hero usa una **imagen fija** con un **brillo cálido de vela
  animado por CSS** (`.candle-glow::after`, `@keyframes flicker`). Se descartó el
  video de fondo: los clips de vela candidatos en Pexels son verticales (mal
  encuadre para un hero horizontal) y su URL de archivo no se pudo verificar de
  forma fiable. La imagen + CSS es más liviana y no depende de un video frágil.
- `prefers-reduced-motion`: desactiva el fade del hero, el parpadeo del brillo y
  el reveal, y el scroll suave.
- El reveal no oculta contenido si JavaScript está desactivado (clase `.js`).

## Recursos remotos (dependencia de internet)

Todas las URLs se verificaron con respuesta **200** antes de incrustarlas.

| Uso | Pexels |
| --- | --- |
| Hero | foto `16596421` (cartas de tarot y vela sobre la mesa) |
| Presentación (arco) | foto `6014324` (manos acomodando cartas sobre la mesa) |
| Proceso (banda de fondo) | foto `31584091` (carta de tarot con velas y cristales) |
| Diario (3) | fotos `36789977`, `30160855`, `3088369` |

Servidas desde `images.pexels.com`. En producción se recomienda **descargar y
versionar** los recursos para no depender de terceros y optimizar peso/encoding.

## Secciones del mockup

1. **Nav** fija → Lecturas · Cómo funciona · Diario · Reservar.
2. **Hero** asimétrico — titular, propuesta, 2 CTA, línea de confianza y panel de
   imagen con brillo de vela.
3. **Credo** — franja delgada con glifos planetarios y tres promesas.
4. **Quién lee las cartas** — retrato en arco + texto.
5. **Lecturas** — 3 cartas de tarot (carta del día, tres, cruz completa).
6. **Proceso** — banda a sangre con 4 pasos en numerales romanos.
7. **Diario** — 3 artículos con imagen.
8. **Contacto** — formulario de reserva + WhatsApp/correo/horario.
9. **Footer**.

## Accesibilidad

- Enlace "Saltar al contenido", `label` en todos los campos y foco visible
  (`focus-visible:ring`) en botones y enlaces.
- Imagen del hero con `alt` descriptivo; imagen de fondo del proceso decorativa
  (`alt=""`, `aria-hidden`).
- Glifos decorativos con `aria-hidden="true"`.
- `prefers-reduced-motion` respetado (ver arriba).

## Cómo abrir

Abrir `index.html` directamente en el navegador (necesita internet para CDN e
imágenes). No requiere build ni servidor.

## Limitaciones conocidas

- No se inspeccionó en navegador real desde el entorno de generación; se verificó
  estructura, enlaces y contraste de forma estática, y que las URLs de fuentes e
  imágenes devuelvan 200.
- El brillo de vela es una animación CSS, no video real.
- Precios, marca y datos de contacto son ficticios (mockup).
