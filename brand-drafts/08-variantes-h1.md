# 08 · Variantes de H1 (H1-a … H1-f)

**Encargo (Paco, vía coordinador, 26-11-2026).** Ha elegido H1 · "Fingerprint + Receipts" (auras generativas de G + sello "✓ fecha · fuente" de A, ver [05](05-direcciones-ronda-2.md)) y quiere ver variantes de color y de forma antes de fijarla. Aquí hay seis, que cambian a la vez **paleta**, **forma del aura** y **forma del sello**.

**Fijo en las seis** (decisiones ya cerradas o comunes): tagline "We read the docs. You ship the code."; tema claro por defecto, respetando el del sistema; sin mascota; tipografía Roboto Flex + DM Mono (SIL OFL 1.1, como H1; solo cambian los ejes del titular por variante); el sistema semántico común de [03](03-direcciones.md) (✓ / ✕ / ? con borde discontinuo, frescura, modalidades siempre con nombre). La codificación del aura es la misma en todas, con distinta forma: **matiz = modalidad**, **forma cerrada = free tier continuo / abierta = trial**, **marca discontinua = alguna flag "not stated"**, **desaturada = verificada hace más de 30 días**. La parte "única" de cada aura (ángulos, largos, contornos) sale de una semilla calculada del `slug`, así que es estable entre builds.

**Datos.** `data/providers.json` de `origin/main` (5903832, 25-11-2026): v2.14.2, 73 proveedores. "Flags sin decir" = cuántos de `card_required`, `phone_required`, `commercial_ok` y `data_policy.trains_on_prompts` son `null`. Edad = días desde `last_verified` hasta el 26-11-2026. La ficha de ejemplo es Groq (cifras de `free_limits`, cita de `data_policy`, 7 fuentes distintas entre `docs_url`, `free_limits`, `data_policy` y `field_checks`).

**Contraste.** Fórmula de luminancia relativa de WCAG 2.x (la de `build.test.mjs`). Texto ≥ 4.5 sobre fondo **y** panel; bordes de control y matices gráficos ≥ 3 (WCAG 1.4.11). En dos variantes (Pastel y Señalética) algunos matices no llegan a 3:1 en claro a propósito: el aura lleva un **contorno de tinta** que sí lo cumple, y la modalidad siempre va además en texto. Las cifras de esta página las calcula el script que genera los prototipos, no están estimadas.

## Enlaces

