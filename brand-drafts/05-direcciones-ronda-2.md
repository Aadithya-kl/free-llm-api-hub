# 05 · Direcciones visuales, ronda 2 (D, E, F, G + híbridos)

**Encargo (Paco, vía coordinador, 25-11-2026).** Después de ver A, B y C pide "más": la web actual es "muy monocolor", "falta variedad, falta una esencia propia", tiene que ser "mucho más moderna" y "parece hecha hace 2 años". Esta ronda añade cuatro direcciones decididamente multicolores y con carácter, una con mascota (D) y otra con sistema ilustrativo propio (E), más dos híbridos. Todas conectan con el diferencial (cita + fecha + fuente, "dice lo que no sabe") y pasan WCAG AA en claro y oscuro.

Mismo método que en [03](03-direcciones.md): contrastes con la fórmula de luminancia relativa de WCAG 2.x (la de `build.test.mjs`), fuentes con licencia comprobada en `google/fonts/ofl/*/METADATA.pb` el 25-11-2026 (todas **SIL OFL 1.1**) y datos reales del repo (v2.14.2, 2026-11-24, 64 proveedores). El sistema semántico común de 03 (estado triple ✓ / ✕ / ? con borde discontinuo, frescura, modalidades) se mantiene en todas: el color nunca va solo.

