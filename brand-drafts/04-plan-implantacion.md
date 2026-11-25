# 04 · Plan de implantación (dirección A "Receipts" + modalidades)

**Restricciones que respeta:** nada se construye ni se prueba en el PC de Paco (sesiones en la nube o CI regeneran `site/`); ramas `feat|fix|docs|chore|refactor/<a-z0-9->` para pasar la política de commits; **menos PRs** (agrupar lo pequeño); todo como PR en borrador y los merges los decide Paco; commits sin trailers de IA en el hub. Objetivo: marca nueva en producción **antes del 31-01-2027**, para que la v2.16.0 de Product Hunt (febrero) salga ya con ella.

**Cruce con la auditoría paralela.** Varias PRs de marca absorben ítems ya priorizados allí: Q2 (hero compacto), Q12 (OG), Q13 (score), Q18 (emojis del selector), M6 (badge "receipt") y M10 (logo). Conviene que la sesión coordinadora no los lance por separado.

## Fase 0 · Decisión (Paco, 1 sesión)

- Elegir dirección (recomendada: A) y tagline (recomendada: "Free LLM APIs, with receipts.").
- Confirmar el nombre: se queda "Free LLM API Hub" y se añade símbolo.
- Decidir si el tema por defecto pasa a claro (recomendado) y si la cabecera deja de ser verde.

## Fase 1 · Cimientos sin cambio visible grande (dic., 2 PRs)

| PR | Rama | Contenido | Ficheros | Riesgo / pruebas |
|---|---|---|---|---|
| **1. Tokens semánticos** | `refactor/semantic-color-tokens` | Añadir `--ok --unk --bad --chg --trial --m-*` y `--control` a los dos temas en `styles.css`, **con los valores actuales** donde ya existan (`--green`→`--ok`, `--warn`→`--unk`, `--red`→`--bad`). Sustituir usos directos. Sin cambio visual. Extender el test de contraste (`build.test.mjs:3137`) para recorrer los tokens nuevos sobre `--bg`, `--panel` y `--panel-2`. | `site/styles.css`, `site/tables.css`, `scripts/build.test.mjs` | Bajo. El test de contraste protege el resto |
| **2. Estado triple con forma** | `feat/tri-state-flags` | Componente único `flag` (✓ / ✕ / ? con borde discontinuo) para Card · Phone · Commercial · Training en tabla y ficha, en orden fijo. Emojis del selector de modalidad sustituidos por chips con punto de color + `aria-hidden` (Q18). | `scripts/build.mjs`, `scripts/lib/rows.mjs`, `shared-rows.js`, `styles.css`, tests de explorador | Medio: toca el render de servidor y cliente (`shared-rows.js` es la fuente compartida) |

## Fase 2 · La identidad (ene., 3 PRs)

| PR | Rama | Contenido | Ficheros |
|---|---|---|---|
| **3. Paleta y tipografía A** | `feat/brand-receipts-theme` | Valores de A en los tokens (papel, tinta, `--stamp`), tema claro por defecto respetando `prefers-color-scheme`, cabecera en papel con línea de tinta (se elimina `--header-bar` verde y se actualiza el test de `build.test.mjs:2241`). Martian Mono 500/800 e Instrument Sans 400/600 **autoalojadas en woff2 con subset latino** junto a `site/fonts/` y su `OFL.txt` (una por familia). JetBrains Mono se queda solo para `pre`/`code`. Presupuesto: ≤ 90 KB de fuentes nuevas y `preload` solo para el peso del H1. | `styles.css`, `site/fonts/*`, plantilla `<head>` en `build.mjs`, `scripts/lighthouse-gate.mjs` (presupuesto, en CI) |
| **4. Símbolo y sello** | `feat/brand-receipt-mark` | Ticket-logo en el sprite (`#logo`), `favicon.svg` (sin animación), `icons.mjs` (PNG 32/192/512 y apple-touch, regenerados en la nube), `assets/logo-{light,dark,full}.svg`. Componente **sello "receipt"** (`✓ 24 Nov · source`, con `title` que muestra la cita) en la tabla y la ficha (M6). Animación de estampado con `prefers-reduced-motion`. | `build.mjs` (SPRITE), `scripts/icons.mjs`, `site/favicon.svg`, `assets/`, `styles.css` |
| **5. Hero, ficha y score** | `feat/brand-home-and-provider` | Hero alineado a la izquierda con el ticket de totales (Q2), sin logo repetido ni cursor; ficha con bloque de límites grande, cita destacada y "Get a free key" (cuando exista `keys_url`, M2); score como "#1 of 64" con barra de 6 partes (Q13). | `build.mjs`, `scripts/lib/provider-sections.mjs`, `styles.css`, tests de ficha y home |

