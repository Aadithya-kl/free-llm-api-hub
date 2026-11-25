# 02 · Estrategia de marca: Free LLM API Hub

Los textos de marca van en inglés, que es el idioma del producto. La explicación va en español. La declaración de posicionamiento y el concepto "receipts" vienen de la auditoría paralela (§2.2); aquí se convierten en plataforma de marca.

## 1. Propósito

**Why we exist:** *So that anyone can build with AI without paying first — and without being misled about what "free" means.*

El hub no existe para listar APIs (eso lo hace cualquier awesome list), sino para que la palabra "free" vuelva a significar algo comprobable.

## 2. Audiencias

| Audiencia | Qué necesita | Qué la hace confiar |
|---|---|---|
| **Indie dev o estudiante** (núcleo, tráfico de "free LLM API") | Una API que funcione hoy, sin tarjeta, y un snippet listo | Un límite concreto y una fecha reciente |
| **Dev que va a producción** (side project con usuarios) | Saber si el uso comercial está permitido, si entrena con sus prompts y si el límite aguanta | Las **flags de producción** con cita literal |
| **Agentes de IA y herramientas** (LLMs que consultan `llms.txt` o la API JSON) | Datos legibles por máquina, estables y con esquema | JSON Schema, versión y licencia MIT |
| **Docentes, investigadores y periodistas** | Una fuente citable con historial | `CITATION.cff`, historial por campo e informe mensual |
| **Contribuidores** | Una tarea pequeña y clara | Good first issues y un proceso de verificación explícito |

## 3. Posicionamiento

> **For developers who need a free AI API they can actually ship on, Free LLM API Hub is the open, ad-free dataset that shows its receipts:** every limit and requirement is quoted from the provider's own docs, dated and re-checked within 90 days — and when a provider doesn't say, we say so.

**Categoría:** *verified dataset* (no "directorio" ni "lista"). **Contra quién:** las awesome lists (sin fecha ni fuente) y los directorios con anuncios (sin neutralidad).

## 4. Valor diferencial (los cinco "receipts")

| Pilar | En el producto hoy | Cómo se ve en la marca |
|---|---|---|
| **Quoted** | `field_checks`, "In the provider's words", `data_policy.quote` | La cita es un componente visual con firma: comillas, fuente y fecha. |
| **Dated** | `last_verified`, `checked` por campo y SLA de 90 días | Cada dato lleva su sello de fecha. La frescura tiene una escala de color propia. |
| **Says what it doesn't know** | Estado triple: sí / no / **no consta** (`source_silent`) | "No consta" tiene su propio color y forma (borde discontinuo y "?"), nunca gris neutro ni hueco. |
| **Production flags** | `card_required`, `phone_required`, `commercial_ok`, `data_policy.trains_on_prompts` | Cuatro flags fijas, siempre en el mismo orden (Card · Phone · Commercial · Training) y con la misma iconografía en tabla, ficha, OG, widget y badge. |
| **Machine-readable** | `providers.json`, CSV, JSON Schema, `llms.txt`, MIT | En la marca se nota con mono para los datos, URLs visibles y un bloque "Use the data" como elemento recurrente. |

Además: **sin anuncios ni afiliación; el dinero no cambia ningún score** (`/submit/`). Esto va en el pie de cada pieza ("0 paid placements").

## 5. Personalidad

| Es | No es |
|---|---|
| **Meticulous** (el inspector que enseña su libreta) | Pedante ni burocrático |
| **Candid** (dice "no consta" y "esto ya no es gratis") | Cínico ni alarmista |
| **Useful first** (snippet, límite, enlace a la clave) | Marketing, "revolutionary", "unlock" |
| **Open** (MIT, datos, proceso a la vista) | Corporativo ni anónimo: hay un mantenedor con nombre |
| **Dry humour, rarely** (404 "command not found") | Memes ni emojis de relleno |

Arquetipo: **el inspector o notario amable** — la persona del equipo que se lee la letra pequeña por ti.

## 6. Voz y tono

