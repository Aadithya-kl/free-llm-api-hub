# Auditoría de issues abiertas: free-llm-api-hub (26-11-2026)

**Solo lectura.** No se ha editado, etiquetado, comentado ni cerrado nada en GitHub. Las acciones las ejecuta el coordinador con el OK de Paco, siguiendo `PLAN-aplicar-estandar.md` (pasos H4–H7).

**Base:**
- 48 issues abiertas (`gh issue list --state open`, leídas a las 21:18 UTC del 26-11) y 10 PRs abiertas, todas de pacocartones;
- `origin/main` en `5af5ef7`;
- `data/providers.json` en ese commit: 77 proveedores, versión 2.14.2.

**Referencias:** `ESTANDAR-oss-v2.md` (las reglas R1–R9 están en su §3.1).

## Resumen

| Decisión | Nº | Issues |
|---|---|---|
| Mantener (solo se pone el *issue type*) | 29 | #455, #744, #746, #758, #777, #778, #794, #799, #803, #824, #825, #826, #829, #830, #832, #871, #877, #878, #879, #880, #881, #882, #883, #884, #885, #886, #887, #888, #889 |
| Re-etiquetar | 5 | #4 (además, su pie generado se corrige en el generador: N7), #490, #694, #872, #874 |
| Reescribir | 5 | #7, #8 (también se re-etiqueta), #439, #603, #795 (texto de estado) |
| Cerrar | 5 | #555, #556, #792, #800, #873 |
| Fusionar con otra | 4 | #12 → #7; #747, #796 y #827 → #795 |

Total: 29 + 5 + 5 + 5 + 4 = 48.

**Hallazgos transversales:**
1. **0 de 48 issues tienen *issue type*.** El repo tiene Task, Bug, Feature, Data y Docs. Hay que ponerlo en bloque (Plan H5). Correspondencia: `bug`→Bug, `feature`→Feature, `docs`→Docs, `data`→Data y `chore`→Task.
2. **Una sola issue sin etiqueta de tipo:** #12, que se fusiona en #7.
3. **Good first issues:** hoy hay 38 abiertas. Después de esta auditoría quedan **29**: se cierran 5, se fusionan 3 y #872 pierde la etiqueta. Eso cabe en el tope de 30, con la reserva SWoC dentro.
4. **Tres issues ya estaban resueltas en `main` y seguían abiertas:**
   - #792: el selector ya no tiene emoji, y lo comprueba `scripts/flags.test.mjs:122`;
   - #800: el H2 "All providers" lo añadió `ea574c92` (#892) **mientras la issue estaba asignada a alvaroalonsoparrondo-a11y**;
   - #873: la PR #900 de Satwik0607, fusionada, no tenía `Closes`.
5. **Textos que piden regenerar derivados** con el bot en modo `push`:
   - #7 ("There is no regeneration bot");
   - #603 ("generated outputs are committed");
   - el pie generado de #4 (`scripts/staleness.mjs:105`);
   - la plantilla `program-task.yml` ("including regenerated outputs" y el valor por defecto `npm run check`).
6. **#874 recibe un comentario del bot en cada ejecución que falla:** 10 el 26-11, todos con `/find/ 0.79`. Ver N6.

## Tabla: una fila por issue

Columnas:
- **Decisión:** M = mantener, RE = re-etiquetar, RW = reescribir, C = cerrar, F = fusionar.
- **Etiquetas estándar:** etiquetas finales (`tracker` solo si Paco aprueba crearla; si no, esas issues se quedan sin ella).
- **Nivel SWoC:** E/M/H = Easy/Medium/Hard; — = sin etiqueta de programa.

