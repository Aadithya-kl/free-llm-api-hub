# Plan para aplicar el estándar OSS v2 (26-11-2026)

**Estado:** borrador, sin ejecutar. Cada paso marcado con 🔒 cambia algo en GitHub y **necesita el OK de Paco**. Lo ejecuta un solo actor: el coordinador, una acción pública cada vez.

**Referencias:**
- `ESTANDAR-oss-v2.md` (el qué);
- `AUDITORIA-issues-2026-11-26.md` (decisión por issue, textos y comentarios).

**Antes de cada paso** (AGENTS.md): refrescar la base y los checks.
- `git fetch origin` y `gh issue list` / `gh pr list` otra vez.
- Si una issue ha cambiado desde el 26-11 a las 21:18 UTC (comentario, PR o asignación), se revisa su fila de la auditoría antes de actuar.

**Sin npm ni builds.** Las PRs de plantillas y docs no necesitan build. Las comprobaciones de la PR las hace el CI.

## Orden y dependencias

```
H0 decisiones ─┬─ H1 etiquetas ─┬─ H5 tipos ── H6 re-etiquetado ── H7 reescrituras ── H4 cierres
               │                └─ H8 SWoC (cuando SWoC confirme los nombres)
               ├─ H2 PR de plantillas (borrador → Paco fusiona)
               ├─ H3 PR en dasousa-contributors-strategy (borrador)
               └─ H9 issues nuevas (N3, N4, N6 y N7 ya; N1, N2, N5 y N8 después de #846)
H10 verificación → R1–R3 otros repos
```

H4 va después de H7 porque al cerrar #12, #747, #796 y #827 se remite a #7 y #795, que antes tienen que tener el texto nuevo.

---

## free-llm-api-hub

### H0. Decisiones de Paco (bloquean el resto)

Son las 5 del resumen final. Mientras no estén:
- H1 se aplica sin `tracker` y sin borrar `wontfix`;
- el resto no cambia.

### H1. 🔒 Diff de etiquetas

Estado actual: 17 etiquetas. Usos medidos con `gh search issues --include-prs` el 26-11.

| Acción | Etiqueta | Detalle | Usos |
|---|---|---|---|
| **Crear** | `tracker` | `5319e7` · "Umbrella or recurring list; the work happens in linked issues or PRs" (si Paco aprueba) | — |
| **Editar descripción** | `help wanted` | → "Ready for outside help: the scope and the check are in the issue" | 30+ |
| **Editar descripción** | `needs info` | → "Waiting for the author; closed after 14 days without an answer" | 1 |
| **Editar descripción** | `blocked` | → "Waiting on outside information or prior work, named in the issue". Color `6E7781` → `6e7781` (mismo color) | 2 |
| **Renombrar** | — | Ninguna. Los 8 nombres de núcleo ya coinciden con v1 | — |
| **Borrar** | `wontfix` | 0 usos. Si Paco aprueba retirarla | 0 |
| **Borrar** | `javascript` | Está en 2 PRs cerradas de Dependabot. Ningún workflow la lee: en `.github/` solo aparece como lenguaje de CodeQL. Al borrarla desaparece de esas 2 PRs | 2 |
| **Mantener** | `bug`, `docs`, `feature`, `data`, `chore`, `good first issue`, `priority:high`, `priority:low`, `area:site`, `area:ci`, `area:mcp`, `dependencies` | Ya cumplen el estándar | — |

**Comandos** (cuando haya OK; idempotentes):

```bash
R=pacocartones/free-llm-api-hub
gh label create tracker --color 5319e7 --description "Umbrella or recurring list; the work happens in linked issues or PRs" -R $R
gh label edit "help wanted" --description "Ready for outside help: the scope and the check are in the issue" -R $R
gh label edit "needs info" --description "Waiting for the author; closed after 14 days without an answer" -R $R
gh label edit blocked --color 6e7781 --description "Waiting on outside information or prior work, named in the issue" -R $R
gh label delete wontfix --yes -R $R        # solo con OK
gh label delete javascript --yes -R $R     # solo con OK
```