**Reglas.** (1) La cifra primero y el adjetivo después, o nunca. (2) Cita y fecha antes que la opinión. (3) "Not stated" antes que inventar. (4) Frases cortas, en activa, sin "unlock", "supercharge", "seamless" ni "revolutionary". (5) Llamar a las cosas como las llama quien usa la API ("free key", "rate limit"), no como las llama el esquema (`source_silent`). (6) Sin emojis como marcadores de sección.

El tono varía con el momento. Los ejemplos muestran el registro; las cifras de Gemini, del filtro vacío y de los 94 días son ilustrativas, no datos del dataset.

| Momento | Tono | Ejemplo |
|---|---|---|
| Hero | Seguro y concreto | **Free LLM APIs, with receipts.** |
| Fila de la tabla | Telegráfico | `30 RPM · 1K RPD · 200K tokens/day` · `✓ 24 Nov · source` |
| "No consta" | Neutral y transparente | **Not stated.** Groq's docs don't mention phone verification. *Checked 24 Nov 2026 — 3 pages read.* |
| Bloqueador | Directo, sin drama | **Card required.** Cerebras asks for a card before the $5 credit. |
| Retirada | Factual, con alternativa | **No longer free.** GitHub Models stopped its free tier on 30 Jul 2026. Similar options: Groq, OpenRouter. |
| Dato viejo | Responsable | This entry is 94 days old — past our 90-day promise. **Help re-check it →** |
| Vacío de filtros | Útil | No provider matches all 4 filters. Drop "No phone" to see 6. |
| Botón principal | Verbo + objeto | **Get a free key ↗** · **Copy snippet** · **Copied** |
| Contribución | Invitación concreta | **Spotted something out of date?** Fix it in 2 minutes — the form is pre-filled. |
| Pie | Principio | No ads. No affiliate links. Money never changes a score. |
| Error 404 | Humor seco | `command not found: /pricing` — try searching for a provider. |
| Social | Noticia con prueba | Gemini cut 2.5 Pro free requests from 100 to 50 a day. Source and date ↓ |

## 7. Arquitectura del nombre

| Opción | Pros | Contras | Veredicto |
|---|---|---|---|
| **A. "Free LLM API Hub" completo** (como ahora) | Coincide con el dominio y con la búsqueda principal; es descriptivo y ya tiene tracción en GSC y 129★ | Largo y genérico: se confunde con freellm.net, free-llm.com y freellm.site | **Se queda como nombre legal y SEO** |
| **B. Nombre corto nuevo** (p. ej. "Receipts", "Fineprint") | Memorable y registrable | Rompe el SEO y la tracción a dos meses de Product Hunt; "Receipts" está muy usado | No ahora |
| **C. Nombre completo + forma corta "freellm/hub"** | Se escribe como una ruta (dev-native), sirve para el handle, la cabecera móvil y el OG | Puede leerse como "freellm.net" si se descuida | Opcional (dirección B) |
| **D. Nombre completo + monograma/símbolo** | El símbolo da memorabilidad sin tocar el nombre: favicon, avatar, sello y badge | Hay que diseñar bien el símbolo | **Recomendada** |

**Recomendación: D.** Nombre "Free LLM API Hub" sin cambios. Se añade un **símbolo propio** que funciona solo (favicon, avatar de GitHub, sello de verificación) y un **nombre de componente**: el sello se llama **"receipt"** en la UI ("See the receipt"), con lo que el concepto se vuelve parte del vocabulario sin renombrar el producto. Escritura: siempre "Free LLM API Hub" en texto; nunca `free-llm-api-hub` fuera del nombre del repositorio (esto corrige el OG).

## 8. Taglines (5 opciones)

| # | Tagline | Para qué |
|---|---|---|
| 1 | **Free LLM APIs, with receipts.** | Hero, OG y Product Hunt (recomendada, alineada con la auditoría) |
| 2 | **Every free tier, quoted and dated.** | Descripción de GitHub, README, `meta description` |
| 3 | **Free means free. We check.** | Redes, pegatinas, banner del README |
| 4 | **The fine print, verified.** | Fichas y comunicación de cambios |
| 5 | **What's free today — and how we know.** | Informe mensual "What changed" |

Recomendación: **1** como tagline principal y **2** como descriptor fijo debajo del nombre en el README y el perfil de GitHub.
