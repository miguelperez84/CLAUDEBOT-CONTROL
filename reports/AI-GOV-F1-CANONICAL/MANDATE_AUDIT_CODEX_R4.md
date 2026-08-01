# Reauditoría independiente Codex — Mandato de Fase 1 R4

## 1. Identificación

- **Tarea auditada:** `AI-GOV-F1-CANONICAL`.
- **Agente auditor:** Codex.
- **Repositorio operacional:**
  `/home/miguel/proyectos/CLAUDEBOT-CONTROL-CODEX-AI-GOV-F1-MANDATE-R4`.
- **Rama operacional:** `audit/codex-ai-gov-f1-mandate-r4`.
- **HEAD operacional inicial:**
  `dd414455d0bf46ebd8f098e1049bdef32edafa96`.
- **Commit objetivo auditado:**
  `aa965803f103bfd3923ddd8fdbd04dd87253367a`.
- **Padre exacto comprobado:**
  `7c61c1ad56318186b126c93acb4f7c281a699a56`.
- **Artefactos auditados:**
  `tasks/AI-GOV-F1-CANONICAL/MANDATE.md` y
  `tasks/AI-GOV-F1-CANONICAL/ACCEPTANCE.md`.
- **Objeto:** reauditoría completa, independiente y desde cero del
  mandato R4; evaluación individual de A-01 a A-21, H-01 a H-05,
  N-01 a N-04 y N-05; búsqueda de contradicciones y defectos nuevos.

La implementación de la Fase 1 continúa sin autorizarse. Este informe
no autoriza implementación, integración, push, congelación ni cierre y
no sustituye una decisión expresa de Miguel.

## 2. Preflight y alcance

El preflight obligatorio produjo:

```text
$ pwd
/home/miguel/proyectos/CLAUDEBOT-CONTROL-CODEX-AI-GOV-F1-MANDATE-R4

$ git branch --show-current
audit/codex-ai-gov-f1-mandate-r4

$ git rev-parse HEAD
dd414455d0bf46ebd8f098e1049bdef32edafa96

$ git status --short
[sin salida]
```

La ruta, rama y HEAD coincidieron exactamente con la instrucción
operacional y el árbol estaba limpio. La reauditoría continuó.

Los dos artefactos objetivo se leyeron exclusivamente mediante
`git show` contra `aa965803f103bfd3923ddd8fdbd04dd87253367a`. Las
cinco fuentes institucionales se leyeron exclusivamente mediante
`git show` contra `dd414455d0bf46ebd8f098e1049bdef32edafa96`. Los
tres informes anteriores se leyeron exclusivamente como los blobs
históricos autorizados y se usaron solo como evidencia comparativa
auxiliar. Las salidas extensas se repitieron por tramos del mismo
`git show` cuando el límite de visualización truncó la salida; esa
paginación no cambió el blob fuente ni abrió otra ruta.

## 3. Archivos y blobs abiertos

1. `aa965803f103bfd3923ddd8fdbd04dd87253367a:tasks/AI-GOV-F1-CANONICAL/MANDATE.md`.
2. `aa965803f103bfd3923ddd8fdbd04dd87253367a:tasks/AI-GOV-F1-CANONICAL/ACCEPTANCE.md`.
3. `dd414455d0bf46ebd8f098e1049bdef32edafa96:AGENTS.md`.
4. `dd414455d0bf46ebd8f098e1049bdef32edafa96:templates/AUDIT_TEMPLATE.md`.
5. `dd414455d0bf46ebd8f098e1049bdef32edafa96:decisions/OWNER_DECISIONS.md`.
6. `dd414455d0bf46ebd8f098e1049bdef32edafa96:docs/plan_arquitectura_gobernanza_multi_ia_v1.md`.
7. `dd414455d0bf46ebd8f098e1049bdef32edafa96:docs/reauditoria_codex_plan_arquitectura_gobernanza_multi_ia_v1_r3.md`.
8. `749ab3c73383984a2f893236835387d20709c71c:reports/AI-GOV-F1-CANONICAL/MANDATE_AUDIT_CODEX.md`.
9. `c30a7cb8f5cd26eccd8365cd50c53aff9fd7fa03:reports/AI-GOV-F1-CANONICAL/MANDATE_AUDIT_CODEX_R2.md`.
10. `71e61f8f66ceb3f5b457dc8c1c0927d83a9679ac:reports/AI-GOV-F1-CANONICAL/MANDATE_AUDIT_CODEX_R3.md`.