**Otra vía,** cuando exista `labels-v2.tsv` (H3), y en una sesión con `jq`:
- `sync-labels.sh $R --labels labels-v2.tsv` (plan);
- después, `--apply`.

`--delete` no se usa: los dos borrados se hacen a mano.

### H2. 🔒 PR de plantillas y docs: `chore/oss-standard-v2` (borrador; Paco fusiona)

**Rama:** `chore/oss-standard-v2`, que cumple `hub-branch-names`. **Autor:** Paco Cartones con su noreply. Sin trailers de IA ni el pie de Claude en la PR (memoria `no-claude-footer-github`).

| Fichero | Cambio |
|---|---|
| `.github/ISSUE_TEMPLATE/program-task.yml` → **`task.yml`** | Formulario §2.5 del estándar, para GFI, `help wanted` y programas: `labels: ["help wanted"]` y orden Context → … → For contributors. Se quitan "including regenerated outputs if any" (campo Files) y el valor por defecto `npm run check` (campo How to check), y se pone el bloque push mode del §2.6. El aviso de etiquetas de programa remite a la tabla de `CONTRIBUTING.md` › Programs |
| `.github/ISSUE_TEMPLATE/proposal.yml` (**nuevo**) | §2.4: para quien quiere implementar algo sin issue. Las peticiones de usuario siguen yendo a Discussions (enlace "Questions & ideas" en `config.yml`), así que el Hub **no** añade `feature.yml` (adaptación permitida, §5) |
| `.github/ISSUE_TEMPLATE/config.yml` | Añadir al final el enlace de seguridad (`SECURITY.md`) |
| `bug_report.yml`, `inaccuracy.yml`, `new-provider.yml` | Sin cambios: ya llevan `labels:` y `type:` correctos |
| `.github/PULL_REQUEST_TEMPLATE.md` | Añadir el comentario de programa: "Taking part in a program… Link the program issue with `Closes #123`…". El resto se queda |
| `CONTRIBUTING.md` | (a) En "Claiming an issue", sustituir "We read every pull request and reply as soon as we can" por el objetivo de **3 días laborables, sin compromiso**, y la definición de respuesta real. (b) En "Good first issues", una línea: "We keep at most about 30 open". (c) En "Recurring issues", decir que las listas llevan `tracker` y no se reclaman |
| `.github/workflows/lighthouse.yml:146` | `--label chore` → `--label bug --label area:site` (R8: una regresión de rendimiento es un `bug`). **Ojo:** es un workflow, así que hay que revisar el diff línea a línea. Si N6 se abre antes, se incluye allí |
| `scripts/monthly-issues.mjs:125` y `:183` | Añadir `tracker` a las dos. La de candidatos pasa de `['help wanted']` a `['data', 'help wanted', 'tracker']` (R1: hoy no lleva tipo) |
| `.contributors.json` (**nuevo**) | Perfil v1: `repository`, `maintainers: ["pacocartones"]`, `response: {target_business_days: 3, best_effort: true}`, los 8 `labels.required`, `labels.additional: ["blocked","tracker","priority:high","priority:low","area:site","area:ci","area:mcp","dependencies"]`, los `checks` reales (`npm run validate`, `npm test`), `paths` (CONTRIBUTING.md, SECURITY.md, AI_POLICY.md) y `claim_policy: "self-service"` |
| `changes/unreleased/oss-standard-v2.md` | Una línea: issue forms and contribution guide aligned with the maintainers' standard |

**Sin tocar:**
- `issue-assign.yml`: ya es la referencia;
- `scripts/staleness.mjs`: es N7, una GFI.

**Comprobación de la PR:** que todos los `labels:` de los formularios existan después de H1, y que el CI pase en la PR.

### H3. 🔒 PR en `dasousa-contributors-strategy`: `templates/v2/` (borrador; privado)