| | Prototipo (Artifact privado) | Fichero local |
|---|---|---|
| D · Tick (mascota) | [claude.ai/artifact/Kt2pSCoix2z4YUNjEJ1Gft](https://claude.ai/artifact/Kt2pSCoix2z4YUNjEJ1Gft) | [prototipos/d-tick.html](prototipos/d-tick.html) |
| E · Riso (sistema ilustrativo) | [claude.ai/artifact/QXUnXMKyg8CEtuBdj372h7](https://claude.ai/artifact/QXUnXMKyg8CEtuBdj372h7) | [prototipos/e-riso.html](prototipos/e-riso.html) |
| F · Aurora Bento | [claude.ai/artifact/XVNU1dcoaog4m8t5CySgft](https://claude.ai/artifact/XVNU1dcoaog4m8t5CySgft) | [prototipos/f-aurora-bento.html](prototipos/f-aurora-bento.html) |
| G · Fingerprint (arte generativo con datos) | [claude.ai/artifact/MHoc38oSUeWR92Ua8TSVAj](https://claude.ai/artifact/MHoc38oSUeWR92Ua8TSVAj) | [prototipos/g-fingerprint.html](prototipos/g-fingerprint.html) |

Los enlaces son privados: solo los abre el dueño de la cuenta hasta que se compartan desde el menú Share de cada página.

Un dato nuevo, calculado para esta ronda, alimenta a F y G: **110 de las 256 flags de producción (43 %) son "not stated"**, y 55 de los 64 proveedores tienen al menos una. Es la mejor prueba numérica de "dice lo que no sabe", y ningún competidor puede enseñarla.

---

## D · "Tick" — mascota

**Concepto.** La marca tiene un personaje: **Tick**, un ticket de compra con ojos, mofletes y un sello en la mano. *Tick reads the fine print so you don't have to.* Es la versión cálida de "with receipts": el mismo concepto que A, pero con alguien que lo hace. Interfaz en **bento de bloques de color caramelo** con esquinas muy redondeadas.

**Por qué conecta con el diferencial.** Los **estados de ánimo de Tick son estados del dato**: sonriente = verificado, ceja levantada con "?" = no consta, ojos cerrados con "z" = hay que volver a comprobarlo (más de 90 días). La mascota enseña el sistema semántico sin leer ninguna leyenda.

**Logo.** Tick de frente (busto) a 28-32 px; a 16 px, solo el contorno del ticket con dos puntos (ojos). Personaje original dibujado para el prototipo (SVG propio, sin recursos de terceros).

**Paleta.** Rellenos de marca (fijos en los dos temas, siempre con texto `#1B1530` encima):

| Relleno | Hex | Texto `#1B1530` encima |
|---|---|---|
| Naranja | `#FF8A3D` | 7.48 |
| Chicle | `#FF7EB6` | 7.45 |
| Cielo | `#5CC8FF` | 9.33 |
| Lima | `#B8F15A` | 13.18 |
| Lila | `#B69CFF` | 7.68 |

Tokens de texto (sobre fondo / panel):

| Token | Claro | Ratio | Oscuro | Ratio |
|---|---|---|---|---|
| Fondos | `#F7F5FF` / `#FFFFFF` | — | `#16122A` / `#211C3B` | — |
| `--ink` | `#1B1530` | 16.26 / 17.55 | `#F4F0FF` | 16.25 / 14.49 |
| `--muted` | `#554C70` | 7.33 / 7.91 | `#B7AED6` | 8.70 / 7.76 |
| `--ok` (lima) | `#3F6B00` | 5.87 / 6.34 | `#B8F15A` | 13.66 / 12.19 |
| `--unk` (naranja) | `#A84300` | 5.61 / 6.06 | `#FF8A3D` | 7.76 / 6.92 |
| `--bad` | `#C0262D` | 5.47 / 5.90 | `#FF7A85` | 7.26 / 6.47 |
| enlace / lila | `#6A3FD0` | 6.02 / 6.49 | `#B69CFF` | 7.96 / 7.10 |
| cielo (texto) | `#00699E` | 5.54 / 5.98 | `#5CC8FF` | 9.67 / 8.63 |
| chicle (texto) | `#B0246A` | 5.89 / 6.35 | `#FF7EB6` | 7.72 / 6.89 |
| `--control` | `#8B83A8` | 3.55 sobre blanco | `#6F6795` | 3.13 sobre panel |

**Tipografía.** **Unbounded** 500/700/900 (display redondeada y expandida), **Onest** 400-700 (texto) y **DM Mono** 400/500 (datos).

**Iconografía.** Phosphor (MIT) en peso Bold, que casa con las formas redondas; o el sprite propio engrosado.

**Ilustración y datos.** Tick en 6-8 poses reutilizables: hero, vacío de filtros, 404, éxito al copiar, "past our 90-day promise", informe mensual y Product Hunt. Los datos van en tarjetas de color grandes (cifras en Unbounded 900).

**Movimiento.** Tick "flota" suavemente en el hero (3,2 s) y estampa el sello al copiar un snippet; las tarjetas se inclinan 0,4° al pasar el ratón. Todo bajo `prefers-reduced-motion`.

**OG / README.** Bloque de color plano con Tick a la derecha y el titular en Unbounded; en la ficha, color según modalidad y Tick con la cara del estado de verificación. Banner del README con Tick sellando.

| Recurso | ¿Moda o dura? |
|---|---|
| Mascota | **Dura** si el personaje es bueno (Octocat, el pato de DuckDuckGo, Clippy para bien y para mal). Es la vía más rápida a la "esencia propia". |
| Bento de colores caramelo | Moda 2024-2026. Envejecerá en 2-3 años; se puede sustituir sin tocar a Tick. |
| Unbounded / tipografía expandida | Moda reciente (2024-26), aguanta mejor que el bento. |

**Riesgos.** (1) Un personaje simpático puede **restar seriedad** a un producto cuyo valor es la confianza: Tick nunca debe aparecer junto a un dato negativo con cara de broma. (2) Hace falta **un ilustrador**: cada pose nueva es trabajo de diseño, no de código. (3) Personajes "ticket con cara" pueden existir ya en fintech; antes de fijarlo, conviene una búsqueda de marcas registradas (no hecha aquí). (4) Las tarjetas caramelo comparten estética con muchas apps de consumo.

---

## E · "Riso" — sistema ilustrativo propio

**Concepto.** Un fanzine impreso en risografía. Cada **modalidad es una forma plana en una tinta de riso** (bocadillo azul = texto, ojo rosa = visión, ondas naranjas = voz, nube de puntos verde = embeddings, sol y montaña amarillos = imagen, hoja doblada rosa = documentos). La ilustración de cada proveedor es la **sobreimpresión de sus propias formas**, con un leve desregistro, así que el dibujo de una ficha *dice* qué sabe hacer ese proveedor. El sello "✓ Received 24 Nov · source" se imprime como un tampón redondo.

**Por qué es un sistema y no un dibujo.** Las ilustraciones se **generan a partir de `modalities`** en el build (son SVG con `mix-blend-mode: multiply` en claro y `screen` en oscuro). Un proveedor nuevo tiene su ilustración el mismo día, sin ilustrador.

**Logo.** Un cuadrado azul y un círculo rosa sobreimpresos con un check en tinta: "dos planchas que coinciden" = el dato y su fuente.

**Paleta.** Las tintas siguen los colores estándar de riso (azul, rosa fluorescente, amarillo, verde y naranja). Como relleno van sin texto encima o con texto oscuro; para texto se usan variantes oscurecidas:

| Token | Claro (sobre `#F6F8FA` / `#FFFFFF`) | Oscuro (sobre `#0B1B33` / `#13284A`) |
|---|---|---|
| `--ink` | `#0B1B33` 16.18 / 17.23 | `#F6F8FA` 16.18 / 13.79 |
| `--muted` | `#4A5568` 7.07 / 7.53 | `#AEB9CC` 8.71 / 7.42 |
| azul (enlaces) | `#0068A8` 5.56 / 5.92 | `#5BB8F0` 7.84 / 6.68 |
| rosa (no) | `#C4157D` 5.26 / 5.60 | `#FF6EC0` 6.76 / 5.76 |
| verde (sí) | `#00733F` 5.60 / 5.96 | `#3FD08A` 8.70 / 7.41 |
| naranja (no consta) | `#B23E00` 5.51 / 5.86 | `#FF8A57` 7.40 / 6.31 |
| amarillo (texto) | `#7A6400` 5.40 / 5.75 | `#FFE800` 13.78 / 11.74 |
| `--control` | `#7D8899` 3.59 sobre blanco | `#5E7499` 3.10 sobre panel |
| Botón: blanco sobre azul riso `#0078BF` | 4.73 | (igual en oscuro) |

El azul riso `#0078BF` con texto oscuro da 3.64 y **no pasa**: los botones azules llevan texto blanco. El rosa y el verde riso con blanco dan 3.09 y 3.07: tampoco se usan con texto blanco.

**Tipografía.** **Anybody** (variable, ancho 50-150, peso 400-900), condensada al 62 % en mayúsculas para titulares, y **Figtree** 400-700 para el texto.

**Iconografía.** Las seis formas de modalidad **son** los iconos grandes; para la interfaz, Tabler (MIT) en trazo 2.

**Datos.** Gráficos en tintas planas sobreimpresas (barras que se solapan en multiply), sin degradados.

**Movimiento.** Las tarjetas se desplazan con una sombra dura de color (rosa → azul al pasar el ratón), como un papel que se levanta. Al cargar, las formas del hero pueden "imprimirse" una por plancha (150 ms cada una).

**OG / README.** Titular condensado a la izquierda y la sobreimpresión de modalidades a la derecha; en la ficha, el dibujo de ese proveedor. Banner del README con todas las formas.

| Recurso | ¿Moda o dura? |
|---|---|
| Estética riso (sobreimpresión, desregistro) | Moda editorial 2019-2024, ya madura; puede leerse como "indie de 2021". Lo que **dura** es el *sistema* (forma = modalidad). |
| Sombra dura de color (neo-brutalismo) | Moda 2023-25, de las que antes envejecen. Prescindible. |
| Grotesca condensada en mayúsculas | Clásico suizo; dura. |

**Riesgos.** (1) `mix-blend-mode` en el OG exige rasterizar en el build (`resvg` soporta `mix-blend-mode` en SVG, pero hay que probarlo en CI). (2) Con 4 o más modalidades la sobreimpresión se vuelve una mancha (Cloudflare, Gemini): limitar a 3 formas y añadir "+1". (3) El neo-brutalismo de las tarjetas puede parecer "plantilla de Gumroad".

---

## F · "Aurora Bento" — los datos como protagonista

**Concepto.** La portada **es un tablero vivo del dataset**: celdas bento de cristal esmerilado sobre una aurora hecha con los colores de las modalidades. Cada celda es un dato real: frescura (58/64 comprobados esta semana, en anillo), proveedores, sin tarjeta (51), **"What the docs don't say: 110 of 256 flags"** con barra rayada, reparto por modalidad, **"Latest receipts"** (feed de verificaciones con fecha) y **"Not free"** (OpenAI, Anthropic, xAI… tachados, del README del 20-11-2026). La ficha es otro bento: un cubo de límites con medidor, flags y cita.

**Logo.** Tres teselas redondeadas (degradado violeta-rosa-ámbar, cian y verde) y la cuarta es un check: "el cuarto cuadro es la verificación".

**Paleta.**

| Token | Oscuro (sobre `#07070C` / `#12131C`) | Claro (sobre `#F4F5FA` / `#FFFFFF`) |
|---|---|---|
| `--ink` | `#F2F3F8` 18.14 / 16.69 | `#0C0D14` 17.80 / 19.39 |
| `--muted` | `#A0A3B5` 8.04 / 7.40 | `#4B4F63` 7.42 / 8.08 |
| violeta (marca) | `#9F87FF` 7.07 / 6.50 | `#5B3FE0` 5.97 / 6.50 |
| cian | `#2FD8FF` 11.86 / 10.91 | `#006F8E` 5.26 / 5.73 |
| rosa | `#FF6EB4` 7.79 / 7.17 | `#B5206E` 5.68 / 6.18 |
| ámbar (no consta) | `#FFB020` 10.99 / 10.11 | `#8A5600` 5.65 / 6.16 |
| verde (sí) | `#3DDC97` 11.37 / 10.46 | `#0F7848` 5.08 / 5.53 |
| `--bad` | `#FF6B6B` 7.24 / 6.66 | `#C0262D` 5.42 / 5.90 |
| `--control` | `#5F6380` 3.16 sobre panel | `#8A8EA3` 3.24 sobre blanco |
| Botón | `#07070C` sobre `#9F87FF`: 7.07 | blanco sobre `#5B3FE0`: 6.50 |

Los colores de la aurora (`#7C5CFF`, `#00D1FF`, `#FF5CA8`, `#FFB020`, `#3DDC97`) solo son fondo difuminado, nunca texto. Las celdas tienen un relleno del 72 % para que el contraste del texto no dependa de lo que haya detrás; el texto en degradado ("with receipts.") usa los tokens de texto, cuyos tres extremos pasan 5:1.

**Tipografía.** **Geist** 400-800 y **Geist Mono** 400-600 (las dos de Vercel, OFL). Una sola familia con su mono: es la apuesta más "herramienta de 2026" y la más neutra.

**Iconografía.** Lucide (ISC).

**Datos.** Es la dirección más rica en visualización: anillos, barras apiladas, medidores y feed. Cada celda puede ser un componente reutilizable en `/quality/` y en el informe mensual.

**Movimiento.** La aurora deriva muy despacio (24 s, alterna); los anillos se rellenan al cargar; las cifras cuentan hasta su valor. Todo bajo `prefers-reduced-motion`.

**OG / README.** Aurora en oscuro con el titular en Geist 800; la ficha, con las cifras y "✓ verified 24 Nov 2026".

| Recurso | ¿Moda o dura? |
|---|---|
| Bento grid | Moda 2023-2025 (Apple, Linear, Vercel). Aguanta si **cada celda es un dato**; si son tarjetas de marketing, ya es cliché. |
| Glassmorphism (`backdrop-filter`) | Moda que vuelve cada pocos años (iOS 7, Big Sur, "Liquid Glass" de Apple en 2025). Coste de rendimiento en móvil. **Pasajera.** |
| Aurora / mesh gradient | **Pasajera** (2022-2025) y hoy muy asociada a la estética de la IA genérica. |
| Texto en degradado | Pasajero, con riesgo de contraste. |
| Geist | Dura como tipografía, pero identifica con Vercel. |

**Riesgos.** (1) **Es la más "2026" y la menos propia**: aurora + bento + cristal + Geist es exactamente lo que hacen cientos de startups de IA, y eso choca con "esencia propia". (2) `backdrop-filter` y el desenfoque de 30 px penalizan el LCP en móviles de gama baja (verificar con el gate de Lighthouse en CI). (3) Envejecerá la primera de las siete.

---

## G · "Fingerprint" — identidad generativa a partir del dato

**Concepto.** **Cada proveedor tiene un "aura" única, calculada a partir de sus propios datos**: sectores cónicos con el color de cada modalidad; disco lleno si el free tier es continuo y anillo si es trial; **borde discontinuo si su documentación deja flags sin decir**; desaturada si la última comprobación tiene más de 30 días. La portada es el **campo de las 64 auras**, que funciona a la vez como ilustración, mapa del dataset y logo vivo. El titular usa tipografía variable que "respira" (ancho y peso).

**Por qué conecta con el diferencial.** La identidad **es** el dato, incluido lo que no se sabe: el borde discontinuo hace visible el "not stated" en cada proveedor y en el logo de cada OG. Ningún competidor puede copiarlo sin tener el dataset detrás. Es el mismo principio que las identidades generativas clásicas (MIT Media Lab 2011, Casa da Música).

**Logo.** El aura del propio hub: las seis modalidades en disco lleno, sin borde discontinuo. En favicon, a 16 px, un círculo cónico de 4 sectores. Cada proveedor tiene además su **favicon/avatar automático** (su aura).

**Paleta.** Los matices de las modalidades (`#7C5CFF` texto, `#00C2E0` visión, `#FFA31A` audio, `#2BC48A` embeddings, `#FF4F8B` imagen, `#FF7A3D` OCR, `#4C8DFF` rerank) solo son relleno gráfico, nunca texto. El texto usa:

| Token | Claro (sobre `#FAFAFA` / `#FFFFFF`) | Oscuro (sobre `#0E0E11` / `#18181D`) |
|---|---|---|
| `--ink` | `#0F0F12` 18.33 / 19.14 | `#F3F3F5` 17.39 / 15.96 |
| `--muted` | `#55565E` 6.99 / 7.29 | `#A6A7B0` 8.05 / 7.39 |
| `--accent` (marca, magenta) | `#C2255C` 5.42 / 5.66 | `#FF6B9A` 7.18 / 6.59 |
| `--ok` | `#1B7A44` 5.14 / 5.37 | `#4FD08A` 9.84 / 9.03 |
| `--unk` | `#8A5700` 5.84 / 6.10 | `#F0BA4E` 10.87 / 9.97 |
| `--bad` | `#C0262D` 5.66 / 5.90 | `#FF7A7A` 7.63 / 7.01 |
| `--chg` | `#3D5AFE` 4.92 / 5.13 | `#8C9EFF` 7.76 / 7.12 |
| `--control` | `#8A8B93` 3.39 sobre blanco | `#64656E` 3.06 sobre panel |
| Botón | blanco sobre `#C2255C` (≈5.7) | `#0E0E11` sobre `#FF6B9A`: 7.18 |

(El primer magenta probado, `#D6336C`, daba 4.42 y se descartó.) El borde discontinuo del aura usa `--unk`, que pasa 3:1 como elemento gráfico en los dos temas.

**Tipografía.** **Roboto Flex** (variable con 13 ejes: `wdth` 25-151, `wght` 100-1000, `opsz`…) para display y texto, y **DM Mono** 400/500 para los datos.

**Iconografía.** Lucide (ISC) en trazo 1.75; las auras sustituyen a los avatares y los logos de terceros (que además evitan problemas de marca registrada al no usar logos de proveedores).

**Datos.** Además del campo de auras, la tabla de comparación puede ordenar y agrupar auras (por modalidad, por frescura): la visualización y la identidad son lo mismo.

**Movimiento.** La palabra clave del titular cambia de ancho y peso en bucle lento (5 s); las auras crecen un 15 % al pasar el ratón; al filtrar, las que no cumplen se desaturan. Todo bajo `prefers-reduced-motion`.

**OG / README.** OG oscuro con el titular a la izquierda y 16 auras en cuadrícula; en la ficha, el aura grande del proveedor junto a sus cifras. Banner del README: el campo completo de auras, regenerado en cada release (el banner cambia con el dataset).

| Recurso | ¿Moda o dura? |
|---|---|
| Identidad generativa basada en datos | **Dura.** Lleva 15 años funcionando en identidades culturales y se renueva sola con el dato. |
| Tipografía variable | **Dura** como tecnología. El texto que "respira" en bucle es moda: dejarlo solo en el hero, o solo al pasar el ratón. |
| Degradados cónicos | Estéticos de 2024-26, pero aquí codifican información, así que no son decoración. |

**Riesgos.** (1) **Hay que aprender a leerla**: sin leyenda, un aura es un círculo bonito. La leyenda debe estar siempre cerca (portada, ficha, OG con texto). (2) **Daltonismo**: los sectores se distinguen por color; la modalidad debe ir siempre también en texto (ya lo hace la ficha) y el estado nunca depende solo del color (anillo, borde discontinuo y desaturación son formas). (3) SVG no tiene degradado cónico nativo: para los OG, `og.mjs` tendría que dibujar sectores como arcos SVG (factible con `resvg`). (4) 64 círculos parecidos pueden verse como "confeti" si la paleta no se disciplina.

---

## Híbridos

### H1 · "Fingerprint + Receipts" (G + A) — recomendado

Las **auras de G** como identidad visual y multicolor (portada, avatar de cada proveedor, OG y banner) más el **sello "receipt" de A** como firma de la verificación (`✓ 24 Nov · source`, girado, en la tabla, la ficha y el widget). Fondo blanco o casi negro (no papel), tipografía variable Roboto Flex con datos en DM Mono, y el sistema semántico común. El aura dice *qué es* el proveedor; el sello dice *cómo lo sabemos*.

### H2 · "Riso + Tick" (E + D)

La mascota Tick dibujada **en tintas de riso**, viviendo dentro del sistema de formas de E: Tick en el hero, los 404 y los estados vacíos, y las sobreimpresiones de modalidades en tarjetas y fichas. Es la combinación con más personalidad y la más divertida para Product Hunt, pero suma los riesgos de las dos (seriedad, ilustrador, estética indie).

Variante barata de cualquiera de las dos: **Tick como personaje secundario** (solo 404, vacíos, "past our 90-day promise" y el lanzamiento de Product Hunt), sin que sea la marca principal.

---

## Comparativa de las siete (y los dos híbridos)

Escala ★ (1-3); en "riesgo de envejecer" y "coste", más estrellas = peor.

| Dirección | Multicolor | Se siente 2026 | Esencia propia | Conecta con "receipts" | Memorable | Riesgo de envejecer | Coste de implantación | Notas de accesibilidad |
|---|---|---|---|---|---|---|---|---|
| A · Receipts | ★ | ★★ | ★★★ | ★★★ | ★★ | ★ | ★ | La más sobria; Paco la considera poco colorida |
| B · Spectrum | ★★★ | ★★ | ★ | ★★ | ★★ | ★★ | ★★ | Oscuro por defecto |
| C · Periodic | ★★★ | ★★ | ★★ | ★★ | ★★★ | ★★ | ★★★ | Símbolos de dos letras con colisiones |
| D · Tick | ★★★ | ★★★ | ★★★ | ★★★ | ★★★ | ★★ | ★★★ (ilustrador) | El tono simpático puede restar confianza |
| E · Riso | ★★★ | ★★ | ★★★ | ★★ | ★★★ | ★★ | ★★ | Tintas riso con texto blanco descartadas |
| F · Aurora Bento | ★★★ | ★★★ | ★ | ★★★ | ★ | ★★★ | ★★ | `backdrop-filter` y rendimiento en móvil |
| G · Fingerprint | ★★★ | ★★★ | ★★★ | ★★★ | ★★★ | ★ | ★★ | Leyenda obligatoria; color nunca solo |
| **H1 · G + A** | ★★★ | ★★★ | ★★★ | ★★★ | ★★★ | ★ | ★★ | Hereda las salvaguardas de A y G |
| H2 · E + D | ★★★ | ★★ | ★★★ | ★★★ | ★★★ | ★★ | ★★★ | Suma riesgos de D y E |

## Recomendación honesta

**H1 · Fingerprint + Receipts.** Es la única propuesta que cumple a la vez las cuatro cosas que pide Paco sin pagar el precio de una moda:

- **Multicolor con motivo.** Hay siete matices, pero cada uno significa una modalidad; no es decoración.
- **Esencia propia.** Nadie más puede tener estas auras porque salen de nuestro dataset, y el sello de A es la prueba visible del diferencial.
- **De 2026 sin fecha de caducidad.** La identidad generativa y la tipografía variable son técnicas duraderas; en F, en cambio, bento, cristal y aurora son las primeras que envejecerán.
- **Barata y escalable.** Las auras se calculan en el build (CSS para la web y arcos SVG para los OG), un proveedor nuevo tiene su identidad el mismo día y no hace falta ilustrador.

**Lo que haría con el resto:**

- **D (Tick)** es la que más "esencia" aporta de golpe y la más divertida para Product Hunt. Si Paco quiere personaje, lo recomiendo como **secundario** (404, vacíos, lanzamiento) encima de H1, y con un ilustrador para fijarlo, no como marca principal: en un producto de confianza, la mascota no debe estar junto a cada dato.
- **F** sirve como **cantera de componentes** (las celdas "What the docs don't say", "Latest receipts" y "Not free" son buenas ideas de contenido para la portada de cualquier dirección), pero no como identidad.
- **E** es la más bonita como sistema ilustrativo. Si a Paco le gusta más que G, H2 es una alternativa legítima, aunque más cara de mantener.

**Impacto en el plan.** El [plan de implantación](04-plan-implantacion.md) sirve casi igual para H1. Las PRs 1 (tokens semánticos) y 2 (estado triple con forma) son idénticas. En la PR 3 cambian la paleta (blanco o casi negro + matices de modalidad + magenta de marca) y la tipografía (Roboto Flex + DM Mono). La PR 4 añade `aura.mjs`: genera el CSS del aura por proveedor y los arcos SVG del OG, más su test.

**Decisiones de Paco:**
1. ¿H1 o alguna de las siete?
2. ¿Quiere a Tick como personaje secundario? (Si sí, encargar o abrir a la comunidad la ilustración definitiva y revisar marcas registradas).
3. ¿Tema por defecto claro o oscuro?
4. ¿Mantiene la tagline "Free LLM APIs, with receipts." o prefiere la de G, "Every free AI API has a fingerprint."?

---

## Galería y prototipos de los híbridos (añadido 25-11-2026)

- **Galería "Brand directions"** con las nueve opciones, sus capturas de portada y ficha, paletas, tipografía, notas de durabilidad y las taglines: [claude.ai/artifact/TcYMg614favBhKXc9PaDPT](https://claude.ai/artifact/TcYMg614favBhKXc9PaDPT) (fichero: [galeria/brand-directions.html](galeria/brand-directions.html); capturas en `galeria/img/`).
- **H1 · Fingerprint + Receipts:** [claude.ai/artifact/M1ToUWCJKtwk9FGTHD454w](https://claude.ai/artifact/M1ToUWCJKtwk9FGTHD454w) ([prototipos/h1-fingerprint-receipts.html](prototipos/h1-fingerprint-receipts.html)).
- **H2 · Riso + Tick:** [claude.ai/artifact/8yjDCktJ7ecZdgqZz9HXm4](https://claude.ai/artifact/8yjDCktJ7ecZdgqZz9HXm4) ([prototipos/h2-riso-tick.html](prototipos/h2-riso-tick.html)).
- Taglines nuevas: [06-taglines.md](06-taglines.md). Los prototipos de H1 y H2 ya usan dos de ellas ("Every limit quoted. Every quote dated." y "We read the docs. You ship the code.").