| # | Título (abreviado) | Etiquetas actuales | Dec. | Etiquetas estándar | Tipo | Nivel SWoC | Motivo / nota |
|---|---|---|---|---|---|---|---|
| 4 | Weekly re-verification worklist (bot) | data | RE + RW (generador) | data, tracker | Data | — | Lista recurrente. El pie dice "run `npm run build && npm test`, and open a PR": se corrige en `staleness.mjs` (N7), no a mano, porque el bot reescribe el cuerpo |
| 7 | [tri-state] phone_required tracker | help wanted, data | RW | data, help wanted, tracker | Data | — | El cuerpo dice "There is no regeneration bot" y da recuentos de octubre (41). Hoy: 56 de 77 en `null`, 55 con motivo registrado; solo `scaleway` no tiene motivo. Absorbe #12 |
| 8 | [tri-state] commercial_ok tracker | help wanted, data | RE + RW | data, help wanted, tracker | Data | — | Lista del 14-11 (30). Hoy: 37 en `null`, 6 sin motivo (`huggingface`, `ibm-watsonx`, `baseten`, `scaleway`, `vercel-ai-gateway`, `plamo`) |
| 12 | HF Inference Providers: phone_required | help wanted | F → #7 | — | — | — | Necesita una cuenta (no es GFI desde el 08-10). Es un caso de #7. Le falta la etiqueta de tipo |
| 439 | commercial_ok: huggingface, ibm-watsonx, baseten | help wanted, data | RW | data, help wanted | Data | H | Formato antiguo: sin bloque push mode y con la mención a Hacktoberfest. Términos legales = Hard (reserva SWoC) |
| 455 | Backfill models_free (4 providers) | help wanted, data | M | data, help wanted | Data | M | Texto correcto y al día (estado del 25-11). Lo de `novita` es una decisión del mantenedor, ya anotada |
| 490 | Contextual AI: trial prompt policy | help wanted, data, blocked | RE | data, blocked | Data | — | R3: `blocked` quita `help wanted`. Espera que el proveedor aclare. El cuerpo es un traspaso de evidencias largo; no se reescribe |
| 555 | GFI: free-tier limits (Cerebras/SiliconFlow/Z.ai) | help wanted, gfi, data | C | — | — | — | Su propia cabecera dice "New work goes to #556". Cerebras no es elegible |
| 556 | GFI: free limits (ModelScope/SiliconFlow/Z.ai) | help wanted, gfi, data | C (completada) | — | — | — | Abhishekkumar071 comprobó los tres el 26-11: ninguno publica límites numéricos sin iniciar sesión. Era el resultado completo que pedía la issue. **Paco abre las 3 URLs antes de cerrar** |
| 603 | commercial_ok: Scaleway or Vercel | help wanted, data | RW | data, help wanted | Data | H | "generated outputs are committed and `npm run check` passes after committing" contradice el modo push |
| 694 | [new provider] Synap by Linkrra | needs info, data | RE | data | Data | — | El proveedor cambió `free.html` el 26-11 a las 08:07 UTC, como se le pidió. La pelota está en nuestro tejado: quitar `needs info` y responder en el plazo (ver `eval-694-synap.md`) |
| 744 | GFI: data_policy for one provider | help wanted, gfi, data | M | data, good first issue, help wanted | Data | E | 19 candidatos sin `data_policy` |
| 746 | GFI: playground_url | help wanted, gfi, data | M | data, good first issue, help wanted | Data | E | Quedan `moondream`, `pollinations` y `elevenlabs`. Conviene refrescar la lista en un comentario |
| 747 | GFI: models_url (batch 1) | help wanted, gfi, data | F → #795 | — | — | — | Solo queda `scaleway`, que ya está en #795. Las PRs que esperaba ya están fusionadas |
| 758 | data: why card_required holds its value | help wanted, gfi, data | M | data, good first issue, help wanted | Data | E | — |
| 777 | data: why openai_compatible holds its value | help wanted, gfi, data | M | data, good first issue, help wanted | Data | E | `groq` en curso con AyhamJo7 (#785) |
| 778 | data: trial credit duration | help wanted, gfi, data | M | data, good first issue, help wanted | Data | E | `mixedbread` comprobado por vivek-ambariya |
| 792 | Explorer: modality options without emoji | feature, help wanted, gfi, area:site | C (completada) | — | — | — | Ya está en `main` (`site/index.html:361-369` y `scripts/flags.test.mjs:122`). Lo señaló alvaroalonsoparrondo-a11y |
| 794 | Guides hub: label each card's count | feature, help wanted, gfi, area:site | M | feature, good first issue, help wanted, area:site | Feature | E | — |
| 795 | GFI: models_url (perennial) | help wanted, gfi, data | RW (estado) | data, good first issue, help wanted | Data | E | Dice "16 of 77" y "9 in review": esas 9 ya están fusionadas. Hoy hay 25 con enlace y 52 sin él (51 activos; `poolside` es `verified: false`). Absorbe #747, #796 y #827 |
| 796 | GFI: models_url speech/embeddings | help wanted, gfi, data | F → #795 | — | — | — | Solo queda `cartesia` (en #795) |
| 799 | Provider pages: "Spotted something out of date?" | feature, help wanted, gfi, area:site | M | feature, good first issue, help wanted, area:site | Feature | E | **Riesgo:** toca la ficha, igual que #846 (Cálida). Si #846 no se fusiona antes del 15-12, pasarla a `blocked` |
| 800 | Home: visible "All providers" H2 | feature, help wanted, gfi, area:site | C (completada) | — | — | — | La resolvió #892 (`site/index.html:323`) mientras estaba asignada a alvaroalonsoparrondo-a11y. Disculparse y ofrecerle otra (ver comentario) |
| 803 | GFI: quote for one "Not free" entry | help wanted, gfi, data | M | data, good first issue, help wanted | Data | E | — |
| 824 | GFI: add keys_url | help wanted, gfi, data | M | data, good first issue, help wanted | Data | E | 47 sin enlace |
| 825 | data: re-check keys_url | help wanted, gfi, data | M | data, good first issue, help wanted | Data | E | — |
| 826 | data: why phone_required holds its value | help wanted, gfi, data | M | data, good first issue, help wanted | Data | E | — |
| 827 | GFI: models_url recent providers | help wanted, gfi, data | F → #795 | — | — | — | Bytez, Liquid AI y Public AI ya tienen enlace. Quedan `lemonfox` y `azure-speech` (en #795) |
| 829 | /embed/: Sort by option | feature, help wanted, gfi, area:site | M | feature, good first issue, help wanted, area:site | Feature | M | 2–3 h y JS del generador: Medium |
| 830 | Long guides: "On this page" list | feature, help wanted, gfi, area:site | M | feature, good first issue, help wanted, area:site | Feature | E | — |
| 832 | Tutorial: regeneration bot steps | docs, help wanted, gfi | M | docs, good first issue, help wanted | Docs | E | Asignada a MikeFTV (26-11) |
| 871 | /find/: "Help confirm it" link | feature, help wanted, gfi, area:site | M | feature, good first issue, help wanted, area:site | Feature | E | — |
| 872 | Lighthouse gate: add 3 guides | help wanted, gfi, chore, area:ci | RE | chore, help wanted, area:ci | Task | M | 4 ficheros o más (gate, test, workflow y docs): incumple el criterio 2 de GFI. Ojo: `/find/` está en 0,79 (#874) |
| 873 | README: point to /find/ | docs, help wanted, gfi | C (completada) | — | — | — | Hecho en la PR #900 (Satwik0607), fusionada el 26-11. `README.md:23` |
| 874 | Lighthouse performance below budget (bot) | chore | RE | bug, area:site, priority:high | Bug | — | Es una regresión (`/find/` 0,79 < 0,80), no mantenimiento. La reparación es del mantenedor. El ruido del bot va en N6 |
| 877 | data: why commercial_ok (value known) | help wanted, gfi, data | M | data, good first issue, help wanted | Data | M | Hay que leer términos legales: Medium |
| 878 | data: find changelog/status page (comment only) | help wanted, gfi, data | M | data, good first issue, help wanted | Data | — | Solo deja un comentario, sin PR, así que no puntúa en SWoC |
| 879 | Tests: changes.mjs helpers | help wanted, gfi, chore | M | chore, good first issue, help wanted | Task | E | — |
| 880 | Tests: long-guide wording helpers | help wanted, gfi, chore | M | chore, good first issue, help wanted | Task | E | — |
| 881 | Tests: /find/ matching helpers | help wanted, gfi, chore | M | chore, good first issue, help wanted | Task | E | — |
| 882 | Tests: release-tags in a throwaway repo | help wanted, gfi, chore | M | chore, good first issue, help wanted | Task | M | 2–3 h y git temporal: Medium |
| 883 | Tests: comparePath, sharedModalities, nameCmp | help wanted, gfi, chore | M | chore, good first issue, help wanted | Task | E | — |
| 884 | Doc pages: scrollable tables not keyboard-reachable | bug, help wanted, gfi, area:site | M | bug, good first issue, help wanted, area:site | Bug | E | — |
| 885 | A11y guard: focusable named table wrappers | bug, help wanted, gfi, area:site | M | bug, good first issue, help wanted, area:site | Bug | E | — |
| 886 | README: Guides line misses 3 guides | docs, help wanted, gfi | M | docs, good first issue, help wanted | Docs | E | Desde #898 hay 5 guías por caso de uso más. Conviene añadir un comentario de estado |
| 887 | docs/README.md: site page table | docs, help wanted, gfi | M | docs, good first issue, help wanted | Docs | E | — |
| 888 | docs/guides.md per guide | docs, help wanted, gfi | M | docs, good first issue, help wanted | Docs | M | 2–3 h: Medium |
| 889 | CONTRIBUTING: run a single test file | docs, help wanted, gfi | M | docs, good first issue, help wanted | Docs | E | — |

*gfi* = `good first issue` (abreviado en esta tabla).

**Recuento de la propuesta de nivel** (para cuando existan las etiquetas; la lista final la cierra `SWOC-reserva-por-niveles.md`):
- **Easy:** 24 candidatas (más N1, N3 y N7 cuando se abran);
- **Medium:** 6 (#455, #829, #872, #877, #882 y #888), más N5, N6 y N8;
- **Hard:** 2 (#439 y #603), más N2.

El objetivo de 12 Easy está cubierto de sobra. Faltan 2 Hard para llegar a 4.

---

## Textos de reescritura (en inglés, listos para pegar en el cuerpo)

### #7: nuevo cuerpo

Título: `[tri-state] phone_required — 56 of 77 unknown; account-based checks welcome`

```markdown
`phone_required` is a tri-state field in [`data/providers.json`](https://github.com/pacocartones/free-llm-api-hub/blob/main/data/providers.json): `true` (the provider asks for phone/SMS verification before the free API key works), `false` (it doesn't), `null` (not confirmed; it does not mean "no").

## Status at main `5af5ef7` (2026-11-26 UTC)

- **21** providers have a value (`true` or `false`).
- **56** are `null`. **55** of them already record why in `field_checks.phone_required` (the official pages are silent, or only an account shows it). Only `scaleway` has neither a value nor a reason: that is the one public-page task left.
- What's left is evidence public pages don't give.

## How you can help

- **You have an account with one of these providers** and remember whether signup asked for a phone number: comment with the provider, the UTC month you signed up and what the flow asked for. We record it only once a provider page or a dated signup check states it, so a comment is useful even if it can't go straight into the data.
- **`scaleway`:** read its signup and console docs and either quote the sentence or record the reason (`source_silent` with the pages you read). Use #826 for the format.
- Hugging Face (`huggingface`) was tracked in #12: its signup form asks for an email and a password, and no public page says whether a phone is asked for later (checked 2026-11-24).

## Rules

- Primary source only: the provider's own signup, console or terms pages. A third-party summary can help you find the fact, never confirm it.
- Couldn't confirm it? Leave `null` and say what you read. An honest unknown beats a confident wrong answer.
- One provider per pull request.

**How to check.** `npm run validate`, then `npm run build && npm test` if you have the project set up.
Commit only the files you edited (and a changelog fragment for user-visible changes). **Do not regenerate or commit derived files:** the regeneration bot commits them to `main` after the merge. If a check on your PR asks for regenerated files, say so in the PR and a maintainer will handle it.

This is a tracker, not a single task: there's no need to `/take` it. AI-assisted work is welcome and must follow `AI_POLICY.md`.
```

### #8: nuevo cuerpo

Título: `[tri-state] commercial_ok — tracker: 6 providers still unchecked (#439, #603)`

```markdown
`commercial_ok` is a tri-state field in `data/providers.json`: `true` (the free offer explicitly permits commercial or production use), `false` (evaluation, personal or non-production only), `null` (not verified). Silence is **not** permission.

## Status at main `5af5ef7` (2026-11-26 UTC)

- **37** providers are `null`. **31** of them record why in `field_checks.commercial_ok` (their terms neither grant nor deny commercial use of the free access).
- **6 have neither a value nor a reason:**
  - `huggingface`, `ibm-watsonx`, `baseten` → #439
  - `scaleway`, `vercel-ai-gateway` → #603
  - `plamo` (added recently) → open for anyone here
- Value known but reason missing for some providers → #877.

## Contribution contract

One provider per pull request. Quote the exact clause from the provider's own terms, acceptable-use policy or plan page, link it and give the UTC date you read it. If the documents stay ambiguous, leave `null` and record what you read; that is a complete result.

**How to check.** `npm run validate`, then `npm run build && npm test` if you have the project set up.
Commit only the files you edited (and a changelog fragment for user-visible changes). **Do not regenerate or commit derived files:** the regeneration bot commits them to `main` after the merge. If a check on your PR asks for regenerated files, say so in the PR and a maintainer will handle it.

This is a tracker: take the linked issues with `/take`, or comment here for `plamo`. AI-assisted work is welcome and must follow `AI_POLICY.md`.
```

### #439: nuevo cuerpo (mismo título)

```markdown
**Context.** `commercial_ok` is tri-state: `true` if the provider's own terms allow commercial or production use of the free access, `false` if they limit it to evaluation or non-commercial use, `null` when nobody has confirmed it. These three providers are `null` at main `5af5ef7` with no reason recorded (tracker: #8).

**Task.** Pick one of `huggingface`, `ibm-watsonx` or `baseten`. Open its Terms of Service or Acceptable Use Policy and its pricing page, and look for *commercial*, *production*, *evaluation only* and *resale*.
- If a sentence settles it, set `true` or `false` and record the quote with `npm run quotes:add -- <slug> --field commercial_ok` (see `docs/quotes.md`).
- If the terms are silent or contradict each other, leave `null` and record the reason in `field_checks.commercial_ok` (`source_silent` or `sources_disagree`, with the pages and the UTC date).

`huggingface` also appears in #7 (`phone_required`): if you edit that entry, mention it so two pull requests don't collide.

**How to check.** `npm run validate`, then `npm run build && npm test` if you have the project set up.
Commit only the files you edited (and a changelog fragment for user-visible changes). **Do not regenerate or commit derived files:** the regeneration bot commits them to `main` after the merge. If a check on your PR asks for regenerated files, say so in the PR and a maintainer will handle it.

**Done when:**
- [ ] one provider has a quoted `commercial_ok` or a recorded reason, with the page and the UTC date in the PR
- [ ] `npm run validate` passes

**Files:** `data/providers.json`, `data/quotes.json` (written by the helper), `changes/unreleased/<short-name>.md`.
**Size:** 2–4 hours: reading legal terms carefully matters more than speed.

To take it, comment `/take` and the bot assigns it to you, as `CONTRIBUTING.md` describes. Questions are welcome here before you start. AI-assisted work is welcome and must follow `AI_POLICY.md`; every quote comes from a page you opened yourself. A partial answer is useful: tell us what you read and what you could not confirm.
```

### #603: nuevo cuerpo (mismo título)

```markdown
**Context.** `scaleway` and `vercel-ai-gateway` have `commercial_ok: null` and no recorded reason at main `5af5ef7` (tracker: #8). Pinecone's terms were already read in #631 (general internal-business language does not settle hosted free-tier commercial use): keep that finding and revisit Pinecone only with a new, clearly applicable clause.

**Task.** Pick one:
- Scaleway: https://www.scaleway.com/en/pricing/model-as-a-service/ and its terms
- Vercel AI Gateway: https://vercel.com/docs/ai-gateway/pricing and its terms

Read the free-access page together with the terms that apply to it. The evidence must settle this API access and plan, not a generic product licence. Keep conditions: a conditional permission is not an unconditional `true`.
- Settled → set the value and record the quote with `npm run quotes:add -- <slug> --field commercial_ok`.
- Not settled → leave `null` and record the reason in `field_checks.commercial_ok` with the pages and the UTC date. A comment here with the same information is also a complete result.

Don't change other fields or claim a full re-verification from a single-field check.

**How to check.** `npm run validate`, then `npm run build && npm test` if you have the project set up.
Commit only the files you edited (and a changelog fragment for user-visible changes). **Do not regenerate or commit derived files:** the regeneration bot commits them to `main` after the merge. If a check on your PR asks for regenerated files, say so in the PR and a maintainer will handle it.

**Done when:**
- [ ] one provider has a quoted value (with its conditions) or a recorded reason
- [ ] the PR or comment gives the exact clause or pages and the UTC date read
- [ ] `npm run validate` passes

**Files:** `data/providers.json`, `data/quotes.json`, `changes/unreleased/<short-name>.md`.
**Size:** 2–4 hours.

To take it, comment `/take` and the bot assigns it to you, as `CONTRIBUTING.md` describes. AI-assisted work is welcome and must follow `AI_POLICY.md`.
```

### #795: sustituir el párrafo de estado (el resto del cuerpo se queda)

Hay que reemplazar el primer párrafo de "Pick one provider" y las líneas "Done:" e "In review" por esto:

```markdown
`models_url` is the provider's own public page listing the models its API offers. Provider pages link it as "Browse the official model catalogue ↗". At main `5af5ef7` (2026-11-26 UTC), **25 of 77** providers have it. These **51** active entries don't (`poolside` is also missing it, but it is `verified: false`: skip it):

**Text LLMs with an ongoing free tier:** `siliconflow`, `zai-glm`, `modelscope`, `vercel-ai-gateway`, `ovhcloud-ai-endpoints`, `huggingface`, `ai-horde`, `typhoon`, `aion-labs`, `meganova`, `sea-lion`

**Text LLMs with a trial credit:** `ai21`, `scaleway`, `novita`, `nlpcloud`, `pollinations`, `contextual-ai`, `upstage`, `wandb-inference`, `regolo`, `google-agent-platform-express`, `inception`, `lemonfox`, `modal`

**Speech:** `cartesia`, `azure-speech`, `speechmatics`, `gladia`, `speechify`, `unreal-speech`, `rime`, `fish-audio`, `camb-ai`, `rev-ai`, `voicegain`, `smallest-ai`, `retell-ai`

**Embeddings, OCR, images and other:** `jina-ai`, `mixedbread`, `pinecone-inference`, `twelve-labs`, `ocr-space`, `llamaparse`, `nanonets`, `unstructured`, `nutrient`, `veryfi`, `datalab`, `runware`, `photoroom`, `moondream`

Thanks to everyone who added the first 25, including @alvaroalonsoparrondo-a11y (Cohere, Deepgram, AssemblyAI, ElevenLabs, Bytez, Public AI and more). This is the single open issue for `models_url`; #747, #796 and #827 are closed into it.
```

(Comprobar al pegar que los 51 slugs siguen sin enlace: `jq -r '.providers[] | select(.models_url == null) | .slug' data/providers.json`. La lista sale del `main` del 26-11.)

---

## Comentarios de cierre y fusión (en inglés)

**#555:**
> Closing in favour of #556, which took over `free_limits` on 2026-11-20 with the findings from this thread. Thanks @Abhishekkumar071 for the Cerebras check: it showed that its published numbers apply only to the one-time trial credit, which is why trial-credit entries can't carry `free_limits`.

**#556** (después de que Paco abra las URLs del último comentario):
> Thanks @Abhishekkumar071. Your check of 2026-11-26 is exactly the result this issue asked for: Z.ai's rate-limit page needs a login, SiliconFlow publishes only category-wide ranges, and ModelScope publishes concurrency and Magicube costs rather than request or token limits. So `free_limits` stays absent for all three, and there is no eligible provider left here. Closing as completed; if a provider later publishes numbers for its continuous free access, we'll open a new task.

**#792:**
> This is already on `main`: the seven `#modality` options are plain text with unchanged values, and `scripts/flags.test.mjs` ("modality filter: plain-text options…") fails if a pictograph comes back. Thanks @alvaroalonsoparrondo-a11y for checking and saying so. Closing as completed.

**#800:**
> @alvaroalonsoparrondo-a11y, sorry: the "All providers" heading landed on `main` in #892 (home density work) while this issue was assigned to you, which shouldn't have happened. Closing as completed. If you'd like a replacement of the same size, #794 and #871 are free; comment `/take` there and it's yours.

**#873:**
> Done in #900 by @Satwik0607, merged 2026-11-26: `README.md` now points to the Find my free API wizard near the top (and `docs/README.md` too). Thank you! Closing as completed.

**#12 → #7:**
> Merging this into #7, which now tracks every provider whose phone requirement needs an account to confirm. Hugging Face's status (signup asks for email and password; no public page says whether a phone comes later, checked 2026-11-24) is copied there. If you have an HF account and remember the signup flow, a comment in #7 is very welcome. Thanks @JhansiOruganti-43 for the early interest.

**#747, #796, #827 → #795:**
> Closing into #795, now the single open issue for `models_url`. The provider left here (`scaleway` / `cartesia` / `lemonfox`, `azure-speech`) is listed there. Thank you to everyone whose PRs filled the rest of this batch.

**Respuesta pendiente en #694** (dentro del plazo; la redacta Paco después de releer `free.html` y aplicar `eval-694-synap.md`): no se incluye aquí porque depende de la decisión de inclusión.

---

## Issues nuevas que faltan (huecos reales, comprobados en `main` `5af5ef7`)

**Ya resuelto en `main` (no se abre issue):**
- de la QA (`QA-web-2026-11-26.md`): U1, U2, U3 y U6 (banner y menú), con #892 y `scripts/home-density.test.mjs`; el estilo del widget, `/changes/`, el ancho de la fecha "Checked" y las cifras de la puntuación, con #891; el scroll lateral en el móvil, con #902;
- del AEO: `llms.txt` ampliado, `.md` por ficha y `Google-Extended` en HTML, con #901;
- el Dataset inválido, `dateModified` y Article: lo cubre la PR #904 (abierta);
- IndexNow ya está en `pages.yml`;
- `Offer` en `/find/` se omite a propósito (`find-page.mjs:95`) y #904 toca ese fichero.

**Sin issue (no es trabajo de repo):**
- Bing Webmaster Tools: acción de Paco;
- PRs a `awesome-*`: pausa de difusión hasta el 10-12;
- prueba AEO mensual: sesión local.

**Se abre cuando haya datos:**
- la tabla de límites por modelo (AEO 4 y 7) depende de `free_limits.per_model` en #774;
- las comparativas por pares con impresiones dependen de la línea base de 28 días en GSC.

| Id | Título | Etiquetas | Tipo | Nivel | Cuándo |
|---|---|---|---|---|---|
| N1 | Provider pages: title as the question people ask ("Is the X API free?") with the month | feature, help wanted, area:site | Feature | E | Después de fusionar #846, que toca `build.mjs`, y con la redacción aprobada por Paco |
| N2 | Provider pages: an answer-first sentence and a FAQPage generated from the data | feature, area:site, blocked | Feature | H | Bloqueada por #846. `help wanted` cuando se desbloquee |
| N3 | Long-form guides: every title states its count and "Checked" | feature, help wanted, good first issue, area:site | Feature | E | Ya (no choca con la pila Cálida) |
| N4 | Home `<title>`: lead with "Free LLM API list" and say "76 verified of 77" | feature, area:site, priority:high | Feature | — | Ya. Es del mantenedor: experimento de CTR con fecha de medición |
| N5 | Provider page: key and snippet before the score; no empty rule in "What's free" | feature, area:site, blocked | Feature | M | Bloqueada por #846 |
| N6 | Lighthouse report: update one comment instead of adding one per failing run | chore, help wanted, area:ci | Task | M | Ya |
| N7 | Weekly worklist (#4): footer tells contributors not to commit derived files | chore, help wanted, good first issue | Task | E | Ya |
| N8 | One word for unknown values: "not stated" everywhere | feature, help wanted, area:site | Feature | M | Después de #846 (toca `build.mjs`). Paco confirma la palabra |

### N1: Provider pages: title as the question people ask, with the month

```markdown
**Context.** Every provider page is titled `<Name> — free tier & limits · Free LLM API Hub` (`scripts/build.mjs`, the `htmlPage({ title: … })` call in the provider page loop). In our 2026-11-26 answer-engine check, none of our provider pages was cited for "is the Groq API free?"-style questions; the pages that win put the question in the title and carry a date. The home page already uses a month stamp (`TITLE_MONTH`).

**Task.**
1. Change the provider page title to:
   - ongoing free tier (`free_type` is not `trial-credit`): `Is the ${p.name} API free? Free tier limits (${TITLE_MONTH})`
   - trial credit: `${p.name} API: free trial credit and limits (${TITLE_MONTH})`
2. Keep it at most 60 characters before ` · Free LLM API Hub` is dropped: if the name makes it longer, drop the `(${TITLE_MONTH})` part, never the question.
3. Use the same string for `og:title`/`twitter:title` if they are set from the title.
4. Add a test in `scripts/provider-page.test.mjs`: for three providers (one ongoing, one trial, the longest name) the built `site/p/<slug>.html` has the expected `<title>` and it is ≤ 60 characters without the suffix.

Do not change the H1, the meta description or the OG image.

**How to check.** `npm run build && npm test` (the test reads the built pages). Commit your source and test changes only. **Do not regenerate or commit derived files:** the regeneration bot commits them to `main` after the merge. If a check on your PR asks for regenerated files, say so in the PR and a maintainer will handle it.

**Done when:**
- [ ] the titles follow the two patterns and the 60-character rule
- [ ] the new test passes, with a negative control shown in the PR (revert the title and show it fails)
- [ ] `npm run build && npm test` pass, with the output in the PR

**Files:** `scripts/build.mjs`, `scripts/provider-page.test.mjs`.
**Size:** about 1–2 hours.

To take it, comment `/take` and the bot assigns it to you, as `CONTRIBUTING.md` describes. Questions are welcome here before you start. AI-assisted work is welcome and must follow `AI_POLICY.md`.
```

### N2: Provider pages: an answer-first sentence and a FAQPage generated from the data

```markdown
**Context.** Answer engines quote the first self-contained sentence under a page's heading. Our provider pages open with badges and a score, not with an answer. The long-form guides already open with a 40–55-word direct answer and a FAQPage whose text is the visible text (`scripts/guides-seo.test.mjs`), so the pattern and its tests exist.

**Blocked by #846** (it rebuilds the provider page header). Start after it merges.

**Task (agree the approach here first).**
1. Under the H1 of `/p/<slug>`, one sentence built only from the data, e.g. "**Is the Groq API free?** Yes: an ongoing free tier, no credit card. Limits: 30 requests/min and 1,000/day for gpt-oss-120b (checked 2026-11-24, source)." Trial credits and `verified: false` entries get their own wording; unknown fields say "not stated", never a guess.
2. A `FAQPage` JSON-LD with 3–4 questions (Is it free? Does it need a card? What are the limits? Is commercial use allowed?), each answer identical to visible text on the page.
3. Tests: every provider page has the sentence, it contains the `last_verified` date, and every FAQ answer appears verbatim in the visible HTML.

**How to check.** `npm run build && npm test`; validate two pages in the Rich Results Test and paste the result. Commit source and tests only (push mode: no derived files).

**Done when:** the sentence and FAQ exist on all provider pages, the tests pass, and the Rich Results Test shows no FAQ errors.

**Files:** `scripts/build.mjs` or a new `scripts/lib/provider-answer.mjs`, `scripts/provider-page.test.mjs`.
**Size:** more than a day, in steps (Hard).
```

### N3: Long-form guides: every title states its count and "Checked"

```markdown
**Context.** Titles in `LONG_GUIDES` (`scripts/lib/long-guides.mjs`) follow two styles. Some say how many entries were checked — `Free Embedding APIs ({n}, Checked): Limits and Terms` — and those are the guides answer engines cited in our 2026-11-26 check. Others don't: OpenAI alternatives, production checklist, coding, RAG and agents. The chatbot guide writes `({n} Checked)` without the comma.

**Task.**
1. Give every list-type guide a title with `({n}, Checked)`: coding, RAG, agents and OpenAI alternatives. Keep each under the 60-character limit `scripts/guides-seo.test.mjs` already enforces (shorten the subtitle part if needed). The production checklist is not a list of providers: leave it.
2. Fix the chatbot title to `({n}, Checked)`.
3. Add a test in `scripts/guides-seo.test.mjs`: every guide except the production checklist has `, Checked)` in its title.

**How to check.** `node --test scripts/guides-seo.test.mjs` needs the build; run `npm run build && npm test` if you have the project set up. Commit your source and test changes only. **Do not regenerate or commit derived files:** the regeneration bot commits them to `main` after the merge.

**Done when:**
- [ ] the five titles follow the pattern and stay ≤ 60 characters
- [ ] the new test fails when one title loses the pattern (negative control in the PR)
- [ ] `npm run build && npm test` pass, with the output in the PR

**Files:** `scripts/lib/long-guides.mjs`, `scripts/guides-seo.test.mjs`.
**Size:** about 1 hour.

To take it, comment `/take` and the bot assigns it to you, as `CONTRIBUTING.md` describes. Questions are welcome here before you start. AI-assisted work is welcome and must follow `AI_POLICY.md`.
```

### N4: Home `<title>`: lead with "Free LLM API list" and say "76 verified of 77" (mantenedor)

```markdown
**Context.** "free llm api" is our largest query in Search Console (639 impressions, 1.3 % CTR on 2026-11-23). The home title (`HOME_TITLE`, `scripts/build.mjs`) reads `Free LLM APIs (Nov 2026): 76 verified free tiers & credits, sourced & dated`, while the page and `llms.txt` say 77 providers. Answer engines see two numbers.

**Task.**
- Title: `Free LLM API list (Nov 2026): 77 free tiers, 76 verified with sources` (≤ 70 characters; the month stays generated).
- Use the same counts and wording in `og:title`, `twitter:title` and the first line of `llms.txt`.
- Test: the title starts with "Free LLM API list" and both numbers match the data.
- Record the deploy date in `analytics/PLAN-medicion.md` to compare CTR 28 days before and after.

**Files:** `scripts/build.mjs`, `scripts/build.test.mjs`. **Size:** under 1 hour.
```

### N5: Provider page: key and snippet before the score; no empty rule in "What's free"

```markdown
**Context.** On a 390 px phone, `/p/groq` shows "Get a free key" about three screens down and the copyable snippet below it; the score block and its legend come first (QA 2026-11-26). The "What's free" card also starts with an empty rule: `.prose h2 { border-top; padding-top }` applies to `h2#whats-free` inside `.prov-summary`, and `.prov-summary h2` (`site/styles.css`) resets only the margin.

**Blocked by #846** (it rebuilds this page). Start after it merges.

**Task.**
1. Order: What's free (headline numbers) → **Get a free key** + **Copy base URL** → quickstart snippet → requirements (reasons collapsible) → score on one line ("#1 of 76 scored · 62/100 · how it is computed ▸", bar and legend inside the disclosure).
2. `.prov-summary h2 { border-top: 0; padding-top: 0; }`.
3. Test: in the built `site/p/groq.html`, the keys link and the snippet come before the score block, and `.prov-summary h2` has no top border.

**How to check.** `npm run build && npm test`, plus a 390 px screenshot before and after in the PR. Commit source and tests only (push mode).

**Files:** `scripts/build.mjs`, `site/styles.css`, `scripts/provider-page.test.mjs`. **Size:** about half a day (Medium).
```

### N6: Lighthouse report: update one comment instead of adding one per failing run

```markdown
**Context.** When the nightly/main Lighthouse check fails, `.github/workflows/lighthouse.yml` (step "Open, update or close the performance issue") opens one issue and then adds **a new comment on every failing run**. On 2026-11-26, #874 got ten identical comments (`/find/: performance 0.79 is below 0.80`), one per merge to `main`.

**Task.**
1. Keep one issue per failure episode, as today, and keep closing it on the first clean run.
2. Instead of `gh issue comment` on every run, rewrite the issue body with the latest result (commit, run link, failing pages and scores, UTC time). Add a new comment only when the set of failing pages or their scores change.
3. Keep the job's permissions as they are (`issues: write` only, no checkout in the report job).
4. Document the behaviour in the workflow's header comment.

**How to check.** Workflow logic can't run locally: explain in the PR how you tested the shell (for example, the script body run against a test repo or with `gh` stubbed), and paste `actionlint` output if you have it. A maintainer reviews any workflow change line by line before approving its run.

**Done when:**
- [ ] repeated identical failures produce no new comments; a changed result produces exactly one
- [ ] the body always shows the latest run
- [ ] the issue still closes on the first clean run

**Files:** `.github/workflows/lighthouse.yml`. **Size:** about 2–3 hours (Medium).

To take it, comment `/take` and the bot assigns it to you, as `CONTRIBUTING.md` describes. AI-assisted work is welcome and must follow `AI_POLICY.md`.
```

### N7: Weekly worklist (#4): footer tells contributors not to commit derived files

```markdown
**Context.** The body of #4 is generated by `scripts/staleness.mjs`. Its last line tells contributors to "update the entry in `data/providers.json` …, run `npm run build && npm test`, and open a PR". Since the regeneration bot runs in push mode, contributors must not commit the files `npm run build` regenerates, and the footer doesn't say so.

**Task.**
1. In `scripts/staleness.mjs`, change the footer to: re-check the provider's own docs; update the entry (`last_verified` = today, or `verified: false` with a note); run `npm run validate` (and `npm run build && npm test` if you have the project set up); **commit only `data/providers.json`, `data/quotes.json` if the quote helper changed it, and a changelog fragment — the regeneration bot commits derived files after the merge**; open a PR. Keep the link to `docs/update-playbook.md`.
2. In `scripts/staleness.test.mjs`, assert that the generated body contains "regeneration bot" and does not contain "commit the regenerated".

**How to check.** `node --test scripts/staleness.test.mjs` (no build needed), then `npm test` if you have the project set up. Commit your source and test changes only.

**Done when:**
- [ ] the footer has the new wording
- [ ] the test passes, and fails if the old wording comes back (negative control in the PR)

**Files:** `scripts/staleness.mjs`, `scripts/staleness.test.mjs`.
**Size:** under 1 hour.

To take it, comment `/take` and the bot assigns it to you, as `CONTRIBUTING.md` describes. Questions are welcome here before you start. AI-assisted work is welcome and must follow `AI_POLICY.md`.
```

### N8: One word for unknown values: "not stated" everywhere

```markdown
**Context.** The same fact — a provider's page doesn't say — appears as "?" on provider pages, "not confirmed" on `/compare/` and `/find/`, and in other words elsewhere (QA 2026-11-26, U7). Readers and answer engines can take these for different states. At main `5af5ef7`, "not confirmed" appears in `scripts/lib/find.mjs` (11), `scripts/lib/find-page.mjs` (3), `scripts/lib/compare.mjs` (4) and `scripts/build.mjs` (9; some may be legitimate other uses).

**Start after #846 merges** (it edits `scripts/build.mjs`).

**Task.**
1. List every user-visible place that names an unknown tri-state value (paste the list in a comment here first; a maintainer confirms it before you change code).
2. Use "not stated" in all of them (keep "?" only as an icon with "not stated" as its accessible name).
3. Add a test that the built `/find/`, one `/compare/` page and one provider page contain no "not confirmed".

**How to check.** `npm run build && npm test`. Commit source and tests only (push mode).

**Done when:** one term everywhere, the test passes, and the PR lists every string changed.

**Files:** the four files above and their tests. **Size:** about half a day (Medium).
```