No se abrió ninguna otra ruta. Los blobs 8 a 10 no sustituyeron,
redujeron ni limitaron la revisión completa desde cero de los dos
artefactos objetivo.

## 4. Comandos ejecutados

```text
pwd
git branch --show-current
git rev-parse HEAD
git status --short

git rev-parse aa965803f103bfd3923ddd8fdbd04dd87253367a^
git diff --name-status 7c61c1ad56318186b126c93acb4f7c281a699a56 aa965803f103bfd3923ddd8fdbd04dd87253367a
git diff 7c61c1ad56318186b126c93acb4f7c281a699a56 aa965803f103bfd3923ddd8fdbd04dd87253367a -- tasks/AI-GOV-F1-CANONICAL/MANDATE.md tasks/AI-GOV-F1-CANONICAL/ACCEPTANCE.md
git show --check --stat --oneline aa965803f103bfd3923ddd8fdbd04dd87253367a

git show aa965803f103bfd3923ddd8fdbd04dd87253367a:tasks/AI-GOV-F1-CANONICAL/MANDATE.md
git show aa965803f103bfd3923ddd8fdbd04dd87253367a:tasks/AI-GOV-F1-CANONICAL/ACCEPTANCE.md

git show dd414455d0bf46ebd8f098e1049bdef32edafa96:AGENTS.md
git show dd414455d0bf46ebd8f098e1049bdef32edafa96:templates/AUDIT_TEMPLATE.md
git show dd414455d0bf46ebd8f098e1049bdef32edafa96:decisions/OWNER_DECISIONS.md
git show dd414455d0bf46ebd8f098e1049bdef32edafa96:docs/plan_arquitectura_gobernanza_multi_ia_v1.md
git show dd414455d0bf46ebd8f098e1049bdef32edafa96:docs/reauditoria_codex_plan_arquitectura_gobernanza_multi_ia_v1_r3.md

git show dd414455d0bf46ebd8f098e1049bdef32edafa96:decisions/OWNER_DECISIONS.md | sed -n '301,650p'
git show dd414455d0bf46ebd8f098e1049bdef32edafa96:decisions/OWNER_DECISIONS.md | sed -n '651,1000p'
git show dd414455d0bf46ebd8f098e1049bdef32edafa96:decisions/OWNER_DECISIONS.md | sed -n '1001,1350p'
git show dd414455d0bf46ebd8f098e1049bdef32edafa96:decisions/OWNER_DECISIONS.md | sed -n '1351,1700p'
git show dd414455d0bf46ebd8f098e1049bdef32edafa96:decisions/OWNER_DECISIONS.md | sed -n '1701,2050p'
git show dd414455d0bf46ebd8f098e1049bdef32edafa96:decisions/OWNER_DECISIONS.md | sed -n '2051,2400p'
git show dd414455d0bf46ebd8f098e1049bdef32edafa96:decisions/OWNER_DECISIONS.md | sed -n '901,1300p'
git show dd414455d0bf46ebd8f098e1049bdef32edafa96:decisions/OWNER_DECISIONS.md | sed -n '1301,1700p'

git show dd414455d0bf46ebd8f098e1049bdef32edafa96:docs/plan_arquitectura_gobernanza_multi_ia_v1.md | sed -n '251,550p'
git show dd414455d0bf46ebd8f098e1049bdef32edafa96:docs/plan_arquitectura_gobernanza_multi_ia_v1.md | sed -n '551,850p'
git show dd414455d0bf46ebd8f098e1049bdef32edafa96:docs/plan_arquitectura_gobernanza_multi_ia_v1.md | sed -n '851,1150p'

git show 749ab3c73383984a2f893236835387d20709c71c:reports/AI-GOV-F1-CANONICAL/MANDATE_AUDIT_CODEX.md
git show c30a7cb8f5cd26eccd8365cd50c53aff9fd7fa03:reports/AI-GOV-F1-CANONICAL/MANDATE_AUDIT_CODEX_R2.md
git show 71e61f8f66ceb3f5b457dc8c1c0927d83a9679ac:reports/AI-GOV-F1-CANONICAL/MANDATE_AUDIT_CODEX_R3.md

git diff --check
git status --short
git status --short --untracked-files=all
git diff --name-status
git diff --stat
git add -- reports/AI-GOV-F1-CANONICAL/MANDATE_AUDIT_CODEX_R4.md
git diff --cached --check
git diff --cached --name-status
git diff --cached --stat
git status --short
git commit -m "docs: reaudita mandato de Fase 1 (R4)"
git rev-parse HEAD
git rev-parse HEAD^
git diff-tree --no-commit-id --name-status -r HEAD
git show --check --stat --oneline HEAD
git status --short
```