- `templates/v2/labels-v2.tsv`: 8 de núcleo + 5 comunes (sin `area:*` ni las de temporada; esas van en un TSV aparte para cada repo y cada programa). Columnas iguales a `labels-v1.tsv`. `labels-v1.tsv` **no se toca**.
- `templates/v2/ISSUE_TEMPLATE/{bug,data,feature,proposal,task}.yml` y `config.yml`, y `templates/v2/PULL_REQUEST_TEMPLATE.md`: copias literales de `ESTANDAR-oss-v2.md` §2.
- `templates/v2/CONTRIBUTING-sections.md`: "Claiming an issue", "Good first issues", "Review" (los 3 días) y "Programs" (con la tabla de etiquetas vacía).
- `docs/standard-v2.md`: resumen del estándar, con un enlace a este borrador.
- **Opcional, en otra PR:** `scripts/apply-standard.sh <repo>` en modo plan, que compare etiquetas, plantillas y perfil e imprima el diff.

### H4. 🔒 Cierres y fusiones (9 issues)

Los textos están en la auditoría ("Comentarios de cierre y fusión"). Hay que hacerlo **después de H7**, y para cada issue, releerla antes de cerrar.

```bash
R=pacocartones/free-llm-api-hub
# completadas
gh issue close 792 -R $R --reason completed --comment-file c792.md
gh issue close 800 -R $R --reason completed --comment-file c800.md   # antes: gh issue edit 800 --remove-assignee alvaroalonsoparrondo-a11y
gh issue close 873 -R $R --reason completed --comment-file c873.md
gh issue close 556 -R $R --reason completed --comment-file c556.md   # solo después de que Paco abra las 3 URLs
# sustituidas o absorbidas
gh issue close 555 -R $R --reason "not planned" --comment-file c555.md
for n in 12 747 796 827; do gh issue close $n -R $R --reason "not planned" --comment-file c$n.md; done
```

`gh issue close --comment-file` no existe: hay que usar `--comment "$(cat cNNN.md)"` o comentar primero con `gh issue comment N --body-file cNNN.md`.

### H5. 🔒 *Issue types* en bloque (las 48 menos las 9 cerradas, y todas las nuevas)

Los tipos del repo son Task, Bug, Feature, Data y Docs. Correspondencia: `bug`→Bug, `feature`→Feature, `docs`→Docs, `data`→Data y `chore`→Task. Las del tracker reciben el tipo de su etiqueta de tipo.

```bash
# 1) IDs de los tipos
gh api graphql -f query='{repository(owner:"pacocartones",name:"free-llm-api-hub"){issueTypes(first:10){nodes{id name}}}}'
# 2) Por issue: su node id y la mutación
ID=$(gh api graphql -f query='{repository(owner:"pacocartones",name:"free-llm-api-hub"){issue(number:744){id}}}' --jq .data.repository.issue.id)
gh api graphql -f query='mutation($i:ID!,$t:ID!){updateIssueIssueType(input:{issueId:$i,issueTypeId:$t}){issue{number issueType{name}}}}' -f i=$ID -f t=<DATA_TYPE_ID>
```

- Si `updateIssueIssueType` no existe en el esquema, usar `updateIssue(input:{id:$i, issueTypeId:$t})`. Se comprueba primero con una sola issue.
- **Lista por tipo**, tras los cambios de H6:
  - **Data:** #4, #7, #8, #439, #455, #490, #603, #694, #744, #746, #758, #777, #778, #795, #803, #824, #825, #826, #877, #878
  - **Feature:** #794, #799, #829, #830, #871
  - **Docs:** #832, #886, #887, #888, #889
  - **Task:** #872, #879, #880, #881, #882, #883
  - **Bug:** #874, #884, #885

### H6. 🔒 Re-etiquetado en bloque (5 issues, más `tracker` si se aprueba)

