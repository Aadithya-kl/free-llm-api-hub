# Estándar OSS v2 de pacocartones: etiquetas, plantillas y flujo de issues (26-11-2026)

**Estado:** borrador. **No se ha aplicado nada en GitHub.** Sustituye a `ESTANDAR-issues-y-etiquetas.md` (20-11) y se apoya en el estándar v1 de `pacocartones/dasousa-contributors-strategy` (skill `contributor-friendly-repo`, `labels-v1.tsv`, `.contributors.json`). Los pasos concretos están en `PLAN-aplicar-estandar.md` y la revisión de las 48 issues del Hub, en `AUDITORIA-issues-2026-11-26.md`.

**Base revisada:**
- `free-llm-api-hub`: `origin/main` en `5af5ef7` (26-11, 20:00 UTC), 17 etiquetas, 48 issues abiertas y 10 PRs abiertas;
- `dasousa-contributors-strategy` en `HEAD`;
- `market-data-sanity-checker`: 10 etiquetas y 2 issues abiertas.

## 0. Por qué no se aplicaba el estándar anterior (diagnóstico)

| Síntoma en el Hub | Causa | Qué cambia en v2 |
|---|---|---|
| **Ninguna de las 48 issues abiertas tiene *issue type*,** aunque el repo tiene Task, Bug, Feature, Data y Docs | Las plantillas ponen `type:`, pero casi todas las issues se crean por API (`gh issue create`, bots, sesiones de agente), y por API no se aplica | Regla 3.1: tipo y etiqueta de tipo siempre juntos. Re-tipado en bloque (Plan, paso H5) |
| La plantilla `program-task.yml` manda poner `SWoC27`, `Easy`, `Medium` y `Hard`, pero **esas etiquetas no existen** | Se escribió la plantilla antes de crear las etiquetas (bien, porque SWoC aún no confirma los nombres), pero sin decir cuándo se crean | §1.4: etiquetas de temporada con nombre, color y fechas de alta y baja |
| Hay **38 issues abiertas con `good first issue`,** varias ya resueltas (#792, #800, #873) o con más de 2 ficheros (#872) | No hay tope ni barrido (`gfi-audit.sh`) en la rutina | §3.3: tope por capacidad y barrido semanal |
| Textos que piden **regenerar y commitear derivados** (#7, #603, `program-task.yml`, el cuerpo de #4) mientras el bot está en modo `push` | Cada sesión redacta a mano; no hay un pie común | §2: bloque fijo "How to check" según el modo del bot |
| Etiquetas sin uso o redundantes: `wontfix` (0 usos), `priority:low` (0), `area:mcp` (0), `javascript` (2 PRs antiguas) | Se añaden "por si acaso" | §1: núcleo pequeño; lo opcional solo se crea si se usa |
| Issues de seguimiento (#4, #7, #8 y las mensuales) mezcladas con las tareas | No hay forma de filtrarlas | Nueva etiqueta `tracker` (decisión de Paco) |
| Fuera de programas, el Hub no publica un plazo de respuesta | `CONTRIBUTING.md` solo da plazos para SWoC | §3.6: 3 días laborables, sin compromiso, en todos los repos |

## 1. Etiquetas

**Principio** (heredado de v1): las etiquetas sirven para **encontrar trabajo**, no para explicar el proceso. Un repo nuevo arranca con el núcleo; lo opcional solo se crea cuando haga falta, pero siempre con el mismo nombre, color y descripción.

### 1.1 Núcleo: todos los repos (8, igual que `labels.required` de v1)

| Etiqueta | Color | Descripción (≤ 100 caracteres) |
|---|---|---|
| `bug` | `d73a4a` | Something is broken or wrong |
| `feature` | `a2eeef` | A new capability or an improvement to an existing one |
| `docs` | `0075ca` | Documentation only |
| `data` | `bfdadc` | Facts the project ships: add, correct or re-verify |
| `chore` | `ededed` | Maintenance, CI, dependencies or refactoring with no user-facing change |
| `good first issue` | `7057ff` | Good for newcomers; one bounded task |
| `help wanted` | `008672` | Ready for outside help: the scope and the check are in the issue |
| `needs info` | `fbca04` | Waiting for the author; closed after 14 days without an answer |

- Los nombres y colores son los de `labels-v1.tsv`. Las descripciones son las que ya usa el Hub, que son más claras; solo cambian las de `help wanted` y `needs info`, para que digan la regla.
- **`data`** solo existe en repos que publican datos (Hub, market-data). En un repo sin datos se crea igual, porque v1 la exige, pero no tiene plantilla.

### 1.2 Comunes opcionales (mismo nombre y color en todos los repos que las usen)

| Etiqueta | Color | Descripción | Cuándo se crea |
|---|---|---|---|
| `blocked` | `6e7781` | Waiting on outside information or prior work, named in the issue | Al primer bloqueo real. La issue dice "Blocked by #N" o el motivo |
| `tracker` | `5319e7` | Umbrella or recurring list; the work happens in linked issues or PRs | **Nueva, decisión de Paco.** La ponen los bots de listas (`weekly-worklist`, `monthly-issues`) y los trackers de campos. Nunca va con `good first issue` |
| `priority:high` | `b60205` | Handle before other work | Cuando algo bloquea a usuarios o a una fecha. Sin etiqueta, la prioridad es normal |
| `priority:low` | `c2e0c6` | Nice to have; no date | Solo si se va a usar para ordenar. Hoy hay 0 usos: se mantiene, pero no se crea en repos nuevos |
| `dependencies` | `0366d6` | Pull requests that update a dependency file | Lo pone Dependabot (`labels: [dependencies]` en `dependabot.yml`) |

### 1.3 Por repo: área

- **Formato:** `area:<x>` (color `c5def5`) y una descripción que nombre la carpeta.
- **Máximo 4 por repo.** Una issue lleva como mucho una.
- **En el Hub:** `area:site`, `area:ci` y `area:mcp`. `area:mcp` no tiene usos, pero el paquete MCP existe: se mantiene.
- **En un repo nuevo** no se crea ninguna hasta que haya más de ~20 issues abiertas.

### 1.4 De temporada: programas (SWoC y similares)

El motor de puntuación de SWoC lee **el nombre exacto** de la etiqueta, así que aquí no se aplica el prefijo `level:` (es una excepción documentada).

| Etiqueta | Color | Descripción |
|---|---|---|
| `SWoC27` | `1d76db` | Counts for Social Winter of Code Season 7 (Jan–Mar 2027) |
| `Easy` | `bfe5bf` | Program level: one or two named files, one check, under ~2 h |
| `Medium` | `fef2c0` | Program level: reading code or several sources, ~2–6 h |
| `Hard` | `f9d0c4` | Program level: a design decision or multi-file change, agreed in the issue first |

- **Alta:** cuando SWoC confirme los nombres (correo de selección o Discord, previsto del 1 al 12 de diciembre; `SWOC-2027-preparacion.md` §1.5). Si SWoC usa otros nombres, se cambian aquí y en la tabla de `CONTRIBUTING.md` › Programs, que es la única fuente para el contribuidor.
- **Baja:** después del 30-03-2027 **no se borran**, porque están en las PRs fusionadas y son el registro de los puntos. Se quitan de las issues que sigan abiertas.

### 1.5 Retiradas

| Etiqueta | Dónde | Motivo |
|---|---|---|
| `wontfix` | Hub (0 usos) | "Close as not planned" de GitHub más un comentario con el motivo dicen lo mismo sin una etiqueta que juzga (skill, parte 6). **Decisión menor de Paco:** se creó el 20-11 |
| `javascript` | Hub (2 PRs cerradas) | La creó Dependabot antes de fijar `labels: [dependencies]`. Se borra a mano después de comprobar que ningún workflow la lee |
| `hacktoberfest` y `hacktoberfest-accepted` | market-data (en #55 y #214) | Ya retiradas en el Hub. Hacktoberfest 2026 no puntúa PRs |

**Total en el Hub:** 8 de núcleo, 5 comunes (con `tracker`), 3 de área y 4 de temporada (de diciembre a marzo).

## 2. Plantillas

**Fuente única:** `dasousa-contributors-strategy/templates/v2/` (privado, versionado). Se publica una copia en un repo público **`pacocartones/.github`**, que GitHub usa por defecto en todo repo de la cuenta que **no tenga** su propia carpeta `.github/ISSUE_TEMPLATE/` (decisión de Paco; hoy ese repo no existe). Un repo con necesidades propias, como el Hub, copia las plantillas y las adapta.

**Reglas comunes:**
1. Cada formulario lleva `labels:` con **una etiqueta de tipo que exista** y `type:` con el *issue type* equivalente.
2. Los títulos llevan un prefijo entre corchetes que se puede buscar (`[bug]`, `[data]`, `[feature]`, `[proposal]`).
3. No se piden comandos que no apliquen al repo. Los comandos de comprobación salen de `.contributors.json` → `checks`.
4. Nunca se pide a un contribuidor que regenere o commitee ficheros derivados cuando el repo tiene un bot de regeneración en modo `push`. En ese caso se usa el bloque **"How to check (push mode)"** del §2.6.
5. Los textos públicos van en inglés.

### 2.1 Bug: `bug.yml`

```yaml
name: 🐛 Bug report
description: Something is broken or gives a wrong result.
title: "[bug] "
labels: ["bug"]
type: Bug
body:
  - type: input
    id: where
    attributes:
      label: Where does it happen?
      description: Page URL, command, file or API path. Version or commit if you know it.
    validations: { required: true }
  - type: textarea
    id: what
    attributes:
      label: What happens, and what did you expect?
    validations: { required: true }
  - type: textarea
    id: steps
    attributes:
      label: Steps to reproduce
      description: The smallest public input that shows it. No secrets or API keys.
      placeholder: "1. …  2. …  3. See …"
  - type: input
    id: env
    attributes:
      label: Environment
      placeholder: "e.g. Firefox 131 · Node 22 · Windows 11"
```

### 2.2 Datos: `data.yml` (solo en repos que publican datos)

Es la forma genérica. El Hub mantiene sus dos variantes, `inaccuracy.yml` (corregir) y `new-provider.yml` (proponer), que cumplen las mismas reglas.

```yaml
name: 🔧 Wrong or outdated data
description: A published fact is wrong, outdated or missing its source.
title: "[data] "
labels: ["data"]
type: Data
body:
  - type: markdown
    attributes:
      value: Point to the **primary source** (the provider's or publisher's own page), not a third-party summary.
  - type: input
    id: record
    attributes: { label: Which record? , description: "Its name or id in the dataset." }
    validations: { required: true }
  - type: textarea
    id: wrong
    attributes: { label: What is wrong, and what is correct? }
    validations: { required: true }
  - type: input
    id: source
    attributes: { label: Link to the primary source }
    validations: { required: true }
  - type: input
    id: checked
    attributes: { label: UTC date you read it (YYYY-MM-DD) }
    validations: { required: true }
```

### 2.3 Mejora: `feature.yml`

Para que un **usuario** pida algo. Es corta a propósito: quien quiera implementarlo usa la propuesta.

```yaml
name: ✨ Feature request
description: Ask for a capability or an improvement.
title: "[feature] "
labels: ["feature"]
type: Feature
body:
  - type: textarea
    id: need
    attributes:
      label: What are you trying to do?
      description: The task or question you have, not the solution. Who else needs it?
    validations: { required: true }
  - type: textarea
    id: today
    attributes: { label: What do you do today instead? }
  - type: textarea
    id: idea
    attributes: { label: Your idea (optional) }
```

### 2.4 Propuesta: `proposal.yml`

Para quien **quiere implementar** algo que no está en una issue. El enfoque se acuerda antes de escribir código (como v1).

```yaml
name: 🧭 Proposal (before you implement)
description: Agree the scope of a change before writing code.
title: "[proposal] "
labels: ["feature"]
type: Feature
body:
  - type: markdown
    attributes:
      value: A maintainer replies with "go", a narrower scope, or a reason. Please wait for that before opening a pull request.
  - type: textarea
    id: problem
    attributes: { label: Problem and who has it }
    validations: { required: true }
  - type: textarea
    id: scope
    attributes:
      label: Proposed change and what is out of scope
      description: The files you expect to touch.
    validations: { required: true }
  - type: textarea
    id: acceptance
    attributes:
      label: How we will know it works
      description: The check or example that proves it.
    validations: { required: true }
```

### 2.5 Tarea preparada (GFI y programas): `task.yml`, solo para mantenedores

Fusiona `first-task.yml` (v1) y `program-task.yml` (Hub). Es la forma de **toda** issue de entrada, sea `good first issue`, `help wanted` o de programa.

```yaml
name: 🌱 Prepared task (maintainers)
description: For maintainers. A task a newcomer can finish from the issue alone.
title: "<type>: "
labels: ["help wanted"]
body:
  - type: markdown
    attributes:
      value: |
        **For maintainers.** Contributors: please pick an existing task (see CONTRIBUTING.md).
        After opening: add ONE type label, `good first issue` only if it meets every condition in CONTRIBUTING.md › Good first issues,
        and during a program, the program label and ONE level label.
  - type: dropdown
    id: level
    attributes: { label: Level, options: [Easy, Medium, Hard] }
    validations: { required: true }
  - type: textarea
    id: context
    attributes: { label: Context, description: Why it matters and what exists today, with links at the reviewed commit. }
    validations: { required: true }
  - type: textarea
    id: task
    attributes: { label: Task, description: Exactly what to change and what not to change. For data, the page to read; the field stays null if the page doesn't answer. }
    validations: { required: true }
  - type: textarea
    id: check
    attributes: { label: How to check, description: The commands that must pass (from .contributors.json checks) and what to look at by hand. Paste the push-mode block if the repo has a regeneration bot. }
    validations: { required: true }
  - type: textarea
    id: done
    attributes: { label: Done when, description: Observable results a reviewer will check, as a checklist. }
    validations: { required: true }
  - type: textarea
    id: files
    attributes: { label: Files, description: Every file to touch. Never list generated files in push mode. }
    validations: { required: true }
  - type: input
    id: size
    attributes: { label: Size, placeholder: "about 1 hour" }
    validations: { required: true }
  - type: textarea
    id: footer
    attributes:
      label: For contributors
      value: |
        To take it, comment `/take` and the bot assigns it to you (see CONTRIBUTING.md › Claiming an issue). Tasks labelled both `good first issue` and `data` are not assigned: the first correct, sourced pull request is merged.
        Questions are welcome here before you start. AI-assisted work is welcome and must follow AI_POLICY.md. A partial answer is useful: tell us what you did and what you could not confirm.
    validations: { required: true }
```

**Orden fijo del cuerpo:** **Context → Task → How to check → Done when → Files → Size → For contributors.** Las tareas de datos con varios proveedores sustituyen "Task" por "Pick one provider" + "Rules" + "Change", como ya hacen #744 y #824.

### 2.6 Bloques fijos que se pegan tal cual

**How to check (push mode)**, para repos con bot de regeneración en `push` (hoy, el Hub):

```markdown
**How to check.** `<the fast check, e.g. npm run validate or node --test scripts/x.test.mjs>`, then `npm run build && npm test` if you have the project set up.
Commit only the files you edited (and a changelog fragment for user-visible changes). **Do not regenerate or commit derived files:** the regeneration bot commits them to `main` after the merge. If a check on your PR asks for regenerated files, say so in the PR and a maintainer will handle it.
```

**Claim (no data):** `To take it, comment /take and the bot assigns it to you, as CONTRIBUTING.md describes.`

**Claim (good first issue + data):** `**Not claimed:** the first correct, sourced PR for a provider is merged. One provider per PR; check open PRs first.`

### 2.7 `config.yml`

- `blank_issues_enabled: true`, para que los mantenedores y los bots puedan seguir creando issues sin formulario. A cambio, el barrido semanal (§3.7) etiqueta lo que entre sin tipo.
- `contact_links`, en este orden: primera contribución (CONTRIBUTING), tareas `help wanted`, preguntas (Discussions si están activadas) y seguridad (`SECURITY.md`).

### 2.8 Plantilla de PR: `PULL_REQUEST_TEMPLATE.md`

Es el esqueleto común. Cada repo añade su bloque de checklist (el del Hub se mantiene entero).

```markdown
## What changed
<!-- One or two sentences. Use `Closes #123` only if this PR fully resolves the issue; otherwise `Related to #123`. -->

## Source and date (data changes)
<!-- The primary source and the UTC day you read it. What it confirms and what stays unconfirmed. Delete for code or docs. -->

## How I tested it
<!-- The exact commands from CONTRIBUTING.md › Which checks to run, with results. Anything checked by hand. -->

## Remaining work or questions
<!-- Optional. Use a draft PR for unfinished work. -->

## Checklist
<!-- Repository-specific items go here (see .contributors.json checks). Remove items that do not apply. -->
- [ ] I ran the checks for my change and recorded the commands and results above.
- [ ] (Optional) I used AI tools for part of this change, and I have read and tested it myself.

<!-- Taking part in a program such as Social Winter of Code? Link the program issue with `Closes #123`. A maintainer adds the level label when merging. -->
```

## 3. Reglas de uso

### 3.1 Etiquetado (quién, cuándo y cuántas)

| Regla | Detalle |
|---|---|
| **R1. Un tipo** | Toda issue o PR abierta lleva **exactamente una** de `bug`, `feature`, `docs`, `data` o `chore`, y el *issue type* equivalente: `bug`→Bug, `feature`→Feature, `docs`→Docs, `data`→Data y `chore`→Task. Si una issue tiene dos partes, se divide |
| **R2. Entrada** | `help wanted` = lista para que la haga alguien de fuera: tiene alcance, comprobación y "Done when". `good first issue` va **siempre con `help wanted`** y solo si cumple los 6 criterios de `CONTRIBUTING.md` (fuentes públicas, 1–2 ficheros nombrados, una comprobación, < 2 h, sin asignar ni PR abierta, revisada en los últimos 30 días) |
| **R3. Estado** | `needs info`: la pelota la tiene el autor; se cierra a los 14 días sin respuesta, con un comentario amable. `blocked`: la pelota la tiene un tercero o un trabajo previo, que se nombra en la issue; **quita `help wanted`** mientras dure |
| **R4. Seguimiento** | `tracker`: issues paraguas y recurrentes. **Nunca** van con `good first issue` ni cuentan para el tope de GFI ni para el plazo de respuesta |
| **R5. Prioridad** | Solo `priority:high` (y `priority:low` si se usa). Sin etiqueta, la prioridad es normal |
| **R6. Área** | Como mucho una `area:<x>`, si el repo las tiene |
| **R7. Programa** | Solo los mantenedores. La **issue** lleva el programa y un nivel. La **PR** recibe las dos al fusionarla, y solo si cierra una issue de programa (`Closes #N`) |
| **R8. Bots** | Todo workflow que abre issues pone el tipo (y `tracker` si es una lista). Hoy, `lighthouse.yml` pone `chore`, cuando un fallo de rendimiento es un `bug` |
| **R9. Nada de etiquetas de proceso** | Nada de "no claim needed", "in progress" ni "duplicate". El estado lo dicen la asignación, la PR enlazada y el motivo del cierre |

### 3.2 Flujo `/take` y `/release`

Lo implementa `issue-assign.yml`. El del Hub es el de referencia: añade `MAX_OPEN` y el plazo de los programas a la versión de `assets/` de v1.

1. **`good first issue` + `data`: no se reclama.** Se fusiona la primera PR correcta y con fuente. Si alguien escribe `/take`, el bot responde con esa regla. Quien encuentra la respuesta pero no abre la PR lo publica en la issue, y la PR que lo use le da el crédito.
2. **Todo lo demás:** `/take` como primera palabra del comentario. El bot asigna si la issue está libre y la persona tiene menos de **2** issues abiertas asignadas.
3. **`/release`** la devuelve. Se agradece y no tiene coste.
4. **Inactividad:** a los **14 días** sin actividad (7 durante un programa), primero un aviso (el día 5 en un programa) y después se libera. Si dos personas quieren la misma issue, la conserva quien la pidió primero (v1, parte 3).
5. **Repos nuevos:** reclamación **manual** (`claim_policy: "manual"` en `.contributors.json`). El workflow solo se instala después de una revisión aparte (concurrencia y fallos parciales de la API), como dice v1.
6. **Trabajo del mantenedor sobre una issue asignada a otra persona:** no se hace. Si hace falta, se avisa en la issue y se ofrece otra tarea. La #800 es el contraejemplo: la cerró #892 mientras estaba asignada.

### 3.3 Good first issues: cuántas y con qué rutina

- **Tope por capacidad:** el Hub, con un mantenedor más agentes, **≤ 30 abiertas fuera de programa** y la reserva de SWoC (12 Easy) dentro de ese tope. Un repo pequeño, ≤ 5. Se mide con `GFI_MIN=0 GFI_MAX=<tope> gfi-audit.sh <repo>`.
- **Barrido semanal** (lunes, con `weekly-worklist`):
  - `gfi-audit.sh` marca las asignadas, las que tienen PR y las que llevan 30 días sin tocar;
  - se refresca cada marcada (sigue siendo cierta, texto con la regla actual y un comentario de estado);
  - las que ya no pueda terminar un principiante pierden `good first issue` y conservan `help wanted`.
- **Una issue perenne por campo de datos** (por ejemplo, #795 para `models_url`), con la lista de lo que queda. No se abre una issue por cada tanda: así se evitan duplicados como #747, #796 y #827.
- **Conversión:** cada viernes, `gfi-conversion.sh <repo>`. Si un tipo de issue no convierte en 15 casos, se dejan de abrir de ese tipo.

### 3.4 Programas: cómo marcar las issues por nivel (SWoC)

| Nivel | Criterio (`CONTRIBUTING.md` › Difficulty levels) | Qué issues del Hub encajan |
|---|---|---|
| **Easy** | 1–2 ficheros nombrados, una comprobación, sin cuenta de terceros, < ~2 h | GFI de datos de un solo campo, tests de funciones puras, docs de un fichero |
| **Medium** | Leer código o tests, o comparar varias páginas oficiales; ~2–6 h | Generador de `/embed/` (#829), tests con git (#882), `docs/guides.md` (#888), Lighthouse (#872), `free_limits` |
| **Hard** | Una decisión de diseño, varios ficheros o una re-verificación con citas; el enfoque se acuerda antes | `commercial_ok` con términos legales (#439, #603), bloque "respuesta primero" en las fichas |

- **No llevan etiqueta de programa:** `tracker`, issues que necesitan una cuenta de terceros (#7), investigación que solo deja un comentario (#878, porque solo puntúa una PR fusionada) y trabajo del mantenedor.
- **Proporción objetivo el 01-01:** 12 Easy, 8 Medium y 4 Hard (`SWOC-reserva-por-niveles.md`).
- **Tope por persona:** 2 issues Easy fusionadas. Después, Medium o Hard (`CONTRIBUTING.md`).
- **La propuesta de nivel** para cada issue abierta está en la columna "Nivel SWoC" de la auditoría. Se aplica cuando existan las etiquetas.

### 3.5 Cierre

- **Hecho:** "Close as completed", enlazando el commit o la PR y dando las gracias por nombre a quien aportó, aunque no abriera la PR.
- **Duplicado o absorbido:** "Close as not planned" (o *duplicate*) y la frase "Continues in #N", después de copiar a #N lo que quede pendiente y el crédito.
- **Fuera de alcance:** "Close as not planned", explicando qué haría falta para que fuera aceptable. Sin etiquetas que juzguen.
- **`needs info` sin respuesta:** a los 14 días, con la puerta abierta ("reopen when you have …").

### 3.6 Plazo de respuesta

| | Objetivo (best effort; no es un SLA; seguridad va aparte en `SECURITY.md`) |
|---|---|
| **Todo el año, todos los repos** | Una **respuesta real** (revisión, pregunta o asignación; un acuse de recibo no cuenta) a issues, PRs y peticiones de reclamación en **3 días laborables** (v1) |
| **Durante un programa** (Hub, SWoC: 01-01 a 30-03) | Aprobar los checks pendientes en **1 día**, responder a una PR nueva en **2**, primera revisión en **3** y decisión en **7**. Con más de 10 PRs de programa esperando, se pausan las asignaciones y se avisa en las issues |
| **Herramienta** | `PENDING_MAINTAINERS=pacocartones pending-responses.sh <repo> 2`, al empezar cada sesión de mantenimiento. Las listas son incompletas: que salga vacía no demuestra que no espere nadie |

**Hueco en el Hub:** fuera de la sección Programs, `CONTRIBUTING.md` no da plazo ("as soon as we can"). Hay que añadir la frase de los 3 días laborables (Plan, PR H2).

### 3.7 Rutina semanal (≈ 15 min, lunes)

1. `pending-responses.sh`: responder o asignar lo que espera.
2. `gfi-audit.sh`: refrescar o des-etiquetar.
3. **Issues sin tipo:** `gh issue list --search "-label:bug -label:feature -label:docs -label:data -label:chore -label:tracker" --state open`. Se etiquetan y se les pone el tipo.
4. **Etiquetas fantasma:** comprobar que todo `labels:` de las plantillas existe (`sync-labels.sh` en modo plan, que sale con código 1 si falta algo).

## 4. Aplicarlo a un repo nuevo en 10 minutos

**Requisitos:**
- `gh` autenticado como pacocartones, `bash` ≥ 4 y `jq`. **En el PC de Paco no hay `jq`**: hay que usar una sesión en la nube o instalarlo antes;
- un checkout de `dasousa-contributors-strategy` en un commit revisado (anotar el SHA).

Nada de esto ejecuta npm ni builds.

| Min | Paso | Comando o acción |
|---|---|---|
| 0–1 | Etiquetas: plan | `bash skills/contributor-friendly-repo/scripts/sync-labels.sh pacocartones/<repo> --labels templates/v2/labels-v2.tsv` |
| 1–2 | Etiquetas: aplicar (**con el OK de Paco**) | lo mismo con `--apply`. **No** usar `--delete` en el primer pase |
| 2–4 | Plantillas | Si existe `pacocartones/.github` y el repo no necesita formularios propios, no se hace nada (se heredan). Si no, se copian `templates/v2/ISSUE_TEMPLATE/*` y `PULL_REQUEST_TEMPLATE.md` a `.github/` en una rama `chore/oss-standard-v2` y se quitan `data.yml` y el bloque de datos si el repo no publica datos |
| 4–6 | Perfil | Copiar `.contributors.json` del ejemplo (`repository`, `maintainers: ["pacocartones"]`, `checks` reales, `claim_policy: "manual"`) y validarlo con `python3 <strategy>/scripts/check-profile.py .contributors.json --repo-root .` |
| 6–8 | CONTRIBUTING | Pegar las secciones "Claiming an issue", "Good first issues" y "Review" (la de los 3 días laborables) de `templates/v2/CONTRIBUTING-sections.md`. AI_POLICY y SECURITY, si faltan |
| 8–9 | Issue types | Bug, Feature y Task vienen de serie. Data y Docs ya existen a nivel de cuenta (el Hub los tiene). Comprobarlo en Settings → Issues del repo |
| 9–10 | Comprobación | `GFI_MIN=0 GFI_MAX=5 gfi-audit.sh pacocartones/<repo>`, `pending-responses.sh pacocartones/<repo> 2` y `sync-labels.sh` en plan (debe salir con código 0) |

Después, la PR en borrador `chore/oss-standard-v2` la fusiona Paco. El nombre de rama cumple la política de commits del Hub.

**Pendiente en `dasousa-contributors-strategy`** (borrador, con el OK de Paco):
- añadir `templates/v2/` (`labels-v2.tsv`, formularios, PR y secciones de CONTRIBUTING);
- un `apply-standard.sh` que haga los pasos 2–9 en modo plan, como `sync-labels.sh`.

`labels-v1.tsv` y el esquema v1 **no cambian**: v2 es un superconjunto, y los 8 obligatorios siguen igual.

## 5. Qué es común y qué se adapta por repo

| Común en todos (no se toca sin cambiar el estándar) | Se adapta por repo (se documenta en su `CONTRIBUTING.md` o `.contributors.json`) |
|---|---|
| Las 8 etiquetas de núcleo: nombre, color y descripción | Etiquetas `area:<x>` (como mucho 4) |
| Nombre, color y descripción de las comunes opcionales, si se usan | Qué opcionales existen (`blocked`, `tracker`, `priority:*`) |
| Correspondencia etiqueta de tipo ↔ issue type (R1) | Variantes del formulario de datos (Hub: `inaccuracy.yml` y `new-provider.yml`). `feature.yml` se puede omitir si las peticiones van a Discussions (el Hub lo hace) |
| Estructura de los formularios y orden del cuerpo de la tarea (§2.5) | Comandos de comprobación (`checks`) y si hay bot de regeneración (bloque push mode) |
| Reglas R1–R9, cierre (§3.5) y rutina semanal (§3.7) | `claim_policy`: manual (por defecto) o self-service con `issue-assign.yml` revisado |
| Regla `good first issue` + `data` = sin reclamación | `MAX_OPEN` (2 por defecto) y plazos de inactividad |
| Objetivo de respuesta: 3 días laborables, sin compromiso | Plazos de programa (solo en repos inscritos) y tope de GFI |
| Esqueleto de la plantilla de PR | Checklist específica de la PR (el Hub conserva la suya) |
| Política de IA: entender, probar, citar y sin trailers obligatorios | Etiquetas de programa (nombres que dicte el programa) |