Este informe se creó mediante `apply_patch`. Los comandos finales de
verificación, indexado, commit y cierre se ejecutan después de cerrar
su contenido; sus resultados efectivos se incluyen también en la
entrega externa.

## 5. Comprobación de alcance y cadena Git

El padre real del commit objetivo es exactamente:

```text
7c61c1ad56318186b126c93acb4f7c281a699a56
```

El diff exacto padre–objetivo modifica únicamente:

```text
M  tasks/AI-GOV-F1-CANONICAL/ACCEPTANCE.md
```

`tasks/AI-GOV-F1-CANONICAL/MANDATE.md` no cambió en R4. El diff de
`ACCEPTANCE.md` modifica exclusivamente el paso 4 de la vía normal de
A-21 y la fila A-21 de la matriz para incorporar N-05. No altera la
sustancia de H-01 a H-05 ni de N-01 a N-04.

`git show --check --stat --oneline` devolvió:

```text
aa96580 docs: corrige N-05 en cierre de Fase 1
```

No informó errores de whitespace.

## 6. Auditoría completa de `MANDATE.md`

### 6.1 Identificación, autoridad y ejecutabilidad

El mandato identifica repositorio objetivo, rama prevista, commit base
documental, archivos autorizados, prohibiciones y criterios de
aceptación. Separa implementador, auditor y autoridad final. No inventa
los dos SHA operacionales futuros: exige que una autorización posterior
de Miguel fije el commit base de implementación de
`CLAUDEBOT-CONTROL` y el commit inmutable de lectura de `CLAUDEBOT`; si
falta, no coincide o cambia cualquiera, ordena `BLOQUEAR`. Por ello no
es ejecutable todavía y no se autoautoriza.

### 6.2 Objetivo, permisos y rutas

La Capa A queda agnóstica de proyecto, modelo y dominio científico; la
Capa B añade restricciones de `CLAUDEBOT` sin relajar Capa A;
`AGENTS.md` conserva el papel de puerta e índice. La política de
adaptadores debe fijar ubicación, procedimiento, historial, roles,
estados y los cinco eventos, incluido el máximo de 90 días, sin crear
adaptadores en esta fase.

La escritura futura de Sonnet está cerrada a cinco rutas; la de Codex,
a su informe literal. La lectura en `CLAUDEBOT-CONTROL` y las cuatro
lecturas secundarias en `CLAUDEBOT` están enumeradas literalmente. Las
lecturas secundarias solo pueden hacerse con `git show` contra el SHA
completo autorizado, sin working tree móvil, enlaces, sustituciones,
datasets, CSV, resultados, código ni producción.

### 6.3 Huella de `CLAUDEBOT`

La excepción de huella está cerrada a dos comandos exactos. El segundo
usa `bash -o pipefail -c`; ambos deben devolver código `0`. Un fallo
invalida la captura y obliga a `BLOQUEAR`. El informe futuro solo puede
registrar HEAD, SHA-256 y códigos cero, nunca la salida textual de
`status` ni rutas derivadas.