```bash
R=pacocartones/free-llm-api-hub
gh issue edit 4   -R $R --add-label tracker
gh issue edit 7   -R $R --add-label tracker
gh issue edit 8   -R $R --add-label tracker
gh issue edit 490 -R $R --remove-label "help wanted"                       # R3: blocked quita help wanted
gh issue edit 694 -R $R --remove-label "needs info"                        # el proveedor ya respondió: nos toca a nosotros
gh issue edit 872 -R $R --remove-label "good first issue"                  # 4+ ficheros
gh issue edit 874 -R $R --remove-label chore --add-label bug --add-label area:site --add-label priority:high
```

Al quitar `good first issue` de #872, comentar: "Relabelled: this touches four files (gate, test, workflow and docs), so it no longer fits our good-first-issue rule. Still very welcome as `help wanted`."

### H7. 🔒 Reescrituras (5 cuerpos y 2 títulos)

Los textos están en la auditoría: #7 (cuerpo y título), #8 (cuerpo y título), #439, #603 y el bloque de estado de #795.

```bash
gh issue edit 7 -R $R --title "[tri-state] phone_required — 56 of 77 unknown; account-based checks welcome" --body-file b7.md
gh issue edit 8 -R $R --title "[tri-state] commercial_ok — tracker: 6 providers still unchecked (#439, #603)" --body-file b8.md
gh issue edit 439 -R $R --body-file b439.md
gh issue edit 603 -R $R --body-file b603.md
gh issue edit 795 -R $R --body-file b795.md   # cuerpo actual con el bloque de estado sustituido
```

**Antes de pegar:**
- recalcular las cifras (`null` de `phone_required` y de `commercial_ok`, y slugs sin `models_url`) sobre el `main` de ese día;
- dejar en cada issue un comentario de una línea: "Body refreshed on <date> to the current rules (regeneration bot in push mode) and status."

### H8. 🔒 Etiquetas SWoC (cuando SWoC confirme los nombres; previsto del 1 al 12 de diciembre)

1. Crear `SWoC27`, `Easy`, `Medium` y `Hard` con los colores y descripciones del estándar §1.4, o con los nombres que confirme SWoC. En ese caso, actualizar la tabla de `CONTRIBUTING.md` › Programs en la misma PR que la mencione.
2. Aplicarlas a las issues de la reserva: columna "Nivel SWoC" de la auditoría, y lista final en `SWOC-reserva-por-niveles.md`.
3. **Barrido mensual de enero a marzo:** las issues de programa cerradas sin PR pierden las etiquetas. Las PRs fusionadas las conservan.

### H9. Issues nuevas (borradores en la auditoría)

| Cuándo | Issues | Nota |
|---|---|---|
| 🔒 Ya | N3, N6, N7 (`help wanted`) y N4 (del mantenedor, `priority:high`) | N4: la redacción del título la aprueba Paco |
| 🔒 Al fusionar #846 (Cálida) | N1, N5, N8 y N2 (`blocked` hasta entonces) | Si #846 se retrasa más allá del 15-12, abrir N2 y N5 con `blocked` y "Blocked by #846" |

### H10. Verificación (solo lectura, después de H1–H7)

```bash
R=pacocartones/free-llm-api-hub
# 1) sin issues abiertas sin tipo
gh issue list -R $R --state open --search "-label:bug -label:feature -label:docs -label:data -label:chore" --json number --jq length   # esperado: 0
# 2) issue type puesto en todas
gh api graphql -f query='{repository(owner:"pacocartones",name:"free-llm-api-hub"){issues(states:OPEN,first:100){nodes{number issueType{name}}}}}' --jq '[.data.repository.issues.nodes[]|select(.issueType==null)]|length'   # esperado: 0
# 3) tope de GFI y barrido (sesión con jq)
GFI_MIN=0 GFI_MAX=30 PENDING_MAINTAINERS=pacocartones bash gfi-audit.sh $R
# 4) etiquetas de los formularios = etiquetas existentes
bash sync-labels.sh $R --labels labels-hub.tsv     # plan; esperado: sin "create"
```

---

## Los demás repos públicos de Paco

