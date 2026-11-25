# 03 · Direcciones visuales

> **Ronda 2 (25-11-2026):** Paco pidió más color y carácter. Las direcciones D, E, F y G, dos híbridos y la comparativa de las siete están en [05-direcciones-ronda-2.md](05-direcciones-ronda-2.md); la recomendación actualizada es el híbrido H1 (G + A).

Tres direcciones claramente distintas. Todas cumplen lo mismo: dos temas, contrastes WCAG AA (calculados con la fórmula de luminancia relativa de WCAG 2.x, la misma de `build.test.mjs`), un sistema de color semántico común, solo fuentes OFL y prototipo navegable con datos reales del repo (v2.14.2, 2026-11-24).

| | A · Receipts | B · Spectrum | C · Periodic |
|---|---|---|---|
| Idea | El ticket y el sello: prueba documental | Panel de instrumentos: cada modalidad, un color | Tabla periódica de APIs gratis |
| Tema principal | Claro (papel) | Oscuro | Claro, blanco puro |
| Prototipo (privado) | [claude.ai/artifact/AVRXqk2fh4RALfXv2iTf4L](https://claude.ai/artifact/AVRXqk2fh4RALfXv2iTf4L) | [claude.ai/artifact/Bor2VrcHFovFMCt1od2Cgg](https://claude.ai/artifact/Bor2VrcHFovFMCt1od2Cgg) | [claude.ai/artifact/2VFJw7DHjN7LaDkPm5TBEJ](https://claude.ai/artifact/2VFJw7DHjN7LaDkPm5TBEJ) |
| Fichero local | [prototipos/a-receipts.html](prototipos/a-receipts.html) | [prototipos/b-spectrum.html](prototipos/b-spectrum.html) | [prototipos/c-periodic.html](prototipos/c-periodic.html) |
| Encaje con el diferencial | ★★★ | ★★ | ★★ |
| Memorabilidad | ★★ | ★★ | ★★★ |
| Riesgo de envejecer | Bajo | Medio | Medio |
| Coste de implantación | Bajo-medio | Medio | Alto |

Los enlaces de Artifact son privados: solo los abre el dueño de la cuenta hasta que se compartan desde su menú Share.

---

## Sistema semántico común (vale para las tres)

Es la parte más importante y se puede implantar **antes** de elegir dirección: es lo que acaba con el "monocolor" de forma útil.

| Familia | Valores | Forma (nunca solo color, WCAG 1.4.1) |
|---|---|---|
| **Flags de producción** (estado triple) | sí/OK · no/bloqueador · no consta | `✓` borde continuo · `✕` borde continuo · `?` **borde discontinuo**. Orden fijo: Card · Phone · Commercial · Training |
| **Verificación** | verified · not stated · contradicted · unverified | Sello "✓ fecha · source" · "?" · "✕" · sin sello |
| **Frescura** (días desde `last_verified`) | ≤7 · 8–30 · 31–60 · 61–90 · >90 | Verde, verde, ámbar, ámbar y rojo, más el texto "Nd ago". Por encima de 90, aviso "past our 90-day promise" |
| **Tipo** | Ongoing · Trial · Programa | Etiqueta textual; el trial lleva la duración ("Trial · 30 days") |
| **Cambio** | material · editorial | Violeta (`--chg`) para lo material; lo editorial va en gris y agrupado |
| **Modalidades** | text · vision · audio · embeddings/rerank · image · OCR/docs | Un matiz por modalidad, siempre acompañado del nombre |

Tokens (nombres comunes; los valores dependen de la dirección): `--ok --unk --bad --chg --trial --m-text --m-vision --m-audio --m-emb --m-image --m-docs`.

---

## A · "Receipts" (recomendada)

**Concepto.** Papel, tinta y sellos de goma. La web es un libro de cuentas limpio; el color solo aparece cuando un **sello** certifica algo (verificado, no consta, cambio). El objeto de marca es el **ticket con borde troquelado** y el **sello ligeramente girado** "✓ 24 Nov · source". Es la traducción literal de *with receipts*.

**Logo / monograma.** Un ticket (rectángulo con el borde inferior en zigzag) con un check en negativo. Funciona a 16 px, en un color y en sello. Hereda la idea del `>_` (un objeto de dev) y le añade el significado.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 32 32"><path d="M7 3h18a2 2 0 0 1 2 2v24l-3.33-2-3.34 2-3.33-2-3.33 2-3.34-2L5 29V5a2 2 0 0 1 2-2z" fill="#16181C"/><path d="M10.5 15.5l4 4 7.5-8" fill="none" stroke="#F6F6F3" stroke-width="2.6" stroke-linecap="round" stroke-linejoin="round"/></svg>
```

Logotipo: "Free LLM API Hub" en Martian Mono 700 con ancho reducido (87,5) y tracking −2 %. Variante sello: el texto "VERIFIED · SOURCE · DATE" en anillo alrededor del ticket, para badges y el OG.

**Paleta y contraste** (texto sobre `--paper` / `--sheet`):

| Token | Claro | Ratio | Oscuro | Ratio |
|---|---|---|---|---|
| `--paper` / `--sheet` (fondos) | `#F6F6F3` / `#FFFFFF` | — | `#111214` / `#191A1D` | — |
| `--ink` texto | `#16181C` | 16.42 / 17.77 | `#EDEDE8` | 15.96 / 14.82 |
| `--ink-2` secundario | `#4D525B` | 7.25 / 7.85 | `#A5A8AF` | 7.87 / 7.31 |
| `--stamp` marca (azul tinta) | `#2D44D0` | 6.81 / 7.37 | `#94A3FF` | 7.98 / 7.41 |
| `--ok` | `#0E7438` | 5.43 / 5.88 | `#4FC77F` | 8.75 / 8.13 |
| `--unk` no consta | `#8A5700` | 5.63 / 6.10 | `#E8B653` | 10.04 / 9.32 |
| `--bad` | `#B3261A` | 6.04 / 6.54 | `#FF8070` | 7.65 / 7.10 |
| `--chg` cambio | `#6B3CC9` | 6.23 / 6.74 | `#BBA2FF` | 8.68 / 8.06 |
| `--trial` | `#0A6A75` | 5.82 / 6.30 | `#55C8D4` | 9.46 / 8.78 |
| `--m-image` | `#AE2468` | 5.96 / 6.46 | `#FF8CC0` | 8.71 / 8.09 |
| `--m-emb` | `#2F6F1C` | 5.69 / 6.16 | `#8FD46C` | 10.53 / 9.78 |
| `--m-docs` | `#8E4510` | 6.45 / 6.98 | `#F5A06A` | 9.03 / 8.38 |
| `--control` borde de control (1.4.11, ≥3:1) | `#8A8D93` | 3.33 sobre blanco | `#6E727B` | 3.61 / 3.89 |
| Botón primario (texto sobre `--stamp`) | blanco | 7.37 | `#111214` | 7.98 |

Text = `--stamp`, vision = `--trial`, audio = `--unk` (en la práctica, la modalidad va siempre con su etiqueta y nunca se confunde con el estado, porque el estado usa forma de sello o flag). Si Paco quiere más separación, el audio puede pasar a `#7A4C9E`.

**Tipografía** (todas SIL OFL 1.1, verificadas en `google/fonts/ofl/*/METADATA.pb` el 25-11-2026):
- Display y datos: **Martian Mono** (Evil Martians) 400, 500, 700 y 800, ejes `wdth` 87,5–100. Es una mono "de diseño", ancha y con carácter de impresora de tickets, muy distinta de JetBrains Mono.
- Texto: **Instrument Sans** 400, 500, 600 y 700.
- Código: se mantiene **JetBrains Mono** (ya autoalojada) o se pasa a Martian Mono 400. Recomendación: JetBrains Mono en `<pre>` por legibilidad.

**Iconografía.** Se conserva el sprite propio (16 px, trazo 1.4) y se redibujan cuatro glifos de flags con la variante "?" discontinua. Para huecos, **Lucide** (ISC, verificado en `lucide-icons/lucide/LICENSE`) en trazo 1.5, ajustado a 16 px.

**Ilustración y visualización de datos.** Sin ilustración figurativa. Los gráficos se dibujan como tickets: barras finas en tinta, el dato destacado en `--stamp` y totales con línea doble (convención contable). Las cifras siempre en tabulares.

**Movimiento.** Uno solo, con significado: el **sello se estampa** (escala 1.08 → 1 y opacidad 0 → 1 en 180 ms) cuando un filtro deja visibles las filas, y al copiar un snippet, "Copied" aparece como sello. Hover del sello: rotación −1,5° → 0°. Todo bajo `prefers-reduced-motion: no-preference`. Se elimina el cursor parpadeante.

**OG, social preview y banner del README.**
- OG de la home (1200×630, claro): ticket blanco sobre papel, "Free LLM APIs, with receipts." en Martian 800, fila de totales (providers · ongoing · 0 ads) y el ticket-logo arriba a la izquierda.
- OG de ficha: nombre del proveedor, **3 números grandes** de `free_limits` y el sello girado "✓ verified 24 Nov 2026" arriba a la derecha (resuelve Q12 de la auditoría).
- Social preview de GitHub (1280×640): igual que el OG de la home, con "github.com/pacocartones/free-llm-api-hub" en pie.
- Banner del README: `<picture>` claro/oscuro, ticket-logo + nombre + tagline "Every free tier, quoted and dated." Los badges de shields se recolorean a `--stamp` (`2D44D0`) y `--ok`.

**Riesgos.** (1) Puede leerse como "fintech" o "facturación" si se abusa del troquel: usarlo solo en la ficha y en los OG. (2) Las marcas de papel claro pueden verse sosas si se descuida el sello: el sello es obligatorio en cada vista. (3) Martian Mono es ancha: H1 y nombres largos ("Google Agent Platform Express") necesitan `wdth` 87,5 y prueba en 360 px.

---

## B · "Spectrum"

**Concepto.** Un panel de instrumentos. Oscuro por defecto, y **cada modalidad tiene un matiz**; la marca es el espectro completo. El objeto de marca es la **barra de espectro** de 3 px (bajo la cabecera, en el pie del OG y en el badge) y los medidores de modalidad y frescura en el hero. Es lo más cercano al registro de Linear o Raycast.

**Logo.** Un ecualizador de cuatro barras ascendentes en los colores de las modalidades, más un punto ("live"), sobre una tesela oscura. Forma corta del nombre: **freellm/hub**.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 32 32"><rect width="32" height="32" rx="9" fill="#181C33"/><rect x="7" y="16" width="3" height="9" rx="1.5" fill="#A594FF"/><rect x="12" y="12" width="3" height="13" rx="1.5" fill="#3FD0EE"/><rect x="17" y="8" width="3" height="17" rx="1.5" fill="#86E07F"/><rect x="22" y="11" width="3" height="14" rx="1.5" fill="#FFB547"/><circle cx="23.5" cy="6.5" r="1.8" fill="#FF7FB4"/></svg>
```

**Paleta y contraste** (sobre `--bg` / `--panel`):

| Token | Oscuro | Ratio | Claro | Ratio |
|---|---|---|---|---|
| Fondos | `#0A0C14` / `#121527` | — | `#F6F7FB` / `#FFFFFF` | — |
| `--fg` | `#E8EAF2` | 16.25 / 15.04 | `#0E1120` | 17.52 / 18.75 |
| `--muted` | `#9AA1B8` | 7.59 / 7.02 | `#4C5470` | 6.98 / 7.47 |
| `--accent` = `--m-text` | `#A594FF` | 7.70 / 7.12 | `#5B46E0` | 5.77 / 6.18 |
| `--m-vision` | `#3FD0EE` | 10.66 / 9.87 | `#00708F` | 5.28 / 5.65 |
| `--m-audio` | `#FFB547` | 11.11 / 10.28 | `#875700` | 5.78 / 6.19 |
| `--m-emb` | `#86E07F` | 12.07 / 11.17 | `#2E7629` | 5.25 / 5.62 |
| `--m-image` | `#FF7FB4` | 8.32 / 7.70 | `#B4236A` | 5.79 / 6.20 |
| `--m-docs` | `#FF9A5C` | 9.32 / 8.63 | `#A3470F` | 5.66 / 6.06 |
| `--ok` | `#5BD69A` | 10.72 / 9.92 | `#12784A` | 5.15 / 5.51 |
| `--unk` | `#FFC857` | 12.69 / 11.75 | `#875700` | 5.78 / 6.19 |
| `--bad` | `#FF6F6F` | 7.21 / 6.67 | `#C0262D` | 5.52 / 5.90 |
| `--chg` | `#6FB7FF` | 9.20 / 8.51 | `#1F5FC4` | 5.62 / 6.01 |
| `--control` | `#6A7290` | 3.80 sobre panel | `#8890A8` | 3.18 sobre blanco |
| Botón primario | `#0A0C14` sobre `#A594FF` | 7.70 | blanco sobre `#5B46E0` | 6.18 |

**Tipografía** (OFL 1.1, verificadas): **Bricolage Grotesque** 500, 700 y 800 (display, eje óptico 12–96), **Inter** 400, 500 y 600 (texto) y **JetBrains Mono** 400, 500 y 700 (datos; ya en el repo).

**Iconografía.** Sprite propio; para huecos, **Phosphor** (MIT, verificado en `phosphor-icons/core`) en peso Regular, que tiene más personalidad que Lucide y encaja con la grotesca.

**Ilustración y datos.** Sin ilustración: los datos *son* la ilustración. Barra apilada de modalidades, histograma de frescura, medidores de límites en la ficha y sparklines de cambios por mes. Cada serie, en su color de modalidad.

**Movimiento.** El punto "live" late (2,4 s) junto a "58 of 64 entries re-checked this week". Las barras de los medidores se rellenan al cargar (300 ms, una vez). Los cambios de pestaña de modalidad hacen un fundido del borde de la fila al color de su modalidad. Todo con `prefers-reduced-motion`.

**OG y README.** Fondo `#0A0C14` y barra de espectro al pie; titular en Bricolage 800. Banner del README oscuro con el ecualizador. Badges de shields en `A594FF`.

**Riesgos.** (1) **Riesgo alto de "SaaS genérico 2025"**: el oscuro con titular en degradado y glows está muy visto (es lo que la auditoría de modas pide evitar); hay que contenerlo. (2) Siete matices exigen disciplina: si un componente usa color sin modalidad, se rompe el sistema. (3) El oscuro por defecto empeora la legibilidad de tablas densas para parte del público, y el tráfico de Google llega sobre todo de día y en claro. (4) La forma corta "freellm/hub" puede confundirse con freellm.net.

---

## C · "Periodic"

**Concepto.** La **tabla periódica de las APIs gratis**. Cada proveedor es un elemento con símbolo de dos letras (Gq, Gm, Or…), número y color por modalidad principal. Estética suiza: blanco puro, negro, bloques de color planos y grotesca condensada en mayúsculas. Es la dirección más memorable y la más "poster".

**Logo.** Una tesela de elemento: "Fh" en grande, con el número de proveedores (64) en la esquina como "número atómico", en cobalto. El número se actualiza en cada release, lo que da una pequeña marca viva.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 32 32"><rect width="32" height="32" fill="#2349E6"/><text x="3" y="9" font-family="IBM Plex Mono" font-size="6" font-weight="600" fill="#FFF">64</text><text x="3" y="27" font-family="Archivo" font-size="16" font-weight="900" fill="#FFF">Fh</text></svg>
```

(En producción, el texto se convierte a trazado para no depender de la fuente).

**Paleta y contraste.** Los rellenos de tesela son fijos en ambos temas; el texto se elige por tesela.

| Tesela (modalidad) | Relleno | Texto encima | Ratio |
|---|---|---|---|
| Text | cobalto `#2349E6` | blanco | 6.63 |
| Embeddings/rerank | menta `#2BC48A` | `#111111` | 8.42 |
| Speech | sol `#FFC93C` | `#111111` | 12.29 |
| Image | tomate `#FF6A5C` | `#111111` | 6.72 (el tomate `#E0393F` con blanco da 4.35 y no pasa: descartado) |
| OCR/docs | uva `#7A3FD1` | blanco | 6.07 |

| Token de texto | Claro (sobre `#FFFFFF` / `#F2F3F5`) | Oscuro (sobre `#121212` / `#1D1D20`) |
|---|---|---|
| `--fg` | `#111111` 18.88 / 17.01 | `#F2F2F2` 16.73 / 15.02 |
| `--muted` | `#50545C` 7.60 / 6.84 | `#A9A9AF` 8.01 / 7.19 |
| `--t-cobalt` (enlaces) | `#2349E6` 6.63 / 5.97 | `#8AA2FF` 7.75 / 6.96 |
| `--t-mint` (sí) | `#0B7A52` 5.36 / 4.83 | `#4FD6A0` 10.22 / 9.18 |
| `--t-tomato` (no) | `#C8262C` 5.57 / 5.02 | `#FF7A6E` 7.37 / 6.61 |
| `--t-sun` (no consta) | `#7A5A00` 6.38 / 5.75 | `#FFD25E` 13.05 / 11.72 |
| `--t-grape` (cambio) | `#7A3FD1` 6.07 / 5.47 | `#C3A4FF` 8.99 / 8.07 |
| `--control` | `#8A8D93` 3.33 | `#6B6B72` 3.18 |

**Tipografía** (OFL 1.1, verificadas): **Archivo** variable (ancho 62–125, peso 400–900; display condensado al 62–75 % en 900, texto al 100 %) e **IBM Plex Mono** 400, 500 y 600 (datos).

**Iconografía.** **Tabler Icons** (MIT, verificado en `tabler/tabler-icons`) en trazo 2, que casa con el peso suizo; o el sprite propio engrosado a 2 px.

**Ilustración y datos.** La propia tabla periódica es la ilustración: home, OG, pegatinas y el póster "The Periodic Table of Free AI APIs — Q1 2027" (pieza de prensa muy compartible para el informe trimestral B2 de la auditoría). Gráficos en bloques planos, sin degradados.

**Movimiento.** Las teselas suben 3 px al pasar el ratón. Al filtrar, las teselas que no cumplen pierden saturación (no desaparecen), y así la tabla "responde" al filtro. Con `prefers-reduced-motion`, sin desplazamiento.

**OG y README.** OG negro partido: titular condensado a la izquierda y mosaico de teselas a la derecha. En la ficha, la tesela gigante del proveedor (como en el prototipo). README con el póster de la tabla como banner.

**Riesgos.** (1) **Símbolos de dos letras** para 64-70 proveedores: hay colisiones (Groq/Gladia, Cohere/Cerebras/Cloudflare) y cada alta exige decidir un símbolo (se puede generar y fijar en los datos). (2) La metáfora "tabla periódica" ya existe en otros nichos; es memorable pero no exclusiva. (3) Es la dirección con más cambio estructural (home nueva, OG nuevos) y no cabe entera antes de febrero. (4) La modalidad "principal" de un proveedor multimodal es una decisión editorial discutible.

---

## Recomendación

**A · Receipts como identidad, con el sistema de color de modalidades de B dentro.** Es la única dirección en la que la forma *es* el diferencial: el sello de fecha y fuente aparece en la tabla, la ficha, el OG, el widget y los badges, y ningún competidor puede copiarlo sin tener el dato detrás. Es clara por defecto (mejor para tablas densas y para el tráfico de búsqueda), barata de implantar sobre los tokens actuales y la que menos envejece. De **C** se puede rescatar el **póster de la tabla periódica** como pieza de campaña para Product Hunt y el informe trimestral, sin convertirlo en la interfaz.