La fuerza probatoria está correctamente acotada: la igualdad inicial y
final solo demuestra igualdad del estado Git observable en HEAD y
`status --porcelain=v1 -z` en ambos límites. No cubre ignorados ni
cambios transitorios restaurados; ampliar esa cobertura requiere una
autorización separada de Miguel.

### 6.4 Prohibiciones, coherencia y autorización

El mandato prohíbe modificar `CLAUDEBOT`, crear prematuramente
`judgment/`, `adapters/` o `tests/`, copiar Fable, ejecutar validación
conductual o ciencia, alterar fases científicas, ampliar rutas, hacer
push/merge/rebase/tags y congelar antes de auditoría y decisión final.
Declara expresamente que no autoriza implementación ni acciones
irreversibles. No se detectaron contradicciones internas, permisos
implícitos, rutas incompletas ni referencias móviles que impidan una
ejecución futura legítima.

## 7. Auditoría completa de `ACCEPTANCE.md`

`ACCEPTANCE.md` mantiene la separación temporal inequívoca:

- Etapa 1: A-01 a A-17 y A-20, sobre el commit de implementación;
- Etapa 2: A-18 y A-19, sobre el informe de auditoría ya versionado;
- Etapa 3: A-21, cierre posterior y separado.

A-18 y A-19 no alteran retroactivamente el veredicto histórico de la
Etapa 1; sí determinan si existe `APROBAR` vigente para cualquier paso
posterior. El informe queda fijado por ruta literal autorizada y commit
exacto propio.

A-21 conserva dos vías mutuamente excluyentes. La vía normal distingue
seis funciones de commit exactas y una acción de push. La vía
excepcional exige decisión, motivo, commit cerrado y evidencia negativa
local y remota reproducible con códigos `1`. No usa “entrada final” ni
“último commit” como evidencia móvil y no deja rutas `git show`
incompletas.

La corrección N-05 está incorporada materialmente en dos lugares:

1. la descripción normativa del paso 4 exige
   `git merge-base --is-ancestor <commit-de-implementación>
   <commit-de-integración>` y
   `git merge-base --is-ancestor <commit-de-integración> main`, ambos
   con código esperado `0`;
2. la fila A-21 de la matriz repite ambos comandos, sus relaciones y
   ambos códigos esperados `0`.

Ambas formulaciones prueban implementación → integración → `main`
local. A-21 mantiene el checkpoint inmediato posterior al push: SHA
local observado de `main`, SHA remoto observado de
`refs/heads/main` y commit de integración deben ser exactamente
iguales. En conjunto se prueba implementación → integración → `main`
local → `origin/main`. Se admite expresamente el fast-forward, donde
implementación e integración pueden ser el mismo commit. Los comandos
son reproducibles una vez que la operación posterior fija los SHA
completos.

Las búsquedas léxicas de la matriz son controles de apoyo y la lectura
manual es obligatoria para los aspectos semánticos. Los placeholders
identifican hechos futuros que deberán quedar fijados; no se aceptan
como evidencia hasta su sustitución por commits reales.

## 8. Evaluación individual de A-01 a A-21

`CONFORME`/`NO CONFORME` califican la calidad documental y
verificabilidad del criterio, no constituyen veredictos alternativos.

### Etapa 1 — A-01 a A-17 y A-20