`gh repo list pacocartones --visibility public --source` devuelve **2** repos propios: `free-llm-api-hub` y `market-data-sanity-checker`. Los otros ~100 repos públicos son **forks** de contribución (con las issues desactivadas) y quedan fuera del estándar.

### R1. `market-data-sanity-checker`

**Estado:**
- 10 etiquetas: núcleo v1 con las descripciones antiguas, más `hacktoberfest` y `hacktoberfest-accepted`;
- formularios `bug_report.yml` (`[bug]`) y `rule_proposal.yml` (`[data]`), los dos **sin `type:`**;
- `blank_issues_enabled: false`, PR template y sin `.contributors.json`;
- issue types disponibles (Task, Bug, Feature, Data, Docs), pero las 2 issues abiertas no tienen tipo.

| Paso | Acción |
|---|---|
| 🔒 Etiquetas | Actualizar las descripciones de las 8 de núcleo al texto v2 (`gh label edit … --description`). Quitar `hacktoberfest` de #55 y #214 y borrar `hacktoberfest` y `hacktoberfest-accepted` (después ya no las lleva nada). No se crean opcionales |
| 🔒 Issues | **#55** (asignada a Enard52; sin actividad desde el 21-10, 36 días): un aviso ("still on it? If not, comment /release or we'll free it on <fecha +7>"). Pasada la fecha, liberarla. Título: quitar el prefijo "[good first issue]", que repite la etiqueta. **#214** (sin tocar desde el 21-10): refrescarla según la regla de los 30 días (comprobar que sigue siendo cierta y dejar un comentario de estado) o quitarle `good first issue`. Ponerles tipo: Data a las dos |
| 🔒 PR `chore/oss-standard-v2` | Añadir `type: Bug` y `type: Data` a los dos formularios. `task.yml` (con el bloque de comprobación de pnpm/vitest de este repo, sin push mode). Enlace de seguridad en `config.yml`. `.contributors.json` con `claim_policy` según si tiene `issue-assign.yml` (comprobarlo en `.github/workflows`; si no, `manual`). En CONTRIBUTING, la frase de los 3 días laborables |
| Verificar | `sync-labels.sh pacocartones/market-data-sanity-checker --labels labels-v2.tsv` (plan; esperado: solo "extra" de las que sean del repo) y `GFI_MIN=0 GFI_MAX=5 gfi-audit.sh …` |

### R2. Repos que se publiquen más adelante

Ahora son privados: `marketing-agency`, `free-market-data-apis`, `free-gpu-cloud-credits` y `claude-token-cost-calculator`, entre otros. **Paco decide su publicación.** Si se publican:
- los "10 minutos" del estándar §4, **antes** de anunciar el repo;
- `claim_policy: "manual"` y GFI ≤ 5 hasta que haya tracción.

### R3. 🔒 `pacocartones/.github` (si Paco lo aprueba)

- Repo público nuevo con `ISSUE_TEMPLATE/` (bug, feature, proposal, task y config), `PULL_REQUEST_TEMPLATE.md`, `CONTRIBUTING.md` genérico (que remite al del repo si existe), `SECURITY.md`, `CODE_OF_CONDUCT.md` y `SUPPORT.md`.
- GitHub los usa en todo repo de la cuenta **sin** sus propios ficheros. Ni el Hub ni market-data se ven afectados porque tienen los suyos; sirve para los repos futuros y los pequeños.
- **No cubre las etiquetas:** en cuentas personales no hay etiquetas por defecto, así que siempre se crean con el script.
- Es una publicación: la crea y la publica Paco, o el coordinador con su OK explícito.

## Rutina de mantenimiento (después de aplicar)

- **Lunes, ≈ 15 min:** §3.7 del estándar (`pending-responses`, `gfi-audit`, issues sin tipo y etiquetas fantasma).
- **Viernes:** `gfi-conversion.sh`.
- **1 de cada mes:** las issues mensuales nacen con `tracker` (H2).
- **De enero a marzo:** plazos de programa y barrido de las etiquetas SWoC (H8).