## Fase 3 · Fuera de la web (ene., 1-2 PRs + tareas manuales)

| PR / tarea | Rama | Contenido |
|---|---|---|
| **6. OG unificados** | `feat/og-receipts` | Reescribir `scripts/lib/og.mjs` y `site/og.svg` en tema claro, nombre sin kebab, 3 cifras de `free_limits` y sello de fecha en la ficha (Q12). Regenerar con `check-og` y su manifest en la nube. |
| **7. README y badges** | `docs/readme-brand` | Banner `<picture>` nuevo, badges de shields recoloreados (`2D44D0`/`0E7438`), sin emojis en los enlaces principales, tagline y descriptor ("Every free tier, quoted and dated."), `badge-svg.mjs` con el sello. Se puede juntar con la PR 6 por la regla de menos PRs. |
| Manual (Paco) | — | Subir el **social preview de GitHub** (1280×640 PNG generado en la PR 6) en *Settings → Social preview*, actualizar la descripción del repo con el descriptor y cambiar el avatar de la organización o el perfil si se quiere el símbolo. |
| Manual (Paco) | — | Recurso de Product Hunt: galería de 3-5 imágenes con la plantilla OG, logo 240×240. |

## Fase 4 · Pulido y comunidad (feb. en adelante)

- Póster "Periodic Table of Free AI APIs" (rescatado de C) para Product Hunt y el informe trimestral.
- Página `/brand/` o sección en `/press/` (M11) con logos, colores, tipografías y reglas de uso, en CC BY 4.0 para los assets y MIT para el código.
- Widget por proveedor (M8) con el sello.

## Good first issues (sacados de las fases anteriores)

| GFI | Por qué es apto | Depende de |
|---|---|---|
| Sustituir los emojis del selector de modalidad por chips con punto de color | Local, con test existente | PR 1 |
| Recolorear los badges de shields del README a los tokens nuevos | Solo Markdown | PR 3 |
| Añadir `aria-label` descriptivo a cada grupo de flags ("no card; phone not stated…") | Patrón repetible, con test | PR 2 |
| Redibujar los 4 iconos de flag con la variante "?" discontinua en el sprite (16 px, trazo 1.4) | Pequeño y visual, sin lógica | PR 2 |
| Documentar los tokens de color en `docs/brand.md` con su ratio de contraste | Documentación | PR 3 |
| Crear `docs/voice.md` con las reglas de voz y los ejemplos de microcopy de [02](02-estrategia.md) | Documentación | Fase 0 |
| Plantilla de social card para el informe mensual (SVG con variables) | Aislado, sin build | PR 6 |

## Calendario orientativo

| Semana | Entrega |
|---|---|
| 1-5 dic. | Fase 0 (decisión) · PR 1 |
| 8-19 dic. | PR 2 · GFIs de la fase 1 publicados |
| 5-16 ene. | PR 3 y PR 4 (pueden ir en paralelo en sesiones distintas: tocan ficheros diferentes salvo `styles.css`; mejor en serie) |
| 19-30 ene. | PR 5 · PR 6+7 · tareas manuales de GitHub |
| feb. | v2.16.0 + Product Hunt con la marca nueva |

## Riesgos de implantación

- **Tests de contraste fijados a valores** (`build.test.mjs:2241` comprueba el verde de la cabecera): hay que reescribirlos en la PR 3, no desactivarlos.
- **Peso de las fuentes**: dos familias nuevas. Subset latino y dos pesos por familia; verificar con el gate de Lighthouse en CI, nunca en local.
- **Caché**: `styles.css` con `max-age=600` (ver PERF): el cambio se verá mezclado durante unos minutos tras el deploy. Conviene versionar la URL del CSS en la PR 3.
- **Coherencia SEO**: no cambiar `<title>`, URLs ni H1 de las fichas en las PRs de marca, salvo lo ya planificado en P1, para no mezclar efectos en GSC.