| ID | Resultado | Evidencia | Reproducibilidad | Posibles falsos positivos | Posibles falsos negativos | Compatibilidad con `MANDATE.md` |
|---|---|---|---|---|---|---|
| A-01 | CONFORME | Diff base–objetivo y cinco rutas literales de Sonnet. | Dos SHA completos fijados por Miguel. | Ninguno apreciable si se validan los extremos. | Ninguno apreciable; cubre A/M/D en todo el intervalo. | Coincide con §3. |
| A-02 | CONFORME | Diff de `AGENTS.md`, blob final completo y ocho reglas enumeradas. | `git diff` y `git show` anclados. | Un enlace nominal podría parecer suficiente; la lectura semántica lo descarta. | El diff omite texto conservado, cubierto por la lectura final completa. | Conserva puerta, índice y reglas institucionales exigidas. |
| A-03 | CONFORME | Búsqueda de vocabulario de dominio en Capa A. | `git grep` contra el objetivo. | Usos negativos o descriptivos pueden coincidir. | Sinónimos no listados; A-05 exige lectura completa. | Satisface el agnosticismo exigido. |
| A-04 | CONFORME | Encabezados y lectura completa del núcleo institucional. | `git grep` y `git show` contra el objetivo. | Encabezados vacíos; mitigado por lectura manual. | Conceptos sin encabezado; los cubre la lectura completa. | Cubre autoridad, precedencia, permisos, alcance, estados/veredictos y conflictos. |
| A-05 | CONFORME | Lectura manual completa de Capa A. | Blob exacto mediante `git show`. | Una prohibición científica podría confundirse con regla de dominio. | Formulaciones indirectas exigen juicio semántico. | Prohíbe vocabulario científico como regla universal. |
| A-06 | CONFORME | Comparación completa del perfil y el núcleo. | Dos blobs del mismo objetivo. | Una reiteración más restrictiva podría parecer contradicción. | Una relajación implícita exige lectura semántica. | El perfil solo puede añadir restricciones. |
| A-07 | CONFORME | Define referencia normativa documental, la centraliza y revisa los cinco artefactos. | `git grep` anclado más revisión manual y lecturas completas complementarias. | SHA o menciones operacionales lícitas. | Una referencia que omita ambos patrones del grep; la lectura completa la cubre. | Coincide con la centralización normativa y las excepciones evidenciales de §5. |
| A-08 | CONFORME | Lectura completa del perfil; solo punteros, sin transcripción científica. | Blob exacto. | Una cita breve lícita podría parecer copia. | Paráfrasis sustantiva; A-14 añade diff y lectura manual. | Mantiene dominio y legado en `CLAUDEBOT`. |
| A-09 | CONFORME | Búsqueda de F-1A/F10/F11/T2 y revisión contextual. | `git grep` contra el objetivo. | Menciones descriptivas. | Apertura sin identificadores; la lectura completa del perfil la detecta. | No abre ni continúa fases científicas. |
| A-10 | CONFORME | Lectura completa y búsqueda auxiliar de campos, eventos, plazo, ubicación, procedimiento, historial, roles y estados. | Blob exacto. | Coincidencia léxica sin norma. | Sinónimos no buscados; la lectura completa manda. | Reproduce §2 del mandato y §14 del plan. |
| A-11 | CONFORME | Estado exacto y separación semántica de evidencia. | `git grep` fijo más lectura manual. | Mención sin definición. | Separación ambigua; la lectura semántica la detecta. | Evita sobreafirmar hipótesis. |
| A-12 | CONFORME | Lectura completa de la política; no concede permisos por hipótesis. | `git show` del blob exacto. | Una prohibición podría confundirse con permiso por lectura léxica. | Un permiso implícito requiere juicio manual. | No crea adaptadores ni amplía permisos. |
| A-13 | CONFORME | Diff sobre `judgment`, `adapters` y `tests`. | Diff base–objetivo con pathspecs literales. | Rutas históricas intactas no producen salida, correctamente. | Ninguno apreciable para cambios del intervalo bajo esas raíces. | Coincide con §4. |
| A-14 | CONFORME | Diff completo de los cinco artefactos y lectura manual. | Extremos fijados por SHA. | Una mención lícita a Fable puede parecer copia. | Paráfrasis sustantiva difícil de automatizar; exige juicio manual. | Coincide con la prohibición de copiar y sobreafirmar validación. |
| A-15 | CONFORME | Huellas inicial/final, códigos cero, privacidad y límites probatorios. | Informe anclado; comandos exactos con `pipefail`. | Un cambio concurrente ajeno puede bloquear conservadoramente. | Ignorados y cambios transitorios no se detectan; se declara el límite. | Reproduce la excepción cerrada de §3. |
| A-16 | CONFORME | Lectura manual de los comandos del informe. | Informe anclado al objetivo. | Una mención terminológica podría parecer ejecución. | Una acción omitida del informe; se mitiga con diff, rutas y huella. | Coincide con las prohibiciones científicas y conductuales. |
| A-17 | CONFORME | Secciones obligatorias, dos SHA, cuatro rutas, huellas y declaración negativa. | Informe y plantilla fijados por commits. | Secciones nominales sin datos; el esperado exige datos reales. | Omisiones deliberadas requieren contraste con comandos y diff. | Coincide con `AGENTS.md` §5 y §3. |
| A-20 | CONFORME | Tres blobs canónicos literales, `OWNER_DECISIONS.md` y diff completo. | Lecturas y extremos anclados. | Uso negativo de “congelado” puede parecer declaración. | Una fórmula equivalente requiere lectura semántica. | Nada se congela antes de auditoría y decisión final. |