| | Prototipo (Artifact privado) | Fichero local |
|---|---|---|
| **Comparación y feedback "H1 variants"** | [claude.ai/artifact/Bf62Bw7xBCozxodeN72BFn](https://claude.ai/artifact/Bf62Bw7xBCozxodeN72BFn) | [galeria/h1-variants.html](galeria/h1-variants.html) |
| H1-a · Mineral | [claude.ai/artifact/Ecnkb21egeuEA7Kn8kEFwr](https://claude.ai/artifact/Ecnkb21egeuEA7Kn8kEFwr) | [prototipos/h1-a-mineral.html](prototipos/h1-a-mineral.html) |
| H1-b · Neon Night | [claude.ai/artifact/VJcwqgwYuQSuZaxCTQBVK4](https://claude.ai/artifact/VJcwqgwYuQSuZaxCTQBVK4) | [prototipos/h1-b-neon.html](prototipos/h1-b-neon.html) |
| H1-c · Pastel | [claude.ai/artifact/GcGp6nLQqizPT4EGNKFqqX](https://claude.ai/artifact/GcGp6nLQqizPT4EGNKFqqX) | [prototipos/h1-c-pastel.html](prototipos/h1-c-pastel.html) |
| H1-d · Señalética | [claude.ai/artifact/FgwuxR1YQtLQubAWM7DpB5](https://claude.ai/artifact/FgwuxR1YQtLQubAWM7DpB5) | [prototipos/h1-d-senaletica.html](prototipos/h1-d-senaletica.html) |
| H1-e · Cálida | [claude.ai/artifact/N2iU7SPBcZ7AVZuEhNsK5J](https://claude.ai/artifact/N2iU7SPBcZ7AVZuEhNsK5J) | [prototipos/h1-e-calida.html](prototipos/h1-e-calida.html) |
| H1-f · Fría | [claude.ai/artifact/KCcfyaRHytXCAujFshgG35](https://claude.ai/artifact/KCcfyaRHytXCAujFshgG35) | [prototipos/h1-f-fria.html](prototipos/h1-f-fria.html) |

Los enlaces son privados: solo los abre el dueño de la cuenta hasta que se compartan desde el menú Share. La página de comparación guarda cada voto (me gusta / en parte / no me gusta) y sus notas en su base de datos, colección `feedback`, documentos `h1-a` … `h1-f` y `general` (campos `verdict`, `notes`, `updatedAt`; en `general`, `favourite` y `notes`). El coordinador las lee con `ArtifactData list` sobre esa URL.

## Resumen

| | Color | Aura | Sello | Transmite | ¿Moda o dura? |
|---|---|---|---|---|---|
| **H1-a · Mineral** | Tierra y minerales; marca lapislázuli | Anillos de geoda | Sello circular girado | Archivo, geología, rigor tranquilo | Dura |
| **H1-b · Neon Night** | Neón sobre casi negro; marca magenta eléctrico | Constelación de puntos | Pastilla minimalista | Terminal nocturna, tecnología 2026 | Pasajera (color) |
| **H1-c · Pastel** | Pastel suave; marca ciruela | Mancha orgánica | Etiqueta con esquina cortada | Cercanía, comunidad, principiantes | Pasajera |
| **H1-d · Señalética** | Negro, blanco y colores de pictograma; amarillo señal | Mosaico de celdas | Matasellos | Autoridad, claridad, cero adorno | Dura |
| **H1-e · Cálida** | Cálida; marca azafrán tostado | Barras radiales | Ticket troquelado | Energía, optimismo, "recibo" literal | Intermedia |
| **H1-f · Fría** | Fría; marca cobalto | Franjas tipo código de barras | Sello de doble filete | Infraestructura, laboratorio, precisión | Dura (forma); paleta genérica |

---

## H1-a · Mineral

Prototipo: [claude.ai/artifact/Ecnkb21egeuEA7Kn8kEFwr](https://claude.ai/artifact/Ecnkb21egeuEA7Kn8kEFwr) · fichero [prototipos/h1-a-mineral.html](prototipos/h1-a-mineral.html)

- **Color.** Tierra y minerales: lapislázuli (marca), verdín, ocre, malaquita, cinabrio, umbra, amatista sobre piedra clara o basalto.
- **Aura · Anillos de geoda.** Un anillo concéntrico por modalidad, de fuera a dentro. Continuo: el anillo central se cierra en disco. Trial: núcleo hueco. Cada anillo tiene un corte cuyo ángulo sale del slug (huella única). No consta: aro exterior discontinuo. Más de 30 días: desaturado.
- **Sello · Sello circular girado.** Sello de goma circular girado −10°, con el texto "VERIFIED · SOURCE QUOTED" en el anillo y ✓ + fecha en el centro.
- **Qué transmite.** Geología, archivo, instrumento científico. Serio, cálido sin ser rústico; transmite que los datos están "estratificados" y fechados.
- **¿Moda o dura?** Dura. Las paletas minerales y los anillos concéntricos no pertenecen a una moda concreta; el riesgo es leerse algo sobrio para Product Hunt.
- **Leyenda en la ficha.** "How to read this aura: each ring is one modality, outside in · closed core = ongoing · open core = trial · dashed outer ring = flags not stated."

### Tokens

| Token | Uso | Claro | Contraste (bg / panel) | Oscuro | Contraste (bg / panel) |
|---|---|---|---|---|---|
| `--bg` | Fondo | `#F4F5F2` | — | `#121412` | — |
| `--panel` | Panel | `#FFFFFF` | — | `#1B1E1B` | — |
| `--ink` | Texto | `#141A17` | 16.13 / 17.65 | `#EEF0EC` | 16.14 / 14.67 |
| `--muted` | Secundario | `#56605A` | 5.97 / 6.53 | `#A3ABA4` | 7.86 / 7.15 |
| `--line` | Línea | `#DFE3DD` | — | `#2B302C` | — |
| `--control` | Borde de control (≥3) | `#858E87` | 3.09 / 3.38 | `#6A726B` | 3.73 / 3.39 |
| `--accent` | Marca / enlaces | `#2A4A99` | 7.56 / 8.27 | `#9DB4F2` | 9.03 / 8.21 |
| `--on-accent` | Texto de botón | `#FFFFFF` | 8.27 sobre marca | `#121412` | 9.03 sobre marca |
| `--ok` | OK | `#1E6E43` | 5.70 / 6.24 | `#6FCB93` | 9.38 / 8.52 |
| `--unk` | No consta | `#8A5A00` | 5.42 / 5.93 | `#E2B45C` | 9.62 / 8.75 |
| `--bad` | Bloqueador | `#A8321C` | 6.12 / 6.69 | `#F08A72` | 7.57 / 6.88 |
| `--chg` | Cambio | `#5B3FA6` | 7.09 / 7.76 | `#B9A6F0` | 8.62 / 7.83 |
| `--seal-bg` | Fondo del sello | `#FFFFFF` | marca encima: 8.27 | `#1B1E1B` | marca encima: 8.21 |
| `--h-text` | Modalidad text (gráfico) | `#3557A8` | 6.23 | `#7F9BE0` | 6.76 |
| `--h-vision` | Modalidad vision (gráfico) | `#2F8C80` | 3.70 | `#5DBDB0` | 8.26 |
| `--h-audio` | Modalidad audio (gráfico) | `#B57A1E` | 3.33 | `#D9A54A` | 8.31 |
| `--h-embeddings` | Modalidad embeddings (gráfico) | `#2F7D4F` | 4.60 | `#62B07F` | 7.08 |
| `--h-image` | Modalidad image (gráfico) | `#B8452B` | 4.89 | `#E07A5E` | 6.27 |
| `--h-ocr` | Modalidad ocr (gráfico) | `#7E5638` | 5.86 | `#B98C68` | 6.18 |
| `--h-rerank` | Modalidad rerank (gráfico) | `#75579A` | 5.35 | `#A88BCF` | 6.40 |

```css
:root {
  --bg: #F4F5F2;
  --panel: #FFFFFF;
  --ink: #141A17;
  --muted: #56605A;
  --line: #DFE3DD;
  --control: #858E87;
  --accent: #2A4A99;
  --on-accent: #FFFFFF;
  --ok: #1E6E43;
  --unk: #8A5A00;
  --bad: #A8321C;
  --chg: #5B3FA6;
  --seal-bg: #FFFFFF;
  --h-text: #3557A8;
  --h-vision: #2F8C80;
  --h-audio: #B57A1E;
  --h-embeddings: #2F7D4F;
  --h-image: #B8452B;
  --h-ocr: #7E5638;
  --h-rerank: #75579A;
  --radius: 14px;
  --h1-weight: 700; --h1-stretch: 100%; --h1-transform: none; --h1-tracking: -.03em;
}
@media (prefers-color-scheme: dark) { :root:not([data-theme="light"]) {
  --bg: #121412;
  --panel: #1B1E1B;
  --ink: #EEF0EC;
  --muted: #A3ABA4;
  --line: #2B302C;
  --control: #6A726B;
  --accent: #9DB4F2;
  --on-accent: #121412;
  --ok: #6FCB93;
  --unk: #E2B45C;
  --bad: #F08A72;
  --chg: #B9A6F0;
  --seal-bg: #1B1E1B;
  --h-text: #7F9BE0;
  --h-vision: #5DBDB0;
  --h-audio: #D9A54A;
  --h-embeddings: #62B07F;
  --h-image: #E07A5E;
  --h-ocr: #B98C68;
  --h-rerank: #A88BCF;
  color-scheme: dark;
} }
:root[data-theme="dark"] { /* mismos valores oscuros */ }
```

### Parámetros del aura

```yaml
aura: geode            # anillos concéntricos
viewBox: 100
outer_radius: 44
core_hole: {ongoing: 0, trial: 15}       # trial = núcleo hueco
ring_width: (44 - core_hole) / n_modalities, separación 1.8
ring_order: orden de `modalities` en providers.json, de fuera a dentro
ongoing_core: el último anillo se dibuja como disco lleno
gap_per_ring: 3.5–8.5 % de la circunferencia, ángulo = seed(slug)
not_stated: aro r=48.6, trazo 2.2, dash "4 3", color --unk   # si ≥1 flag es null
stale_over_30d: filter saturate(.2)
```

### Parámetros del sello

```yaml
seal: circular-rotated
size: {row: 54px, page: 118px}
rotate: -10deg
rings: exterior trazo 3, interior r=28 trazo 1.4, color --accent
ring_text: "VERIFIED · SOURCE QUOTED · N SOURCES ·" en DM Mono 9.4/100, tracking 1.2
center: "✓" + fecha corta (página) o edad "2D" (fila)
```

---

## H1-b · Neon Night

Prototipo: [claude.ai/artifact/VJcwqgwYuQSuZaxCTQBVK4](https://claude.ai/artifact/VJcwqgwYuQSuZaxCTQBVK4) · fichero [prototipos/h1-b-neon.html](prototipos/h1-b-neon.html)

- **Color.** Neón sobre casi negro en oscuro (magenta eléctrico de marca, cian, lima, ámbar); en claro, los mismos matices saturados y oscurecidos hasta pasar 3:1.
- **Aura · Constelación de puntos.** Puntos en 2-3 órbitas, unidos por líneas finas los de la misma modalidad. Número de puntos según modelos gratis (más modelos, más estrellas). Continuo: puntos llenos y estrella central. Trial: puntos huecos sin centro. No consta: órbita exterior discontinua. En oscuro los puntos brillan.
- **Sello · Pastilla minimalista.** Pastilla plana sin girar: punto de estado verde + "Verified · 24 Nov 2026 · 7 sources". La más discreta de las seis.
- **Qué transmite.** Panel nocturno, terminal, cielo de datos. Moderna y tecnológica; la que más "se siente 2026" en oscuro.
- **¿Moda o dura?** Pasajera en el color: el neón con brillo es estética 2024-26 y envejecerá. La constelación como forma sí dura. En claro pierde gran parte del neón.
- **Leyenda en la ficha.** "How to read this aura: each colour of star is one modality · filled stars + centre = ongoing · hollow stars = trial · more stars = more free models · dashed orbit = flags not stated."

### Tokens

| Token | Uso | Claro | Contraste (bg / panel) | Oscuro | Contraste (bg / panel) |
|---|---|---|---|---|---|
| `--bg` | Fondo | `#FBFBFE` | — | `#09090F` | — |
| `--panel` | Panel | `#FFFFFF` | — | `#13131C` | — |
| `--ink` | Texto | `#0C0B14` | 18.94 / 19.56 | `#F4F3FF` | 18.07 / 16.80 |
| `--muted` | Secundario | `#535166` | 7.43 / 7.67 | `#A9A7C0` | 8.49 / 7.89 |
| `--line` | Línea | `#E4E3EE` | — | `#262536` | — |
| `--control` | Borde de control (≥3) | `#85839A` | 3.56 / 3.68 | `#64637D` | 3.43 / 3.18 |
| `--accent` | Marca / enlaces | `#A0008F` | 7.03 / 7.26 | `#FF4FF0` | 7.21 / 6.71 |
| `--on-accent` | Texto de botón | `#FFFFFF` | 7.26 sobre marca | `#09090F` | 7.21 sobre marca |
| `--ok` | OK | `#007A4D` | 5.23 / 5.40 | `#3DFFA8` | 15.19 / 14.12 |
| `--unk` | No consta | `#8A5A00` | 5.74 / 5.93 | `#FFD23F` | 13.75 / 12.78 |
| `--bad` | Bloqueador | `#C2002E` | 6.10 / 6.30 | `#FF5C7A` | 6.68 / 6.21 |
| `--chg` | Cambio | `#3D3DE0` | 6.91 / 7.14 | `#8F8FFF` | 7.13 / 6.63 |
| `--seal-bg` | Fondo del sello | `#FFFFFF` | marca encima: 7.26 | `#13131C` | marca encima: 6.71 |
| `--h-text` | Modalidad text (gráfico) | `#6C3CF0` | 5.74 | `#A585FF` | 7.00 |
| `--h-vision` | Modalidad vision (gráfico) | `#008FB0` | 3.66 | `#2DE2FF` | 12.70 |
| `--h-audio` | Modalidad audio (gráfico) | `#B07A00` | 3.61 | `#FFD23F` | 13.75 |
| `--h-embeddings` | Modalidad embeddings (gráfico) | `#00915A` | 3.91 | `#3DFFA8` | 15.19 |
| `--h-image` | Modalidad image (gráfico) | `#D1009F` | 4.83 | `#FF4FD8` | 6.96 |
| `--h-ocr` | Modalidad ocr (gráfico) | `#D25A00` | 3.91 | `#FF8A3D` | 8.47 |
| `--h-rerank` | Modalidad rerank (gráfico) | `#2E6BF0` | 4.54 | `#5C9DFF` | 7.30 |

```css
:root {
  --bg: #FBFBFE;
  --panel: #FFFFFF;
  --ink: #0C0B14;
  --muted: #535166;
  --line: #E4E3EE;
  --control: #85839A;
  --accent: #A0008F;
  --on-accent: #FFFFFF;
  --ok: #007A4D;
  --unk: #8A5A00;
  --bad: #C2002E;
  --chg: #3D3DE0;
  --seal-bg: #FFFFFF;
  --h-text: #6C3CF0;
  --h-vision: #008FB0;
  --h-audio: #B07A00;
  --h-embeddings: #00915A;
  --h-image: #D1009F;
  --h-ocr: #D25A00;
  --h-rerank: #2E6BF0;
  --radius: 999px;
  --h1-weight: 850; --h1-stretch: 118%; --h1-transform: uppercase; --h1-tracking: -.01em;
}
@media (prefers-color-scheme: dark) { :root:not([data-theme="light"]) {
  --bg: #09090F;
  --panel: #13131C;
  --ink: #F4F3FF;
  --muted: #A9A7C0;
  --line: #262536;
  --control: #64637D;
  --accent: #FF4FF0;
  --on-accent: #09090F;
  --ok: #3DFFA8;
  --unk: #FFD23F;
  --bad: #FF5C7A;
  --chg: #8F8FFF;
  --seal-bg: #13131C;
  --h-text: #A585FF;
  --h-vision: #2DE2FF;
  --h-audio: #FFD23F;
  --h-embeddings: #3DFFA8;
  --h-image: #FF4FD8;
  --h-ocr: #FF8A3D;
  --h-rerank: #5C9DFF;
  color-scheme: dark;
} }
:root[data-theme="dark"] { /* mismos valores oscuros */ }
```

### Parámetros del aura

```yaml
aura: constellation
viewBox: 100
orbits: [17, 30, 42]  # se usan 2 (≤2 modalidades) o 3; trazo 0.9 en --line
stars: clamp(2 × models_free + n_modalities, 5, 15)
star_radius: 2.8–5.4 (seed)
star_orbit_and_angle: seed(slug)
modality: estrella i → modalities[i % n]; líneas de 1 px (opacidad .6) unen estrellas de la misma modalidad
ongoing: estrellas llenas + estrella central r=6.5 (primera modalidad)
trial: estrellas huecas (trazo 1.9), sin centro
not_stated: órbita exterior con trazo 2 y dash "3 3" en --unk
glow: oscuro → drop-shadow(0 0 2.5px currentColor); claro → none
stale_over_30d: saturate(.2)
```

### Parámetros del sello

```yaml
seal: pill
shape: radio 999px, borde 1px --control, fondo --seal-bg, sin giro
content: punto 8px en --ok (con --glow) + "Verified" en --accent + "· 24 Nov 2026 · 7 sources" en --ink
font: DM Mono 500 12px (fila) / 14px (página)
```

---

## H1-c · Pastel

Prototipo: [claude.ai/artifact/GcGp6nLQqizPT4EGNKFqqX](https://claude.ai/artifact/GcGp6nLQqizPT4EGNKFqqX) · fichero [prototipos/h1-c-pastel.html](prototipos/h1-c-pastel.html)

- **Color.** Pastel suave (lavanda, aguamarina, melocotón, menta, rosa, albaricoque, azul hielo) con marca ciruela. Los rellenos pastel son decorativos en claro: el contorno de tinta lleva el contraste 3:1.
- **Aura · Mancha orgánica.** Un lóbulo orgánico por modalidad, superpuestos en multiplicación como tintas. La forma de cada lóbulo sale del slug. Continuo: mancha llena. Trial: agujero central. No consta: contorno discontinuo ámbar en lugar de tinta.
- **Sello · Etiqueta con esquina cortada.** Etiqueta de equipaje con esquina en punta y ojal, fondo lavanda, girada −3°.
- **Qué transmite.** Amable, cercana, poco intimidante; invita a principiantes. Menos "auditoría" y más "comunidad".
- **¿Moda o dura?** Pasajera: las manchas orgánicas y el pastel vienen de 2019-23 y ya se asocian a ilustración corporativa. La etiqueta sí dura.
- **Leyenda en la ficha.** "How to read this aura: each lobe is one modality · solid blob = ongoing · hole in the middle = trial · dashed amber outline = flags not stated."

### Tokens

| Token | Uso | Claro | Contraste (bg / panel) | Oscuro | Contraste (bg / panel) |
|---|---|---|---|---|---|
| `--bg` | Fondo | `#FBFAFD` | — | `#16151C` | — |
| `--panel` | Panel | `#FFFFFF` | — | `#1F1D27` | — |
| `--ink` | Texto | `#1D1A26` | 16.45 / 17.10 | `#F2EFF8` | 15.95 / 14.63 |
| `--muted` | Secundario | `#5D5870` | 6.52 / 6.78 | `#AEA8BE` | 7.90 / 7.24 |
| `--line` | Línea | `#E9E6F0` | — | `#2E2B38` | — |
| `--control` | Borde de control (≥3) | `#8B869A` | 3.38 / 3.51 | `#6D687B` | 3.38 / 3.10 |
| `--accent` | Marca / enlaces | `#6B3FA0` | 7.10 / 7.38 | `#D2BBFF` | 10.61 / 9.73 |
| `--on-accent` | Texto de botón | `#FFFFFF` | 7.38 sobre marca | `#16151C` | 10.61 sobre marca |
| `--ok` | OK | `#1F7048` | 5.82 / 6.05 | `#8FDDB0` | 11.34 / 10.40 |
| `--unk` | No consta | `#8A5700` | 5.86 / 6.10 | `#F2C46E` | 11.14 / 10.21 |
| `--bad` | Bloqueador | `#B0303C` | 6.06 / 6.30 | `#FF9AA3` | 8.98 / 8.23 |
| `--chg` | Cambio | `#4248C9` | 6.73 / 7.00 | `#A9AEFF` | 8.79 / 8.06 |
| `--seal-bg` | Fondo del sello | `#F1EAFB` | marca encima: 6.30 | `#2A2536` | marca encima: 8.68 |
| `--h-text` | Modalidad text (gráfico) | `#C9B8FF` | 1.71 | `#C9B8FF` | 10.17 |
| `--h-vision` | Modalidad vision (gráfico) | `#A6E3EE` | 1.36 | `#A6E3EE` | 12.82 |
| `--h-audio` | Modalidad audio (gráfico) | `#FFD79C` | 1.31 | `#FFD79C` | 13.34 |
| `--h-embeddings` | Modalidad embeddings (gráfico) | `#B4E9CC` | 1.31 | `#B4E9CC` | 13.36 |
| `--h-image` | Modalidad image (gráfico) | `#FFC0D4` | 1.47 | `#FFC0D4` | 11.87 |
| `--h-ocr` | Modalidad ocr (gráfico) | `#FFCBAE` | 1.40 | `#FFCBAE` | 12.44 |
| `--h-rerank` | Modalidad rerank (gráfico) | `#BBD1FF` | 1.48 | `#BBD1FF` | 11.81 |
| `--edge` | Contorno de tinta del aura | `#4A4560` | 8.74 | `#6A696E` | 3.33 |

**Nota de contraste.** En claro, `--h-text`, `--h-vision`, `--h-audio`, `--h-embeddings`, `--h-image`, `--h-ocr`, `--h-rerank` quedan por debajo de 3:1 como relleno; el contorno `--edge` del aura (8.74:1) es el que cumple 1.4.11, así que **el contorno no se puede quitar** al implantar.

```css
:root {
  --bg: #FBFAFD;
  --panel: #FFFFFF;
  --ink: #1D1A26;
  --muted: #5D5870;
  --line: #E9E6F0;
  --control: #8B869A;
  --accent: #6B3FA0;
  --on-accent: #FFFFFF;
  --ok: #1F7048;
  --unk: #8A5700;
  --bad: #B0303C;
  --chg: #4248C9;
  --seal-bg: #F1EAFB;
  --h-text: #C9B8FF;
  --h-vision: #A6E3EE;
  --h-audio: #FFD79C;
  --h-embeddings: #B4E9CC;
  --h-image: #FFC0D4;
  --h-ocr: #FFCBAE;
  --h-rerank: #BBD1FF;
  --edge: #4A4560;
  --radius: 26px;
  --h1-weight: 620; --h1-stretch: 108%; --h1-transform: none; --h1-tracking: -.025em;
}
@media (prefers-color-scheme: dark) { :root:not([data-theme="light"]) {
  --bg: #16151C;
  --panel: #1F1D27;
  --ink: #F2EFF8;
  --muted: #AEA8BE;
  --line: #2E2B38;
  --control: #6D687B;
  --accent: #D2BBFF;
  --on-accent: #16151C;
  --ok: #8FDDB0;
  --unk: #F2C46E;
  --bad: #FF9AA3;
  --chg: #A9AEFF;
  --seal-bg: #2A2536;
  --h-text: #C9B8FF;
  --h-vision: #A6E3EE;
  --h-audio: #FFD79C;
  --h-embeddings: #B4E9CC;
  --h-image: #FFC0D4;
  --h-ocr: #FFCBAE;
  --h-rerank: #BBD1FF;
  --edge: #6A696E;
  color-scheme: dark;
} }
:root[data-theme="dark"] { /* mismos valores oscuros */ }
```

### Parámetros del aura

```yaml
aura: blob
viewBox: 100
lobes: uno por modalidad; radio 36 (1 mod.), 28 (2), 24 (≥3); desplazamiento 14 del centro
lobe_shape: 7 puntos, radio × 0.80–1.16 (seed), Catmull-Rom cerrado
blend: claro multiply · oscuro screen
edge: trazo 1.5 en --edge (lleva el 3:1 en claro)
trial: máscara circular r=13 en el centro + aro --edge
not_stated: el contorno pasa a --unk, trazo 2.2, dash "4 3"
stale_over_30d: saturate(.2)
```

### Parámetros del sello

```yaml
seal: cut-corner-tag
shape: clip-path polygon(11px 0,100% 0,100% 100%,11px 100%,0 50%), radio derecho 6px
eyelet: círculo 6px en --surf con anillo 1.5px --accent, a 10px del borde
fill: --seal-bg; texto --accent
rotate: -3deg
font: DM Mono 500 12px / 14px
```

---

## H1-d · Señalética

Prototipo: [claude.ai/artifact/FgwuxR1YQtLQubAWM7DpB5](https://claude.ai/artifact/FgwuxR1YQtLQubAWM7DpB5) · fichero [prototipos/h1-d-senaletica.html](prototipos/h1-d-senaletica.html)

- **Color.** Alto contraste de señalética: negro y blanco puros, amarillo señal como color de marca de relleno, azul, verde, magenta, naranja y púrpura de pictograma. Rejilla de tinta 21:1 alrededor de cada celda.
- **Aura · Mosaico de celdas.** Rejilla 4×4 con marco de tinta. Las celdas se reparten entre modalidades en bloques. Continuo: 16 celdas. Trial: el centro (4 celdas) vacío. No consta: una celda discontinua vacía por cada flag sin decir (cuenta exacta, de 0 a 4). Más de 30 días: desaturado.
- **Sello · Matasellos.** Matasellos azul: círculo con VERIFIED / fecha / fuentes y ondas de cancelación a la derecha.
- **Qué transmite.** Aeropuerto, metro, normas. Autoridad, claridad, cero adorno; el "not stated" se cuenta celda a celda.
- **¿Moda o dura?** Dura. La señalética suiza (Aicher, Vignelli) lleva 60 años vigente. Riesgo: frialdad institucional si se abusa del negro.
- **Leyenda en la ficha.** "How to read this aura: colour blocks = modalities · full grid = ongoing · empty centre = trial · each dashed cell = one flag not stated."

### Tokens

| Token | Uso | Claro | Contraste (bg / panel) | Oscuro | Contraste (bg / panel) |
|---|---|---|---|---|---|
| `--bg` | Fondo | `#FFFFFF` | — | `#000000` | — |
| `--panel` | Panel | `#F4F4F4` | — | `#141414` | — |
| `--ink` | Texto | `#000000` | 21.00 / 19.09 | `#FFFFFF` | 21.00 / 18.42 |
| `--muted` | Secundario | `#4A4A4A` | 8.86 / 8.06 | `#B5B5B5` | 10.24 / 8.98 |
| `--line` | Línea | `#D6D6D6` | — | `#2E2E2E` | — |
| `--control` | Borde de control (≥3) | `#767676` | 4.54 / 4.13 | `#7A7A7A` | 4.89 / 4.29 |
| `--accent` | Marca / enlaces | `#0040A8` | 9.14 / 8.31 | `#7FB2FF` | 9.71 / 8.52 |
| `--on-accent` | Texto de botón | `#FFFFFF` | 9.14 sobre marca | `#000000` | 9.71 sobre marca |
| `--ok` | OK | `#00703A` | 6.22 / 5.65 | `#4CD787` | 11.38 / 9.98 |
| `--unk` | No consta | `#8A5A00` | 5.93 / 5.39 | `#FFC20E` | 12.98 / 11.38 |
| `--bad` | Bloqueador | `#C8102E` | 5.88 / 5.35 | `#FF6B7D` | 7.65 / 6.71 |
| `--chg` | Cambio | `#5A2D91` | 9.46 / 8.60 | `#B794F4` | 8.56 / 7.51 |
| `--seal-bg` | Fondo del sello | `#FFFFFF` | marca encima: 9.14 | `#000000` | marca encima: 9.71 |
| `--h-text` | Modalidad text (gráfico) | `#0047BB` | 8.02 | `#3D7DFF` | 5.58 |
| `--h-vision` | Modalidad vision (gráfico) | `#00A3E0` | 2.87 | `#00B8F0` | 9.11 |
| `--h-audio` | Modalidad audio (gráfico) | `#FFC20E` | 1.62 | `#FFC20E` | 12.98 |
| `--h-embeddings` | Modalidad embeddings (gráfico) | `#009A44` | 3.68 | `#14B85A` | 8.03 |
| `--h-image` | Modalidad image (gráfico) | `#E5007D` | 4.54 | `#FF2E9A` | 6.11 |
| `--h-ocr` | Modalidad ocr (gráfico) | `#FF6A13` | 2.87 | `#FF7A2A` | 8.07 |
| `--h-rerank` | Modalidad rerank (gráfico) | `#6A2C91` | 8.82 | `#9B5DD6` | 4.93 |
| `--edge` | Contorno de tinta del aura | `#000000` | 21.00 | `#FFFFFF` | 21.00 |
| `--signal` | Amarillo señal (solo relleno, con tinta encima) | `#FFC20E` | tinta encima 12.98 | `#FFC20E` | — |

**Nota de contraste.** En claro, `--h-vision`, `--h-audio`, `--h-ocr` quedan por debajo de 3:1 como relleno; el contorno `--edge` del aura (21.00:1) es el que cumple 1.4.11, así que **el contorno no se puede quitar** al implantar.

```css
:root {
  --bg: #FFFFFF;
  --panel: #F4F4F4;
  --ink: #000000;
  --muted: #4A4A4A;
  --line: #D6D6D6;
  --control: #767676;
  --accent: #0040A8;
  --on-accent: #FFFFFF;
  --ok: #00703A;
  --unk: #8A5A00;
  --bad: #C8102E;
  --chg: #5A2D91;
  --seal-bg: #FFFFFF;
  --h-text: #0047BB;
  --h-vision: #00A3E0;
  --h-audio: #FFC20E;
  --h-embeddings: #009A44;
  --h-image: #E5007D;
  --h-ocr: #FF6A13;
  --h-rerank: #6A2C91;
  --edge: #000000;
  --signal: #FFC20E;
  --radius: 0px;
  --h1-weight: 900; --h1-stretch: 72%; --h1-transform: uppercase; --h1-tracking: -.005em;
}
@media (prefers-color-scheme: dark) { :root:not([data-theme="light"]) {
  --bg: #000000;
  --panel: #141414;
  --ink: #FFFFFF;
  --muted: #B5B5B5;
  --line: #2E2E2E;
  --control: #7A7A7A;
  --accent: #7FB2FF;
  --on-accent: #000000;
  --ok: #4CD787;
  --unk: #FFC20E;
  --bad: #FF6B7D;
  --chg: #B794F4;
  --seal-bg: #000000;
  --h-text: #3D7DFF;
  --h-vision: #00B8F0;
  --h-audio: #FFC20E;
  --h-embeddings: #14B85A;
  --h-image: #FF2E9A;
  --h-ocr: #FF7A2A;
  --h-rerank: #9B5DD6;
  --edge: #FFFFFF;
  --signal: #FFC20E;
  color-scheme: dark;
} }
:root[data-theme="dark"] { /* mismos valores oscuros */ }
```

### Parámetros del aura

```yaml
aura: mosaic
viewBox: 100
grid: 4×4, celda 22, paso 23.4, marco --edge (tinta) 97×97, sin radio
cell_order: por ángulo alrededor del centro, inicio rotado por seed(slug) → bloques contiguos por modalidad
ongoing: 16 celdas
trial: 4 celdas centrales vacías (color --surf)
not_stated: una celda vacía con cuadrado discontinuo (--unk, trazo 2.4, dash "3.4 2.6") por cada flag null (0–4)
modality_share: celdas restantes repartidas en proporción igual entre modalidades
stale_over_30d: saturate(.2)
```

### Parámetros del sello

```yaml
seal: postmark
circle: {row: 50px, page: 126px}, borde 2px (fila) / 3px + aro interior a 4px (página), --accent
content: "VERIFIED" (versalitas 6.5–10px) / fecha "24 NOV 2026" o "✓ 2D" / "N SOURCES"
cancel_waves: 4 ondas, máscara SVG coloreada con --accent, 30×24 (fila) / 76×56 (página), solapadas −6/−14px
rotate: 0
```

---

## H1-e · Cálida

Prototipo: [claude.ai/artifact/N2iU7SPBcZ7AVZuEhNsK5J](https://claude.ai/artifact/N2iU7SPBcZ7AVZuEhNsK5J) · fichero [prototipos/h1-e-calida.html](prototipos/h1-e-calida.html)

- **Color.** Cálida: azafrán tostado (marca), bermellón, ámbar, frambuesa, mostaza, rosa, óxido y ciruela sobre blanco rosado o negro cálido.
- **Aura · Barras radiales.** 40 barras en abanico, un sector de color por modalidad; el largo de cada barra sale del slug. Continuo: las barras nacen del centro (sol). Trial: solo una corona exterior. No consta: círculo exterior discontinuo.
- **Sello · Ticket troquelado.** Ticket con muescas troqueladas a los lados y línea de corte entre el ✓ y el texto, fondo albaricoque.
- **Qué transmite.** Energía, sol, mercado; acogedora y optimista sin perder precisión. El ticket enlaza con "receipts" de forma literal.
- **¿Moda o dura?** Intermedia. Los abanicos radiales son una forma clásica de visualización; las paletas cálidas van por ciclos (2026 está en uno al alza).
- **Leyenda en la ficha.** "How to read this aura: each colour sector is one modality · rays from the centre = ongoing · outer crown only = trial · dashed circle = flags not stated."

### Tokens

| Token | Uso | Claro | Contraste (bg / panel) | Oscuro | Contraste (bg / panel) |
|---|---|---|---|---|---|
| `--bg` | Fondo | `#FFF9F6` | — | `#17110F` | — |
| `--panel` | Panel | `#FFFFFF` | — | `#211915` | — |
| `--ink` | Texto | `#22140F` | 17.13 / 17.87 | `#FBF1EC` | 16.82 / 15.56 |
| `--muted` | Secundario | `#6A5048` | 7.05 / 7.36 | `#C2A89E` | 8.36 / 7.73 |
| `--line` | Línea | `#F0E2DB` | — | `#352822` | — |
| `--control` | Borde de control (≥3) | `#9A8179` | 3.48 / 3.63 | `#7A645B` | 3.38 / 3.13 |
| `--accent` | Marca / enlaces | `#9C4A00` | 5.93 / 6.19 | `#FFB25C` | 10.48 / 9.69 |
| `--on-accent` | Texto de botón | `#FFFFFF` | 6.19 sobre marca | `#17110F` | 10.48 sobre marca |
| `--ok` | OK | `#2F6B1F` | 6.21 / 6.47 | `#9AD27F` | 10.59 / 9.80 |
| `--unk` | No consta | `#7F5A00` | 5.98 / 6.24 | `#F2C14E` | 11.14 / 10.30 |
| `--bad` | Bloqueador | `#B3261E` | 6.27 / 6.54 | `#FF8A7A` | 8.16 / 7.55 |
| `--chg` | Cambio | `#7A2E8C` | 7.75 / 8.09 | `#E0A3F0` | 9.49 / 8.78 |
| `--seal-bg` | Fondo del sello | `#FFEBD9` | marca encima: 5.35 | `#2E2119` | marca encima: 8.74 |
| `--h-text` | Modalidad text (gráfico) | `#D9502A` | 3.92 | `#FF7A4D` | 7.25 |
| `--h-vision` | Modalidad vision (gráfico) | `#C48200` | 3.08 | `#F5B21F` | 10.03 |
| `--h-audio` | Modalidad audio (gráfico) | `#C2185B` | 5.63 | `#FF5C93` | 6.41 |
| `--h-embeddings` | Modalidad embeddings (gráfico) | `#8E7A00` | 4.08 | `#C9B02E` | 8.66 |
| `--h-image` | Modalidad image (gráfico) | `#D85A85` | 3.52 | `#FF9CBC` | 9.55 |
| `--h-ocr` | Modalidad ocr (gráfico) | `#8B3A2E` | 7.34 | `#D97A62` | 6.15 |
| `--h-rerank` | Modalidad rerank (gráfico) | `#7B2D6B` | 8.29 | `#C77AB8` | 6.15 |

```css
:root {
  --bg: #FFF9F6;
  --panel: #FFFFFF;
  --ink: #22140F;
  --muted: #6A5048;
  --line: #F0E2DB;
  --control: #9A8179;
  --accent: #9C4A00;
  --on-accent: #FFFFFF;
  --ok: #2F6B1F;
  --unk: #7F5A00;
  --bad: #B3261E;
  --chg: #7A2E8C;
  --seal-bg: #FFEBD9;
  --h-text: #D9502A;
  --h-vision: #C48200;
  --h-audio: #C2185B;
  --h-embeddings: #8E7A00;
  --h-image: #D85A85;
  --h-ocr: #8B3A2E;
  --h-rerank: #7B2D6B;
  --radius: 18px;
  --h1-weight: 760; --h1-stretch: 92%; --h1-transform: none; --h1-tracking: -.03em;
}
@media (prefers-color-scheme: dark) { :root:not([data-theme="light"]) {
  --bg: #17110F;
  --panel: #211915;
  --ink: #FBF1EC;
  --muted: #C2A89E;
  --line: #352822;
  --control: #7A645B;
  --accent: #FFB25C;
  --on-accent: #17110F;
  --ok: #9AD27F;
  --unk: #F2C14E;
  --bad: #FF8A7A;
  --chg: #E0A3F0;
  --seal-bg: #2E2119;
  --h-text: #FF7A4D;
  --h-vision: #F5B21F;
  --h-audio: #FF5C93;
  --h-embeddings: #C9B02E;
  --h-image: #FF9CBC;
  --h-ocr: #D97A62;
  --h-rerank: #C77AB8;
  color-scheme: dark;
} }
:root[data-theme="dark"] { /* mismos valores oscuros */ }
```

### Parámetros del aura

```yaml
aura: radial-bars
viewBox: 100
bars: 40, trazo 3.3 (ongoing) / 3.0 (trial), extremo redondo
sectors: contiguos, uno por modalidad (40 / n barras cada uno), rotación = seed(slug)
ongoing: barras desde r=9, largo 0.45–1 × 37 (seed)
trial: barras desde r=27, largo 0.45–1 × 18 (solo corona)
not_stated: aro r=48.4, trazo 2.2, dash "4 3", --unk
stale_over_30d: saturate(.2)
```

### Parámetros del sello

```yaml
seal: perforated-ticket
shape: muescas semicirculares de r=5px a izquierda y derecha (mask radial-gradient)
stub: "✓" separado por línea discontinua 1.5px --accent
fill: --seal-bg; texto --accent
rotate: -1.5deg
font: DM Mono 500 12px / 14px (✓ 16px en página)
```

---

## H1-f · Fría

Prototipo: [claude.ai/artifact/KCcfyaRHytXCAujFshgG35](https://claude.ai/artifact/KCcfyaRHytXCAujFshgG35) · fichero [prototipos/h1-f-fria.html](prototipos/h1-f-fria.html)

- **Color.** Fría: cobalto (marca), glaciar, iris, abeto, violeta, pizarra y cielo sobre hielo o azul noche.
- **Aura · Franjas tipo código de barras.** Cuadrado redondeado con franjas horizontales de grosor variable (sale del slug), agrupadas por modalidad, como un código de barras o una huella. Continuo: franjas enteras. Trial: franjas partidas por el centro. No consta: marco discontinuo.
- **Sello · Sello de doble filete.** Sello notarial rectangular de doble filete, en versalitas espaciadas, girado −3°.
- **Qué transmite.** Laboratorio, registro, logística precisa. Fría y exacta; la más "infraestructura".
- **¿Moda o dura?** Dura en la forma (el código de barras es un icono de verificación). Riesgo: la paleta fría es la más parecida al SaaS genérico y puede perder esencia.
- **Leyenda en la ficha.** "How to read this aura: colour bands are modalities · full stripes = ongoing · stripes split in the middle = trial · dashed frame = flags not stated."

### Tokens

| Token | Uso | Claro | Contraste (bg / panel) | Oscuro | Contraste (bg / panel) |
|---|---|---|---|---|---|
| `--bg` | Fondo | `#F5F8FA` | — | `#0A1016` | — |
| `--panel` | Panel | `#FFFFFF` | — | `#121A22` | — |
| `--ink` | Texto | `#0D1720` | 16.97 / 18.10 | `#EAF2F8` | 16.89 / 15.51 |
| `--muted` | Secundario | `#4E5D6B` | 6.35 / 6.77 | `#9AAAB8` | 8.02 / 7.37 |
| `--line` | Línea | `#DDE5EC` | — | `#22303C` | — |
| `--control` | Borde de control (≥3) | `#7F8C98` | 3.22 / 3.44 | `#5C6C7A` | 3.53 / 3.24 |
| `--accent` | Marca / enlaces | `#0B5FA5` | 6.16 / 6.57 | `#7CC4FF` | 10.19 / 9.36 |
| `--on-accent` | Texto de botón | `#FFFFFF` | 6.57 sobre marca | `#0A1016` | 10.19 sobre marca |
| `--ok` | OK | `#0F6E5A` | 5.79 / 6.18 | `#5FD3B4` | 10.43 / 9.58 |
| `--unk` | No consta | `#7A5A00` | 5.98 / 6.38 | `#E5C062` | 10.97 / 10.07 |
| `--bad` | Bloqueador | `#B4233C` | 6.07 / 6.47 | `#FF8A9C` | 8.53 / 7.83 |
| `--chg` | Cambio | `#4B3FC0` | 7.10 / 7.58 | `#AFA6FF` | 8.85 / 8.12 |
| `--seal-bg` | Fondo del sello | `#FFFFFF` | marca encima: 6.57 | `#121A22` | marca encima: 9.36 |
| `--h-text` | Modalidad text (gráfico) | `#3456D1` | 5.79 | `#7E97FF` | 7.06 |
| `--h-vision` | Modalidad vision (gráfico) | `#0E8CA6` | 3.70 | `#3FC7E0` | 9.52 |
| `--h-audio` | Modalidad audio (gráfico) | `#7A5CD6` | 4.55 | `#A994FF` | 7.62 |
| `--h-embeddings` | Modalidad embeddings (gráfico) | `#12806A` | 4.56 | `#45C2A2` | 8.64 |
| `--h-image` | Modalidad image (gráfico) | `#A0479E` | 5.06 | `#D98BD6` | 7.84 |
| `--h-ocr` | Modalidad ocr (gráfico) | `#56718A` | 4.77 | `#93AAC0` | 7.97 |
| `--h-rerank` | Modalidad rerank (gráfico) | `#1C79C9` | 4.25 | `#5AB0FF` | 8.27 |

```css
:root {
  --bg: #F5F8FA;
  --panel: #FFFFFF;
  --ink: #0D1720;
  --muted: #4E5D6B;
  --line: #DDE5EC;
  --control: #7F8C98;
  --accent: #0B5FA5;
  --on-accent: #FFFFFF;
  --ok: #0F6E5A;
  --unk: #7A5A00;
  --bad: #B4233C;
  --chg: #4B3FC0;
  --seal-bg: #FFFFFF;
  --h-text: #3456D1;
  --h-vision: #0E8CA6;
  --h-audio: #7A5CD6;
  --h-embeddings: #12806A;
  --h-image: #A0479E;
  --h-ocr: #56718A;
  --h-rerank: #1C79C9;
  --radius: 10px;
  --h1-weight: 300; --h1-stretch: 128%; --h1-transform: none; --h1-tracking: -.02em;
}
@media (prefers-color-scheme: dark) { :root:not([data-theme="light"]) {
  --bg: #0A1016;
  --panel: #121A22;
  --ink: #EAF2F8;
  --muted: #9AAAB8;
  --line: #22303C;
  --control: #5C6C7A;
  --accent: #7CC4FF;
  --on-accent: #0A1016;
  --ok: #5FD3B4;
  --unk: #E5C062;
  --bad: #FF8A9C;
  --chg: #AFA6FF;
  --seal-bg: #121A22;
  --h-text: #7E97FF;
  --h-vision: #3FC7E0;
  --h-audio: #A994FF;
  --h-embeddings: #45C2A2;
  --h-image: #D98BD6;
  --h-ocr: #93AAC0;
  --h-rerank: #5AB0FF;
  color-scheme: dark;
} }
:root[data-theme="dark"] { /* mismos valores oscuros */ }
```

### Parámetros del aura

```yaml
aura: barcode
viewBox: 100
frame: rect 94×94, radio 16, trazo 2.2 en --control
stripes: de y=12 a y=88; grosor ∈ {2,3,4,6,8}, separación 2–3 (seed)
modality: franjas agrupadas en bandas contiguas, una por modalidad
ongoing: franjas de 74 de ancho
trial: cada franja partida (dos tramos de 24, hueco central de 26)
not_stated: el marco pasa a --unk con dash "5 4"
stale_over_30d: saturate(.2)
```

### Parámetros del sello

```yaml
seal: double-rule
border: 4px double --accent (fila) / 6px double (página)
text: versalitas, tracking .09em; página en dos líneas "✓ VERIFIED" / "24 NOV 2026 · 7 SOURCES"
rotate: -3deg
font: DM Mono 500 11px / 13–17px
```

---

## Mi recomendación

**Favorita: H1-d · Señalética.** Es la que mejor sirve al diferencial: el mosaico **cuenta** las flags sin decir celda a celda (de 0 a 4), no solo avisa de que hay alguna, y el matasellos es el "receipt" más reconocible de las seis. Tiene el contraste más alto (rejilla de tinta 21:1), funciona a 16 px como favicon (una rejilla 4×4 sobrevive al reducirse mucho mejor que anillos o puntos) y su lenguaje (señalética suiza) lleva décadas sin envejecer. Riesgo: puede resultar fría o institucional si el negro domina; el amarillo señal y los bloques de color lo compensan.

**Segunda: H1-a · Mineral**, si Paco prefiere algo más cálido y sereno. Es la continuación más directa de H1 (anillos) con una paleta propia que no se parece a ningún SaaS.

**Combinaciones que merecen probarse** si ninguna convence entera: el mosaico de H1-d con la paleta Mineral de H1-a (identidad más cálida sin perder el conteo), o el sello ticket de H1-e sobre H1-d.

**Descartaría** H1-c (Pastel): la mancha orgánica es la forma más fechada y obliga a contornos para cumplir contraste. H1-b (Neon) es la más llamativa en oscuro, pero el tema por defecto es claro, y en claro pierde casi todo el neón.

## Impacto en la implantación

El trabajo paramétrico de la sesión cloud sigue valiendo: cambiar de variante es cambiar los **tokens** (tabla y bloque CSS de cada ficha) y la **función de dibujo** del aura y del sello (parámetros de cada ficha). Las seis usan las mismas entradas por proveedor: `slug` (semilla), `category`, `modalities`, `models_free.length` (solo H1-b), `last_verified` y las cuatro flags. Para el OG en SVG (`resvg`) todas son primitivas SVG simples (círculos, líneas, rectángulos, trayectos Bézier); el único cuidado es H1-c, que usa `mask` y `mix-blend-mode` (resvg soporta `mask`; el modo de fusión habría que sustituirlo por opacidad en el OG). El código de referencia está en el `<script>` de cada prototipo.