### Etapa 2 — A-18 y A-19

| ID | Resultado | Evidencia | Reproducibilidad | Posibles falsos positivos | Posibles falsos negativos | Compatibilidad con `MANDATE.md` |
|---|---|---|---|---|---|---|
| A-18 | CONFORME | Ruta autorizada parametrizada, commit propio, SHA auditado y sección final con un único veredicto válido. | `git grep` de apoyo y `git show <commit-auditoría>:<ruta>` obligatorio. | Menciones históricas de los tres términos; decide la sección final. | Una variante podría escapar al grep; la lectura manual es obligatoria. | No condiciona retroactivamente Etapa 1 y sí integra `APROBAR` vigente. |
| A-19 | CONFORME | Mismo blob exacto; hallazgos contrastados con el veredicto. | `git show` contra commit y ruta fijados. | “Crítico” en una declaración negativa. | Severidad sustantiva mal rotulada; exige revisión manual. | Todo hallazgo crítico obliga a `BLOQUEAR`. |

### Etapa 3 — A-21

| ID | Resultado | Evidencia | Reproducibilidad | Posibles falsos positivos | Posibles falsos negativos | Compatibilidad con `MANDATE.md` |
|---|---|---|---|---|---|---|
| A-21 | CONFORME | Descripción normativa y matriz exigen las dos ancestrías con código `0`, checkpoint exacto local/remoto/integración, vía excepcional y commits exactos. | SHA completos, rutas literales, `merge-base`, `ls-remote`, `fetch` autorizado y registros durables. | Un registro que solo afirme éxito; los resultados esperados exigen comandos, SHA y códigos. | Un estado remoto posterior no sustituye el checkpoint inmediato; el criterio exige su registro durable. | Es posterior, no retroactivo, no autoriza por sí mismo y prueba implementación → integración → `main` local → `origin/main`. |

Conteo:

| Resultado | Cantidad |
|---|---:|
| CONFORME | 21 |
| NO CONFORME | 0 |

## 9. Evaluación individual de H-01 a H-05

| ID | Resultado | Evidencia | Consecuencia | Corrección exigida |
|---|---|---|---|---|
| H-01 | RESUELTO | `MANDATE.md` §3 distingue los dos artefactos redactados de la entrada separada y autorizada de `OWNER_DECISIONS.md`; coincide con la historia Git. | Ninguna residual. | Ninguna. |
| H-02 | RESUELTO | La matriz ancla A-02 a A-12 mediante `git show`/`git grep` y exige lectura completa para controles semánticos. | Ninguna residual. | Ninguna. |
| H-03 | RESUELTO | La excepción de huella autoriza solo dos comandos, protege salida/rutas, usa `pipefail`, exige códigos cero y acota la conclusión. | Ninguna residual. | Ninguna. |
| H-04 | RESUELTO | La separación en tres etapas elimina la circularidad; A-21 es posterior y A-18/A-19 no alteran el veredicto histórico. | Ninguna residual. | Ninguna. |
| H-05 | RESUELTO | A-20 enumera tres documentos `governance/` literales y usa el diff solo para descartar rutas adicionales. | Ninguna residual. | Ninguna. |

## 10. Evaluación individual de N-01 a N-04

| ID | Resultado | Evidencia | Consecuencia | Corrección exigida |
|---|---|---|---|---|
| N-01 | RESUELTO | A-07 define la categoría, centraliza las referencias normativas y revisa los cinco artefactos, diferenciando SHA y comandos evidenciales. | Ninguna residual; persiste juicio manual declarado. | Ninguna. |
| N-02 | RESUELTO | A-15 queda anclado al commit de implementación; A-18/A-19 se anclan al commit exacto de su informe en Etapa 2, sin retroactividad. | Ninguna residual. | Ninguna. |
| N-03 | RESUELTO | Mandato y A-15 usan `pipefail`, exigen códigos cero, bloquean ante fallo y limitan la conclusión a estados Git observables. | Ninguna residual; ignorados y cambios transitorios están fuera de cobertura declarada. | Ninguna. |
| N-04 | RESUELTO | A-21 distingue seis funciones de commit y una acción de push, exige integración, checkpoint, cierre posterior y vía excepcional reproducible. | Ninguna residual. | Ninguna. |

## 11. Evaluación individual de N-05

### Resultado: RESUELTO

- **Evidencia normativa:** el paso 4 de la vía normal de A-21 exige
  conjuntamente los dos comandos de ancestría, ambos con código de
  salida esperado `0`. No sustituye el control implementación →
  integración por el control integración → `main`; mantiene ambos.
- **Evidencia en la matriz:** la fila A-21 repite conjuntamente los dos
  comandos, las relaciones que cada uno prueba y los dos códigos
  esperados `0`.
- **Cadena probada:** el primer comando prueba implementación →
  integración; el segundo, integración → `main` local. El checkpoint
  posterior al push exige igualdad exacta entre `main` local observado,
  `refs/heads/main` remoto observado y el commit de integración. La
  combinación prueba implementación → integración → `main` local →
  `origin/main`.
- **Reproducibilidad:** los comandos tienen sintaxis completa y se
  ejecutan sobre los SHA que la operación posterior debe fijar. Los
  resultados esperados están definidos como códigos, no como una
  interpretación narrativa.
- **Fast-forward:** A-21 declara expresamente que implementación e
  integración pueden ser el mismo commit y que la primera ancestría se
  satisface trivialmente.
- **Consecuencia:** ninguna residual; se elimina el falso positivo que
  permitía presentar como integración un commit ya contenido en `main`
  pero ajeno al commit de implementación.
- **Corrección exigida:** ninguna.

## 12. Contradicciones, permisos, ejecutabilidad y reproducibilidad

- No se detectaron contradicciones entre `MANDATE.md` y
  `ACCEPTANCE.md`, ni entre la descripción de A-21 y su matriz.
- No se amplían permisos de lectura o escritura. Los comandos de cierre
  pertenecen a una operación posterior que requiere autorización
  propia; no autorizan su ejecución ahora.
- Los placeholders futuros están tipados por función y deben
  sustituirse por SHA completos reales; ninguna referencia móvil basta
  como evidencia durable.
- Las tres etapas evitan dependencias temporales circulares.
- La vía normal y la excepcional de A-21 son ejecutables y
  reproducibles dentro de sus futuras autorizaciones separadas.
- La corrección R4 no altera los controles de huella, alcance,
  referencias normativas, auditoría posterior ni cierre excepcional.
- La autoridad exclusiva de Miguel, el aislamiento de agentes, la
  taxonomía institucional y el bloqueo ante hallazgos críticos se
  mantienen íntegros.

## 13. Posibles falsos positivos y falsos negativos

| Control | Posible falso positivo | Posible falso negativo | Tratamiento |
|---|---|---|---|
| A-03/A-09/A-10/A-11 | Coincidencias descriptivas o negativas. | Sinónimos no buscados. | Lectura manual completa obligatoria. |
| A-07 | SHA o mención operacional lícita. | Referencia defectuosa sin ambos patrones. | Taxonomía explícita y lectura completa de los cinco artefactos. |
| A-14 | Mención lícita a Fable. | Paráfrasis sustantiva difícil de automatizar. | Diff completo y juicio manual dentro del alcance autorizado. |
| A-15 | Cambio concurrente ajeno entre capturas. | Ignorados o cambio transitorio restaurado. | Bloqueo conservador ante desigualdad y límites probatorios expresos. |
| A-18/A-19 | Términos históricos fuera de la sección final. | Severidad sustantiva mal rotulada. | Blob exacto y lectura manual del cierre y los hallazgos. |
| A-20 | Prohibición que contiene “congelado”. | Declaración equivalente con otro vocabulario. | Lectura semántica de blobs y decisiones. |
| A-21/N-05 | Un commit ajeno ya presente en `main` podría parecer integración si solo se probara integración → `main`. | Un estado remoto tardío podría ocultar el checkpoint real posterior al push. | Primera ancestría obligatoria implementación → integración, segunda integración → `main`, y checkpoint inmediato durable de igualdad exacta. |

Los riesgos residuales declarados no crean una contradicción ni impiden
obtener evidencia suficiente con la fuerza probatoria que cada criterio
declara.

## 14. Hallazgos nuevos y tabla de severidad

No se detectaron hallazgos nuevos.

| Severidad | Cantidad | Hallazgos abiertos |
|---|---:|---|
| Crítico | 0 | Ninguno |
| Mayor | 0 | Ninguno |
| Menor | 0 | Ninguno |

No existe severidad residual en H-01 a H-05 ni N-01 a N-05.

## 15. Declaraciones de alcance y negativas

- No se abrió ninguna ruta distinta de las diez enumeradas en §3.
- No se abrió, consultó ni modificó `CLAUDEBOT`.
- No se abrieron, consultaron ni usaron las ramas anteriores
  `audit/codex-ai-gov-f1-mandate`,
  `audit/codex-ai-gov-f1-mandate-r2` ni
  `audit/codex-ai-gov-f1-mandate-r3`.
- No se abrieron, consultaron ni usaron sus worktrees anteriores.
- De los tres commits históricos se leyeron únicamente los blobs
  literales de informe autorizados.
- No se abrieron datasets, CSV, resultados de discovery/OOS, código
  científico, producción ni fases científicas.
- No se inició, ejecutó ni auditó la implementación de la Fase 1.
- No se modificaron `MANDATE.md` ni `ACCEPTANCE.md`.
- No se modificaron `AGENTS.md`, `OWNER_DECISIONS.md`, `templates/`,
  `docs/` ni `governance/`.
- No se declaró implementado, integrado, congelado ni cerrado ningún
  artefacto de Fase 1.
- No se hizo push, merge, rebase ni se creó tag.
- No se borraron ramas ni worktrees.
- Este informe es el único archivo creado.

## 16. Archivo creado y estado Git

Creado exclusivamente:

```text
reports/AI-GOV-F1-CANONICAL/MANDATE_AUDIT_CODEX_R4.md
```

Antes del indexado, la comprobación expandida debe mostrar únicamente:

```text
?? reports/AI-GOV-F1-CANONICAL/MANDATE_AUDIT_CODEX_R4.md
```

El índice previo al commit debe contener exclusivamente:

```text
A  reports/AI-GOV-F1-CANONICAL/MANDATE_AUDIT_CODEX_R4.md
```

Después del único commit autorizado, el estado Git final debe ser y se
verifica como:

```text
[sin salida]
```

El hash completo, padre, diff-tree y resultado efectivo de
`git show --check` se verifican inmediatamente después del commit y se
incluyen en la entrega externa.

## 17. Veredicto final

```text
APROBAR
```

El mandato R4 puede pasar a evaluación posterior de autorización de
implementación sin nuevas correcciones documentales. A-01 a A-21 están
`CONFORME`; H-01 a H-05 y N-01 a N-05 están `RESUELTO`; no se
detectaron hallazgos nuevos ni severidades residuales.

Este veredicto no autoriza la implementación de la Fase 1 ni ninguna
acción irreversible. La implementación continúa pendiente de una
decisión posterior, expresa y durable de Miguel.
