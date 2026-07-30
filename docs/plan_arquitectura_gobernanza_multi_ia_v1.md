# Plan de arquitectura de gobernanza multi-IA v1

**Estado:** No aprobado. No validado. No implementado. Arquitectura de
cuatro capas y roles definitivos cerrados por decisión de Miguel
(2026-07-28); revisión de ChatGPT ronda 1 (2026-07-28) devolvió
**RECHAZAR PARA VERSIONADO — corregible** y fue corregida (§3, §4, §5.3,
§6, §10, §14, §15, §16, §18, §19); revisión de ChatGPT ronda 2
(2026-07-28) aprobó la arquitectura conceptualmente e identificó cuatro
correcciones cerradas y localizadas, aplicadas en la edición versionada
(§4.2, §6, §8, §9.1, §17, §17.1, §18).

**Historia fija (no se reescribe en ediciones posteriores):**
- versión inicial versionada: commit `abeccd1ed4757b5abda5cbc7a0a3aae49a2f1838`,
  rama `plan/ai-governance-v1`;
- auditoría inicial independiente: Codex, commit
  `c7db9a7616e75d502e556a43466762c8aa4623ca`, veredicto **RECHAZAR**
  (informe `docs/auditoria_codex_plan_arquitectura_gobernanza_multi_ia_v1.md`);
- registro durable de las decisiones arquitectónicas y de las
  autorizaciones operacionales de la Fase 0: commit
  `f00c42b626e49ed69816ca6847db164b28219b7d`
  (`decisions/OWNER_DECISIONS.md`, entrada del 2026-07-28);
- versión correctiva de H-01 a H-11: commit
  `a4b646b780c121598194d56793e6a54d816f8260`, rama
  `control/sonnet-ai-governance-v1-r1`;
- reauditoría independiente de esa versión: Codex, commit
  `8f5734849600c2f02231448422e82bea83671de5`, veredicto
  **RECHAZAR**; H-01 a H-11 quedaron cerrados y se abrió N-01 como
  único hallazgo MAYOR;
- decisión y autorización sustantiva para corregir N-01: commit
  `fe748558013fe6c8d42c1ec3fe7ba2360a160be2`;
- autorización de los ajustes de trazabilidad y del siguiente
  versionado correctivo: commit
  `04149b6b359d15b3ff79d95993205ddffac8752f`.

**Esta edición** conserva las correcciones H-01 a H-11, declaradas
cerradas por la reauditoría independiente de Codex versionada en el
commit `8f5734849600c2f02231448422e82bea83671de5`, e incorpora la
corrección documental del hallazgo N-01 en §9.

La decisión sustantiva y autorización para corregir N-01 está
registrada en el commit
`fe748558013fe6c8d42c1ec3fe7ba2360a160be2`; la ampliación acotada para
actualizar la trazabilidad de esta edición y crear el siguiente
versionado correctivo está registrada en el commit
`04149b6b359d15b3ff79d95993205ddffac8752f`.

La incorporación de esta corrección no declara N-01 cerrado ni
constituye `APROBAR`: requiere una nueva auditoría independiente de
Codex sobre el nuevo commit objetivo que contenga esta edición.

**Estado operativo vigente:** no se declara de forma estática en esta
cabecera; se determina en cada momento mediante el **commit objetivo**
definido en §17.1 (el último commit, en la rama de entrega
correspondiente, cuyo diff modifica este documento) y el veredicto de
la auditoría independiente más reciente sobre ese commit objetivo. Esta
edición, por sí sola, no constituye `APROBAR` vigente: exige una nueva
auditoría independiente de Codex sobre el commit objetivo que la
contenga.

Pendiente antes del inicio de la Fase 1: nueva auditoría independiente
de Codex sobre el commit objetivo de esta edición; ciclo de
corrección/re-auditoría (§17.1) hasta obtener `APROBAR` vigente; y
decisión expresa final de Miguel, registrada en
`decisions/OWNER_DECISIONS.md`, que autorice específicamente el inicio
de la Fase 1. **La Fase 1 no está autorizada por este documento.**
**Repositorio:** `CLAUDEBOT-CONTROL`
**Rama de entrega de esta edición:** `control/sonnet-ai-governance-v1-r2`
**No autoriza:** creación de carpetas, copia de archivos desde `CLAUDEBOT`,
commits, merges, push, ni continuación de F-1A, F10, F11 o T2 en `CLAUDEBOT`.

---

## 1. Objetivo y no objetivos

### Objetivo
Definir la arquitectura documental y de proceso con la que múltiples
agentes de IA (Sonnet, Codex, Gemini, ChatGPT u otros) colaboran bajo
gobernanza única en proyectos coordinados desde `CLAUDEBOT-CONTROL`,
separando de forma explícita en cuatro capas (§5):

- núcleo institucional universal (portable entre proyectos y modelos);
- gobernanza específica de cada proyecto coordinado (perfil, fases,
  documentos rectores propios);
- legado científico e histórico de un proyecto concreto (`CLAUDEBOT`,
  incluido el corpus Fable Judgment v1);
- ajustes específicos de cada modelo (adaptadores fechados).

### No objetivos de este plan
- No implementa la arquitectura (no crea `judgment/`, `adapters/`,
  `tests/`, `governance/` ni ninguna otra carpeta).
- No copia contenido de `CLAUDEBOT` a `CLAUDEBOT-CONTROL`.
- No modifica `AGENTS.md` ni las plantillas existentes.
- No valida, ejecuta ni califica el comportamiento de ningún modelo.
- No abre, continúa ni referencia como activas las fases científicas
  F-1A, F10, F11 ni T2 de `CLAUDEBOT`.
- No decide si `CLAUDEBOT` en sí adopta esta arquitectura; solo prepara
  el diseño para que, si se decide, exista un camino sin duplicar reglas
  científicas.

---

## 2. Autoridad final de Miguel

- Miguel es la única autoridad para: autorizar fases, aprobar merges a
  rama rectora, autorizar acciones irreversibles, aprobar la creación de
  las carpetas de esta arquitectura, y decidir sobre contradicciones que
  ningún agente pueda resolver por criterio documental.
- Ningún veredicto de ningún agente —incluido un consenso entre varios—
  sustituye esa autorización. Esto ya rige en `AGENTS.md` §1 y este plan
  no lo reabre; lo hereda como axioma.
- La autoridad de Miguel es la única capa de este diseño que no tiene
  adaptador ni versión: no se delega, no se aproxima, no se simula.

---

## 3. Git como fuente de verdad

- El estado válido de cualquier decisión, mandato, informe o adaptador es
  el que existe en el historial de git de `CLAUDEBOT-CONTROL` (o de
  `CLAUDEBOT` para lo científico), no lo que un agente recuerde o
  resuma de una conversación anterior.
- Toda afirmación operativa de un agente debe ser reproducible con un
  comando (`git log`, `git diff`, `git show`, hash de archivo). Un
  resumen sin commit citable vale como opinión, no como hecho — regla ya
  vigente en el legado Fable (`FABLE_CONSTITUTION.md` §5) y adoptada aquí
  como principio institucional, no como cita del legado.
- Un documento "vigente" es el que está en la rama rectora (`main`) o en
  el tag/commit que un documento superior cite explícitamente. Memorias,
  resúmenes o conversaciones de agentes **no son fuente duradera**: no
  tienen autoridad más allá de la sesión que las produjo hasta quedar
  versionadas.
- Una instrucción actual y explícita de Miguel, aunque exista solo en la
  conversación en curso, **sí puede autorizar trabajo reversible**
  (edición de un borrador, commit en rama propia sin merge) — es
  autorización operacional, no decisión institucional duradera
  (distinción completa en §4.1).
- Toda modificación de carácter normativo (que cambie una regla vigente,
  no solo el contenido de un borrador en curso) debe quedar
  **versionada mediante commit con autorización expresa** antes de
  integrarse a la rama rectora o darse por cerrada.
- Toda sesión de un agente empieza con un preflight de git (posición,
  rama, estado del árbol, sincronía con remoto) antes de proponer
  cambios. Este plan mismo se redactó tras ese preflight.

---

## 4. Jerarquía y precedencia documental

### 4.1 Dos tipos de autorización de Miguel

Antes de aplicar la precedencia, todo agente distingue dos cosas que no
deben confundirse:

**A. Autorización operacional actual.** Permite una acción concreta
dentro del alcance que declara (p. ej. "autorizo modificar únicamente
`docs/plan_...md`"). Puede existir inicialmente solo en la conversación
en curso. **No constituye por sí sola una regla institucional
permanente**: no se hereda automáticamente a sesiones futuras ni a otros
agentes mientras no quede registrada como decisión duradera (B).

**B. Decisión institucional duradera.** Debe registrarse y versionarse
(`decisions/OWNER_DECISIONS.md` u otro documento equivalente de Capa A/B
que la Fase 1 defina). Es la fuente estable que otras sesiones y agentes
pueden invocar después. Una autorización operacional (A) que Miguel
quiera convertir en regla duradera debe pasar por este registro;
mientras no lo haga, sigue siendo (A) y su alcance no se presume más
allá de la tarea o conversación que la originó.

### 4.2 Precedencia ante conflicto

En orden estricto (el superior gana ante conflicto):

1. **Autorización operacional actual de Miguel** (§4.1.A) para la
   acción concreta — no una autorización pasada ni una de alcance
   distinto.
2. **Decisiones institucionales duraderas ya registradas** (§4.1.B:
   `decisions/OWNER_DECISIONS.md` y equivalentes de Capa A/B).
3. **Núcleo institucional universal** (Capa A, §5.1) — reglas de
   gobernanza agnósticas de proyecto y de modelo.
4. **Gobernanza específica de proyecto** (Capa B, §5.2) — perfil y
   restricciones del proyecto que la tarea declare como objetivo; un
   perfil de proyecto puede añadir restricciones sobre la Capa A, nunca
   relajarlas.
5. **Mandato vigente de la tarea en curso** (`tasks/<ID>/MANDATE.md`).
6. **Adaptador del modelo actuante** (Capa D, §5.4 y §14) — matiza cómo
   aplicar lo anterior según fortalezas/debilidades conocidas de ese
   modelo.
7. **Instrucción conversacional que no constituya una autorización
   operacional actual y explícita de Miguel conforme a §4.1.A.** Si
   contradice los niveles 1-6, el agente señala el conflicto y propone
   la vía legítima (mandato nuevo o decisión de Miguel); no ejecuta
   primero.

### 4.2.1 Ubicación de documentos operativos y de evidencia

Para evitar ambigüedad sobre dónde se ubican documentos que el flujo de
trabajo usa constantemente, pero que no aparecían nombrados en la lista
anterior:

- **`AGENTS.md`** es la expresión operativa e índice de entrada de la
  Capa A (núcleo institucional universal): ocupa el **nivel 3**, junto
  con los documentos canónicos detallados de esa misma capa que la
  Fase 1 nombre y ubique (§5.1).
- **Perfiles de Capa B** (gobernanza específica de proyecto, §5.2):
  ocupan el **nivel 4**.
- **Mandatos** (`tasks/<ID>/MANDATE.md`): nivel 5, sin cambios.
- **Adaptadores por modelo** (Capa D, §5.4, §14): nivel 6, sin cambios.
- **`templates/`** (`TASK_TEMPLATE.md`, `REPORT_TEMPLATE.md`,
  `AUDIT_TEMPLATE.md`): son instrumentos de formato que instrumentan los
  niveles 3 a 5; no tienen precedencia normativa propia ni ocupan un
  nivel independiente en esta lista.
- **`README.md`**: es descriptivo del repositorio, no normativo; solo
  adquiere fuerza de precedencia si un documento normativo de los
  niveles 1-6 lo incorpora expresamente.
- **`STATUS.md`, informes (`*_REPORT.md`) y auditorías (`*_AUDIT.md`)**:
  son artefactos versionados de estado y de evidencia (§12); no ocupan
  un nivel normativo autónomo — su función es demostrar si se cumplió o
  no una condición de los niveles 1-6, nunca sustituirlos.

Si un artefacto de estado o de evidencia (informe, auditoría,
`STATUS.md`, historial de Git) demuestra que una condición exigida por
un nivel superior de la lista de §4.2 no fue satisfecha (p. ej., que no
existe la autorización que el nivel 1 requeriría, o que el mandato del
nivel 5 no fue aprobado), ese hecho **bloquea la transición
correspondiente**, con independencia de que ningún agente lo haya
declarado explícitamente como conflicto.

### 4.3 Regla de superación explícita

Una instrucción o autorización nueva de Miguel que contradiga una
decisión institucional duradera, una regla del núcleo institucional, un
perfil de proyecto, un mandato, un adaptador, o cualquier otra
restricción vigente en los niveles 2 a 6 de §4.2, **solo la supersede
cuando declare explícitamente**:

- la **excepción** que introduce;
- la **regla o documento concreto que reemplaza**;
- el **alcance** de ese reemplazo;
- la **duración**, cuando el reemplazo sea temporal (p. ej. limitado a
  una tarea, una fase o un plazo determinado).

Si la instrucción no declara estos cuatro elementos, el agente
**detiene la acción y solicita aclaración** — no infiere la superación
por implicación ni por presión conversacional, y no la aplica a un
mandato o adaptador vigente solo porque la autorización operacional
ocupe el nivel 1 de §4.2.

El legado y dominio (Capa C, §5.3), incluido el corpus Fable Judgment
v1, **no son documentos congelados con precedencia institucional
global** sobre `CLAUDEBOT-CONTROL`: no ocupan ningún nivel de la lista
de §4.2. Son vinculantes únicamente dentro de tareas que declaren
explícitamente el repositorio de origen correspondiente (p. ej.
`CLAUDEBOT`) como objetivo, y solo bajo las reglas propias de ese
repositorio.

---

## 5. Arquitectura de cuatro capas

La capa de proyecto (Capa B) es **obligatoria**: permite que
`CLAUDEBOT-CONTROL` gobierne más de un repositorio sin mezclar las
reglas particulares de cada uno. Sin ella, cualquier regla específica de
`CLAUDEBOT` tendería a filtrarse como si fuera universal.

```
Capa A — Núcleo institucional universal
  Autoridad, precedencia documental, permisos, control de alcance,
  veredictos, resolución de conflictos. Agnóstica de proyecto y de
  modelo: no menciona trading, datasets ni ningún dominio científico.
  Vive en CLAUDEBOT-CONTROL.

Capa B — Gobernanza específica de proyecto
  Perfil y restricciones de cada proyecto coordinado, documentos
  rectores propios, fases autorizadas, rutas y artefactos propios, y
  relación explícita con el núcleo universal. Obligatoria desde que
  exista más de un repositorio gobernado. Vive en CLAUDEBOT-CONTROL.

Capa C — Legado y dominio
  Evidencia histórica, ADR, reglas científicas, corpus Fable
  Judgment v1. Permanece en su repositorio de origen; se referencia
  por puntero (repositorio + tag/commit + ruta), nunca se copia
  íntegro fuera de él.

Capa D — Adaptadores por modelo
  Traducción de las capas A-C al comportamiento operativo de cada
  modelo, con versión y fecha, limitaciones conocidas y pruebas de
  regresión propias. Vive en CLAUDEBOT-CONTROL y se revisa según los
  eventos de §14.
```

### 5.1 Capa A — Núcleo institucional universal
Contenido:

- **autoridad** — quién decide qué (§2);
- **precedencia documental** — orden de resolución ante conflicto (§4);
- **permisos** — lectura/escritura por objeto (§10);
- **control de alcance** — enumeración de archivos autorizados, diff
  debe coincidir con el mandato, hallazgo fuera de alcance se reporta
  sin tocar (patrón guardián de alcance, ya vigente en `AGENTS.md` §4);
- **veredictos** — taxonomía APROBAR/RECHAZAR/BLOQUEAR y estados de
  tarea (§9);
- **resolución de conflictos** — entre documentos, entre capas, entre
  agentes (§13).

No incluye nada que mencione datasets, discovery, OOS, quintiles ni
terminología de un dominio científico concreto — eso es Capa C.

**Rol de `AGENTS.md`:** `AGENTS.md` sigue siendo el punto de entrada
obligatorio, el resumen de autoridad y prohibiciones críticas, y el
índice hacia los documentos canónicos de esta capa. No se fusiona el
contenido detallado de la Capa A dentro de `AGENTS.md`; los documentos
separados (a nombrar y ubicar en el mandato de la Fase 1, §17) son la
fuente normativa detallada. Este plan no modifica `AGENTS.md` — esa
edición pertenece a la Fase 1, bajo su propio mandato.

### 5.2 Capa B — Gobernanza específica de proyecto
Un perfil por repositorio coordinado desde `CLAUDEBOT-CONTROL` (hoy:
`CLAUDEBOT`; en el futuro, cualquier otro que Miguel decida coordinar
aquí). Cada perfil declara:

- **perfil y restricciones propias del proyecto** (p. ej., para
  `CLAUDEBOT`: producción intocable, prohibición de abrir datasets sin
  autorización específica, guard OOS);
- **documentos rectores vigentes de ese proyecto** (p. ej.
  `docs/estado_rector_post_f8.md` en `CLAUDEBOT`);
- **fases autorizadas y su estado** (p. ej. F-1A, F10, F11, T2 —
  ninguna abierta ni continuada por este plan);
- **rutas y artefactos propios** — dónde viven los mandatos, informes y
  documentos congelados de ese proyecto;
- **relación con el núcleo universal** — qué hereda de la Capa A sin
  modificación y qué restringe adicionalmente. Un perfil de proyecto
  puede añadir restricciones sobre la Capa A; nunca puede relajarlas
  (mismo principio de precedencia de §4).

Ubicación física de los perfiles: a definir en el mandato de la Fase 1
(§17), no en este documento.

### 5.3 Capa C — Legado y dominio
Contenido de `CLAUDEBOT`: evidencia histórica (`docs/`, `archive/`),
ADR-001 a ADR-010, reglas científicas (pre-registro, ceguera,
discovery/OOS, criterios estadísticos de campaña), skills de
`preregistro-hipotesis`, `corrida-unica`, `verificacion-dataset`,
`auditoria-laboratorio`, `postmortem-archivo`, y el corpus Fable
Judgment v1 completo.

**Política v1 de procedencia (sin copia):**

- el corpus original permanece íntegro en `CLAUDEBOT`; no se copia a
  `CLAUDEBOT-CONTROL` bajo ninguna forma, incluida la de un "espejo
  congelado";
- `CLAUDEBOT-CONTROL` conserva únicamente un **manifiesto de
  procedencia** por cada elemento de esta capa que otras capas
  necesiten citar: repositorio, tag/commit, rutas, y hash de archivo
  cuando corresponda verificarlo;
- las reglas clasificadas como universales se reformulan sin
  vocabulario de dominio dentro de la Capa A, con trazabilidad
  explícita al manifiesto de origen (ver §6);
- una copia completa (espejo) del corpus, si se decide en el futuro,
  requiere una **decisión arquitectónica y una auditoría propias**,
  separadas de este plan y de su Fase 1 — no queda autorizada ni
  prevista por defecto.

Ver tratamiento detallado del caso Fable Judgment v1 en §6.

### 5.4 Capa D — Adaptadores por modelo
Un documento por modelo, fechado y versionado, que traduce las capas
A-C al comportamiento operativo observado de ese modelo concreto (ver
§14 para requisitos y §15 para pruebas de regresión). El primero a
redactar —en una fase posterior, no en esta— sería
`SONNET_FABLE_ADAPTER.md`.

---

## 6. Tratamiento de Fable Judgment v1

Fable Judgment v1 es el caso concreto que hoy ocupa la Capa C (legado y
dominio, §5.3) de este plan.

Aclaración terminológica vinculante para todo el plan y para cualquier
adaptador futuro: **Fable Judgment v1 es un sistema documental
transferible de juicio, independiente del proveedor del modelo.** No se
afirma, y ningún documento derivado de este plan puede afirmar, que:

- Sonnet es Fable;
- Fable es necesariamente un modelo específico;
- el comportamiento descrito ya fue validado mediante benchmark aislado.

Lo que sí se registra como hecho verificado directamente en el
historial de `CLAUDEBOT` — cada fila indica el comando o la ruta
reproducible que la sustenta, sin depender de ningún resumen previo:

| Hecho | Cómo verificarlo |
|---|---|
| El corpus documental existe | `git -C CLAUDEBOT ls-tree -r fable-judgment-v1 --name-only -- ai_judgment/` lista `FABLE_CONSTITUTION.md`, `FABLE_DECISION_MODEL.md`, `FABLE_FAILURE_PATTERNS.md`, `FABLE_HANDOFF_PROMPT.md`, `MODEL_ADAPTER_CLAUDE.md`, `MODEL_ADAPTER_CODEX.md`, `MODEL_ADAPTER_GPT.md`, `TRANSFER_COVERAGE_REPORT.md` y `ai_judgment/decisions/ADR-001` a `ADR-010` |
| Está versionado mediante el tag `fable-judgment-v1` | `git -C CLAUDEBOT tag -l fable-judgment-v1` (existe) y `git -C CLAUDEBOT cat-file -t fable-judgment-v1` (`tag`, es decir, objeto anotado) |
| Su commit rector es `3a749d43d1ece2260ab5a1f1b89460a78d330c9c` | `git -C CLAUDEBOT rev-parse 'fable-judgment-v1^{commit}'` — verificable mediante el comando indicado |
| La transferencia documental está implementada | `git -C CLAUDEBOT show 3a749d43d1ece2260ab5a1f1b89460a78d330c9c --stat` (merge que integra `ai_judgment/`, `evals/` y `.claude/skills/`) |
| La validación conductual aislada sigue pendiente | `git -C CLAUDEBOT show 3a749d43d1ece2260ab5a1f1b89460a78d330c9c:ai_judgment/TRANSFER_COVERAGE_REPORT.md`, §4: declara el benchmark aislado no ejecutado |

El manifiesto definitivo de procedencia, con hash por archivo, se
produce recién en la Fase 2 (§17); esta tabla registra únicamente lo
verificable hoy a nivel de commit/tag.

### Procedencia
Repositorio `CLAUDEBOT`, tag `fable-judgment-v1`, commit
`3a749d43d1ece2260ab5a1f1b89460a78d330c9c`, 2026-07-19. Toda referencia
futura debe citar estos tres identificadores juntos, con el commit en
SHA completo; citar solo el nombre "Fable" sin tag ni commit, o citar un
SHA abreviado, no es una referencia válida bajo este plan.

### Inmutabilidad
El corpus en su commit rector no se reescribe ni se resume con pérdida
fuera de `CLAUDEBOT`. Si `CLAUDEBOT` evoluciona el corpus (v2), ese es un
tag nuevo; este plan y sus adaptadores deben citar explícitamente qué
versión usan.

### Qué se referencia
Desde `CLAUDEBOT-CONTROL`: un **manifiesto de procedencia** (no un
espejo del contenido) con repositorio + tag/commit + ruta + hash de
archivo cuando corresponda verificarlo (política general de Capa C,
§5.3). Ejemplo de forma válida de cita: *"criterio derivado de
`CLAUDEBOT` tag `fable-judgment-v1` (commit
`3a749d43d1ece2260ab5a1f1b89460a78d330c9c`),
`ai_judgment/FABLE_DECISION_MODEL.md` §0.1"*.

### Qué se extrae (en una fase posterior, no en esta)
Únicamente los elementos clasificados como universales en el inventario
previo: taxonomía de veredictos, jerarquía de prioridad ante conflicto,
afirmación-vs-prueba, reflejo ante anomalías, patrón de
alcance-enumerado, metodología de evaluación aislada de modelos. Se
extraen **reformulados sin vocabulario de dominio**, no copiados
literalmente.

### Qué no se copia
ADR-001 a ADR-010 completos (son estudios de caso de trading, no reglas
portables), los checklists de `corrida-unica`/`verificacion-dataset`
(activan permisos sobre datasets que `CLAUDEBOT-CONTROL` tiene prohibido
tocar por su propio `AGENTS.md` §7), y ningún fragmento que dé a entender
que un modelo "es" Fable en vez de "aplica criterio derivado de Fable".

---

## 7. Roles definitivos

### Miguel
- Propietario del sistema.
- Única autoridad para acciones irreversibles.
- Decide excepciones, integración y cierre.

### ChatGPT
- Arquitectura, metodología y evaluación crítica.
- Síntesis para decisión de Miguel.
- No escribe en repositorios salvo autorización expresa.
- No tiene autoridad final sobre Miguel.

### Sonnet
- Analista, planificador e implementador.
- Puede redactar y modificar únicamente dentro del mandato autorizado.
- No puede emitir aprobación definitiva sobre su propia implementación.

### Codex
- Auditor independiente y red team.
- Audita artefactos ya versionados.
- No implementa la solución que debe auditar.
- Utiliza APROBAR, RECHAZAR o BLOQUEAR conforme a las reglas
  documentadas (§9).

### Gemini
- Investigación, contraste documental y análisis de mecanismos.
- Lectura por defecto.
- Cualquier escritura requiere autorización expresa y alcance
  delimitado.

### Autonomía
La autonomía de un agente **no se asigna por historial disponible**.
Depende de tres factores combinados en cada caso: el rol del agente
(arriba), el mandato vigente de la tarea (§8), y el riesgo de la acción
concreta (irreversible vs. reversible, §11). Un agente sin historial
previo en un repositorio no recibe automáticamente autonomía baja; recibe
la autonomía que su rol y el riesgo de la tarea concreta justifiquen, con
la misma exigencia de evidencia citable que a cualquier otro.

Regla transversal: ningún agente audita su propio trabajo como única
verificación (`AGENTS.md` §2, ya vigente; y explícito arriba para
Sonnet/Codex); esta arquitectura no la relaja.

---

## 8. Flujo

```
intake → planificación → autorización → implementación → auditoría → integración → cierre
```

1. **Intake** — Miguel o un agente registra la necesidad; se identifica
   repositorio objetivo y qué capas toca: núcleo institucional (A),
   gobernanza de proyecto (B), legado (C), o varias a la vez.
2. **Planificación** — se redacta un mandato (`tasks/<ID>/MANDATE.md`)
   con archivos autorizados, prohibiciones y criterios de aceptación.
   Ningún agente ejecuta durante esta etapa. El primer borrador de
   `MANDATE.md` de una tarea nueva es una acción **reversible** que no
   ejecuta el mandato: puede redactarlo cualquier agente bajo
   **autorización operacional actual y explícita de Miguel** (§4.1.A)
   para esa tarea concreta, que delimite desde ese momento la tarea, la
   rama y el archivo — igual que este propio plan se redactó antes de
   estar versionado. El borrador no habilita ejecutar su contenido;
   solo la autorización posterior de Miguel (paso 3) lo permite.
3. **Autorización** — Miguel aprueba el mandato explícitamente. Sin esto,
   la etapa siguiente no puede comenzar (BLOQUEAR, no RECHAZAR).
4. **Implementación** — el agente asignado trabaja en su propia rama o
   worktree, dentro del alcance enumerado.
5. **Auditoría** — un agente distinto del implementador revisa el diff
   contra el mandato y produce un informe de auditoría propio, sin editar
   el original.
6. **Integración** — una entrega solo puede integrarse cuando se cumplen,
   todas a la vez:
   - el informe de auditoría independiente está versionado;
   - el informe cita el commit exacto auditado;
   - el veredicto vigente sobre ese commit es `APROBAR`;
   - no existe ningún hallazgo bloqueante abierto;
   - Miguel autoriza el merge explícitamente.
   Un veredicto `RECHAZAR` o `BLOQUEAR` impide la integración, aunque no
   exista un hallazgo etiquetado como crítico.
7. **Cierre** — informe final con declaraciones negativas verificables
   (qué no se tocó) y registro en `decisions/OWNER_DECISIONS.md` si hubo
   una decisión de Miguel.

Un hallazgo crítico en cualquier etapa detiene el avance hasta resolución
explícita, sin importar cuántas etapas anteriores ya se completaron
(hereda `AGENTS.md` §3, no lo reabre).

---

## 9. Estados y veredictos permitidos

**Veredictos de auditoría** (ya fijados en `AGENTS.md` §1, este plan los
hereda sin variación):

```
APROBAR
RECHAZAR
BLOQUEAR
```

Sin estados intermedios. La clasificación entre `BLOQUEAR` y
`RECHAZAR` se determina mediante las siguientes reglas, registradas por
decisión de Miguel en el commit
`fe748558013fe6c8d42c1ec3fe7ba2360a160be2` y alineadas con
`AUDIT_TEMPLATE.md` §7:

1. Corresponde `BLOQUEAR` cuando se cumple al menos una de estas
   condiciones:

   - falta la autorización vigente indispensable para ejecutar o
     continuar la acción evaluada;
   - falta evidencia indispensable para identificar legítimamente el
     objeto, el alcance o la continuidad de la auditoría;
   - la ausencia de evidencia impide completar legítimamente la
     auditoría;
   - existe un hallazgo `CRÍTICO`.

2. Corresponde `RECHAZAR` cuando el artefacto puede auditarse
   completamente y la ausencia o insuficiencia del registro documental
   de una autorización anterior, o de otra evidencia obligatoria,
   constituye un defecto no crítico y corregible que no impide
   completar la auditoría.

3. Que un artefacto sea completamente auditable no autoriza
   retroactivamente una acción ni subsana la falta documental. Un
   veredicto `RECHAZAR` impide aprobar, integrar o continuar el avance
   hasta que la deficiencia sea corregida y el nuevo commit sea
   auditado independientemente.

4. Cuando el mismo hallazgo constituya simultáneamente un
   incumplimiento definitivo y un hallazgo `CRÍTICO`, prevalece
   `BLOQUEAR`.

5. Un incumplimiento definitivo no crítico de una regla congelada
   continúa produciendo `RECHAZAR`.

Esta distinción mantiene coherencia con `AUDIT_TEMPLATE.md` §7 y con el
precedente histórico de la auditoría inicial: las deficiencias
documentales no críticas dentro de un artefacto completamente auditable
pueden producir `RECHAZAR`, mientras la imposibilidad legítima de
continuar o cualquier hallazgo `CRÍTICO` obliga a `BLOQUEAR`.

**Estados de tarea** (nuevo, propuesto para esta arquitectura):

```
INTAKE → PLANIFICADA → AUTORIZADA → EN IMPLEMENTACIÓN →
EN AUDITORÍA → INTEGRADA → CERRADA
```

con un estado transversal `BLOQUEADA` (puede aplicarse desde cualquier
etapa) y `DETENIDA POR INCIDENTE` (anomalía irregular: lock, residuo,
contradicción documental — nunca se limpia sola, requiere decisión de
Miguel para reanudar).

### 9.1 Relación con `STATUS.md` y `templates/TASK_TEMPLATE.md`

Los estados de tarea propuestos **complementan** las plantillas
existentes; no las reemplazan. Hoy `templates/` no tiene un
`STATUS_TEMPLATE.md` propio — el `README.md` lo menciona en la estructura
de carpetas, pero los únicos vocabularios de estado ya definidos y
vigentes están en `REPORT_TEMPLATE.md` §8 (veredicto de la entrega) y
`AUDIT_TEMPLATE.md` §7 (veredicto de auditoría). La tabla siguiente
mapea esos estados actuales contra los propuestos:

| Estado actual (plantillas vigentes) | Estado propuesto equivalente | Transición permitida | Responsable |
|---|---|---|---|
| Sin `STATUS.md` formal; necesidad registrada | `INTAKE` | (inicio) → `INTAKE` | Miguel o el agente que detecta la necesidad |
| `MANDATE.md` redactado (`templates/TASK_TEMPLATE.md`), sin la §6 "Autorización" confirmada | `PLANIFICADA` | `INTAKE` → `PLANIFICADA` | Agente planificador |
| `MANDATE.md` con autorización de Miguel confirmada | `AUTORIZADA` | `PLANIFICADA` → `AUTORIZADA` | Miguel (único) |
| Trabajo en curso en rama propia; sin `*_REPORT.md` entregado | `EN IMPLEMENTACIÓN` | `AUTORIZADA` → `EN IMPLEMENTACIÓN` | Agente implementador asignado |
| `*_REPORT.md` entregado (`REPORT_TEMPLATE.md` §8: `COMPLETADO` / `COMPLETADO CON OBSERVACIONES`), pendiente de auditoría | `EN AUDITORÍA` | `EN IMPLEMENTACIÓN` → `EN AUDITORÍA` | Agente implementador entrega; auditor asignado la recibe |
| `*_AUDIT.md` con veredicto `APROBAR` (`AUDIT_TEMPLATE.md` §7) | `INTEGRADA` (tras merge autorizado) | `EN AUDITORÍA` → `INTEGRADA` | Auditor emite veredicto; Miguel autoriza el merge |
| `*_AUDIT.md` con veredicto `RECHAZAR` | vuelve a `EN IMPLEMENTACIÓN` (nueva entrega) | `EN AUDITORÍA` → `EN IMPLEMENTACIÓN` | Miguel decide la reapertura |
| `*_REPORT.md` o `*_AUDIT.md` con veredicto `BLOQUEAR` | `BLOQUEADA` (transversal) | Desde cualquier estado | Quien detecta la falta de autorización o evidencia |
| Anomalía (lock, residuo, contradicción) sin plantilla actual dedicada | `DETENIDA POR INCIDENTE` (transversal, nuevo) | Desde cualquier estado | Quien detecta la anomalía; reanuda solo Miguel |
| Entrada nueva en `decisions/OWNER_DECISIONS.md` que cierra la tarea | `CERRADA` | `INTEGRADA` → `CERRADA` (o `EN AUDITORÍA` → `CERRADA` si no requiere integración) | Miguel |

La transición `EN AUDITORÍA` → `INTEGRADA` sigue exactamente la puerta
de integración de §8: informe de auditoría versionado, que cite el
commit exacto auditado, con veredicto vigente `APROBAR`, sin ningún
hallazgo bloqueante abierto, y autorización expresa de Miguel para el
merge. Un veredicto `RECHAZAR` o `BLOQUEAR` bloquea esta transición
aunque ningún hallazgo esté etiquetado como crítico.

**Salida de los estados transversales.** Ni `BLOQUEADA` ni
`DETENIDA POR INCIDENTE` se levantan por iniciativa de un agente:

- El estado de retorno es el **último estado válido anterior** al
  bloqueo o al incidente. Ese estado se determina mediante el
  **historial de Git y los artefactos versionados** (mandatos,
  informes, auditorías) — `STATUS.md` **no** es la fuente exclusiva
  para determinarlo.
- `STATUS.md` se actualiza **después**, para reflejar el estado ya
  verificado en Git. Si `STATUS.md` contradice lo que Git y los
  artefactos versionados indican, **prevalece Git**, conforme a §12.
- La autoridad para reanudar, en ambos casos, es **exclusiva de
  Miguel**.
- Evidencia exigida para levantar `BLOQUEADA`: registro de la
  autorización o evidencia que faltaba y que motivó el bloqueo (nueva
  autorización expresa de Miguel, o un nuevo commit que la aporta). Si
  el bloqueo se originó en un veredicto `BLOQUEAR` sobre una entrega,
  el reingreso exige una **nueva auditoría independiente** sobre el
  commit corrector, mismo ciclo B-E de §17.1.
- Evidencia exigida para levantar `DETENIDA POR INCIDENTE`: registro de
  la resolución de la anomalía (lock liberado, residuo eliminado,
  contradicción resuelta conforme a §13), citando el commit o la acción
  concreta que la resuelve.

**`EN AUDITORÍA` → `CERRADA` sin integración.** Solo es legítimo cuando
se cumplen, todas a la vez:

- Miguel decide expresamente cerrar la tarea sin fusionar el cambio a
  rama rectora;
- esa decisión y su motivo quedan registrados en
  `decisions/OWNER_DECISIONS.md`;
- el artefacto correspondiente no se integra a la rama rectora;
- esta vía no se interpreta, en ningún caso, como una excepción a la
  puerta de integración de §8.6 — cerrar sin integrar no es integrar.

La sustitución o migración formal de `STATUS.md`/`templates/TASK_TEMPLATE.md`
para incorporar este vocabulario de estados **es una decisión posterior y
auditada**, fuera del alcance de este plan y de su Fase 1.

---

## 10. Permisos de lectura y escritura

| Objeto | Lectura | Escritura |
|---|---|---|
| `CLAUDEBOT-CONTROL` núcleo institucional (Capa A) y perfiles de proyecto (Capa B) | Todos los agentes | Solo mediante mandato autorizado, en rama propia |
| `CLAUDEBOT-CONTROL/tasks/`, `reports/` | Todos los agentes | Solo el agente expresamente autorizado por el mandato de esa tarea, únicamente en la ruta enumerada (`tasks/<ID>/...`, `reports/<ID>/...`), en su propia rama, y sin editar el artefacto del rol distinto (el auditor crea su propio informe; no modifica la implementación que audita) — ver nota 1 |
| `CLAUDEBOT-CONTROL/decisions/OWNER_DECISIONS.md` | Todos los agentes | Solo se agrega (append), nunca se edita entrada previa. Miguel toma la decisión; Miguel puede redactar la entrada directamente o autorizar expresamente a un agente para transcribirla — el agente no crea ni interpreta una decisión nueva, solo la documenta, en la rama y el archivo expresamente autorizados, y solo tras revisar el diff antes del commit — ver nota 2 |
| Legado `CLAUDEBOT` (`ai_judgment/`, ADR, skills) | Lectura libre por referencia | Ningún agente lo edita desde una tarea de `CLAUDEBOT-CONTROL` |
| Datasets, resultados, producción de `CLAUDEBOT` | Ningún agente, desde ninguna tarea de `CLAUDEBOT-CONTROL` | Ninguno (fuera de alcance total, `AGENTS.md` §7 ya vigente) |
| Adaptadores por modelo | Todos los agentes | Pertenecen al sistema de gobernanza, no a ningún modelo (§14): cualquier agente autorizado propone actualizaciones; el modelo descrito puede aportar evidencia pero no aprobar su propio adaptador; un agente independiente audita el cambio; Miguel aprueba la versión nueva |

Nota 1: la autorización para escribir en `tasks/`/`reports/` proviene
siempre de un mandato vigente (`tasks/<ID>/MANDATE.md`) o, para el
primer borrador de ese mismo mandato, de una autorización operacional
actual y explícita de Miguel (§4.1.A, §8).

Nota 2: la autorización para materializar una entrada en
`decisions/OWNER_DECISIONS.md` es siempre una autorización operacional
actual y explícita de Miguel para esa entrada concreta (§4.1.A); no se
infiere de un mandato general ni de una autorización de fase.

---

## 11. Política de ramas, commits, merges y acciones irreversibles

- Convención de ramas de `AGENTS.md` §6 (ya vigente):
  `control/task-<id>`, `control/sonnet-<id>`, `control/codex-<id>`,
  `control/gemini-<id>`.
- Excepciones operacionales de la Fase 0, registradas en
  `decisions/OWNER_DECISIONS.md` (commit
  `f00c42b626e49ed69816ca6847db164b28219b7d`): `plan/<nombre>-v<N>`
  (rama de planificación de este documento; precedente:
  `plan/ai-governance-v1`) y `audit/<agente>-<nombre>-v<N>` (rama de
  auditoría independiente; precedente:
  `audit/codex-ai-governance-v1`). Estas dos familias **no** forman
  parte permanente de `AGENTS.md` §6; su posible incorporación
  definitiva queda reservada para una decisión posterior.
- Cada entrega termina en un commit identificable en la rama propia del
  agente. Ningún commit oportunista fuera del alcance del mandato.
- Merge a rama rectora: solo con autorización explícita de Miguel, nunca
  por consenso entre agentes.
- Acciones irreversibles (push, merge a rama rectora, tags, borrado de
  ramas, cualquier acción sobre `CLAUDEBOT` que toque datasets o
  producción): requieren autorización literal para esa acción concreta;
  una autorización de fase no las cubre implícitamente.
- Ante un lock, residuo o estado git inesperado: congelar, documentar,
  escalar a Miguel. Nunca limpiar ni reintentar por iniciativa propia
  (reflejo ya vigente, heredado como principio institucional).

---

## 12. Handoffs y estado único del proyecto

- El estado único y vigente de cualquier tarea es el que resulta de leer
  `tasks/<ID>/STATUS.md` + el historial git real, no el resumen que un
  agente entregue al siguiente.
- Un handoff entre agentes (o entre sesiones del mismo agente) debe
  incluir: commit exacto, rama, mandato vigente, y qué NO se ha hecho
  todavía — nunca solo un resumen de intención.
- Si existen dos fuentes de estado que se contradicen (p. ej. un
  `STATUS.md` desactualizado contra el estado real del repo),
  **prevalece el historial de git y los artefactos versionados** sobre
  `STATUS.md`. La contradicción se reporta y se corrige antes del
  cierre de la tarea; no se resuelve solo actualizando `STATUS.md` sin
  dejar registro de qué decía antes y por qué estaba desactualizado
  (§13).
- No existe un "estado mental" del proyecto fuera de git: la memoria de
  un agente entre sesiones no es fuente de verdad (§3).

---

## 13. Resolución de contradicciones documentales

Orden de resolución cuando dos documentos se contradicen:

1. Verificar si uno de los dos está obsoleto/supersedido explícitamente
   (patrón ya usado en `CLAUDEBOT`: `estado_actual_claudebot.md` vs
   `estado_rector_post_f8.md`). Si lo está, gana el vigente.
2. Si ambos parecen vigentes, aplica la jerarquía de precedencia (§4):
   gana el nivel superior.
3. Si la contradicción es dentro del mismo nivel (p. ej. dos mandatos
   activos con instrucciones incompatibles), el agente detiene el avance,
   documenta la contradicción explícitamente y escala a Miguel. Ningún
   agente elige por sí mismo cuál documento "tiene más sentido".
4. Toda contradicción resuelta por Miguel se registra en
   `decisions/OWNER_DECISIONS.md`, nunca se resuelve solo de palabra en
   una conversación no versionada.

---

## 14. Adaptadores de modelos fechados y versionados

- Cada adaptador (`ADAPTER_<MODELO>.md`, ubicación a definir en la fase
  de implementación, no en esta) declara en su encabezado: fecha de
  redacción, versión, y el commit/tag del corpus institucional y del
  legado que usó como base.
- Un adaptador describe fortalezas y debilidades **con evidencia
  citable** (commit, informe de auditoría), nunca genéricas — mismo
  estándar que `MODEL_ADAPTER_CLAUDE.md`/`_CODEX.md` ya demostraron en
  `CLAUDEBOT`.
- Los adaptadores **pertenecen al sistema de gobernanza, no a ningún
  modelo** (mismo principio en la tabla de permisos, §10). Cualquier
  agente autorizado puede proponer una actualización; el modelo
  descrito por el adaptador puede aportar evidencia sobre sí mismo,
  pero **no puede aprobar su propio adaptador**; un agente independiente
  audita el cambio propuesto; Miguel aprueba la versión nueva.
- Un adaptador sin historial propio del modelo (caso Gemini hoy, caso
  `MODEL_ADAPTER_GPT.md` en su momento) marca explícitamente cada
  fortaleza o debilidad esperada como **HIPÓTESIS NO VALIDADA**, en una
  sección separada de la evidencia observada — nunca mezcladas en la
  misma lista o tabla. Una hipótesis no validada **no puede, por sí
  sola, modificar permisos, autonomía ni decisiones de riesgo alto**: la
  autonomía real sigue el criterio de rol/mandato/riesgo de §7, no el
  contenido de la hipótesis. En cuanto exista evidencia citable (commit,
  informe de auditoría), esa evidencia reemplaza a la hipótesis
  correspondiente, que deja de usarse.
- Revisión obligatoria por evento — se aplica el que ocurra primero:
  1. cambio mayor o relevante del modelo;
  2. incidente de gobernanza;
  3. desviación conductual comprobada;
  4. cambio material en las herramientas disponibles para el modelo;
  5. cumplimiento de 90 días desde la última revisión.
  Un adaptador vencido por cualquiera de estos eventos se considera
  desactualizado, no inválido — se marca para revisión antes de usarse
  en una decisión de riesgo alto. El mecanismo exacto de registro de
  cada revisión (dónde se anota la fecha/evento que la disparó) se
  define en el mandato de la Fase 1 (§17).
- El adaptador de Sonnet (`SONNET_FABLE_ADAPTER.md`, a redactar en fase
  posterior) debe declarar en su primera sección la misma aclaración
  terminológica de §6: aplica criterio derivado de Fable Judgment v1, no
  reclama ser Fable.

---

## 15. Benchmark conductual y pruebas de regresión

- Estado actual, verificado: **cero** benchmarks conductuales ejecutados
  contra el corpus Fable Judgment v1 (`TRANSFER_COVERAGE_REPORT.md` §4).
  Este plan no cambia ese estado; solo lo hereda como hecho conocido.
- Metodología a reutilizar (documentada en `CLAUDEBOT`, **aún no
  validada conductualmente**): paquete autocontenido y aislado por
  caso, evaluador separado del modelo evaluado, oracle nunca visible al
  evaluado, puntuación binaria con falla automática ante error crítico.
- Para `CLAUDEBOT-CONTROL`, los casos de regresión (`tests/`, a crear en
  fase posterior) deben cubrir el dominio real de este repositorio
  (mandatos, informes, aislamiento de ramas, veredictos APROBAR/
  RECHAZAR/BLOQUEAR) — no los casos de trading de `evals/` en
  `CLAUDEBOT`, que pertenecen a la Capa C y no se duplican aquí.
- Ningún agente puede afirmar "esto ya fue validado conductualmente" sin
  un archivo de resultados versionado y citable, igual que exige el
  legado Fable para cualquier otra afirmación de prueba.

---

## 16. Integración futura con CLAUDEBOT sin duplicar reglas científicas

- `CLAUDEBOT-CONTROL` nunca contiene código científico, datasets ni
  reglas de dominio (`README.md` ya vigente, sin cambios).
- La integración se hace por **referencia versionada**, no por copia: un
  documento en `CLAUDEBOT-CONTROL` cita repositorio + tag/commit + ruta
  de `CLAUDEBOT`; no reproduce el contenido científico.
- Si `CLAUDEBOT` decide adoptar el núcleo institucional de este plan, la
  vía es que `CLAUDEBOT/AGENTS.md` referencie a `CLAUDEBOT-CONTROL` como
  fuente de la Capa A, sin que `CLAUDEBOT-CONTROL` necesite conocer los
  detalles científicos para operar.
- Ninguna tarea de `CLAUDEBOT-CONTROL` abre datasets, ejecuta discovery/
  OOS ni continúa fases científicas (F-1A, F10, F11, T2): eso ocurre
  exclusivamente dentro de `CLAUDEBOT`, bajo su propia autorización.
- Toda referencia cruzada entre repositorios se fija mediante **tag o
  commit inmutable citado explícitamente, en SHA completo** (como en
  §6: tag `fable-judgment-v1`, commit
  `3a749d43d1ece2260ab5a1f1b89460a78d330c9c`); una rama móvil (p. ej.
  `main` sin commit fijado) **no es una referencia normativa válida**,
  porque su contenido puede cambiar después de haberla citado.

---

## 17. Estrategia de migración por fases

Ninguna fase de esta lista está autorizada por este documento; cada una
requiere mandato y autorización explícita propios cuando llegue su turno.

1. **Fase 0 (esta).** Plan de arquitectura, sin implementación. Incluye
   el cierre de las decisiones arquitectónicas de §5, §7, §9, §14 y esta
   sección, resueltas por Miguel el 2026-07-28 y registradas de forma
   duradera en el commit `f00c42b626e49ed69816ca6847db164b28219b7d`
   (`decisions/OWNER_DECISIONS.md`).
2. **Fase 1.** Redactar y congelar los documentos canónicos de la Capa A
   (núcleo institucional) y el primer perfil de Capa B (gobernanza de
   proyecto, para `CLAUDEBOT`), con `AGENTS.md` como índice que los
   referencia sin fusionarlos (§5.1). Define también la ubicación exacta
   de esos documentos y el mecanismo de registro de revisión de
   adaptadores (§14). Sin crear aún `judgment/`, `adapters/` ni `tests/`.
3. **Fase 2.** Crear el **manifiesto de procedencia** de Fable
   Judgment v1 (Capa C) — repositorio `CLAUDEBOT`, tag
   `fable-judgment-v1`, commit
   `3a749d43d1ece2260ab5a1f1b89460a78d330c9c`, rutas citadas y hash de
   archivo cuando corresponda —, sin copiar el corpus completo ni crear
   un espejo. Una copia íntegra del corpus, si se decide en el futuro,
   requiere una decisión arquitectónica y una auditoría propias,
   separadas de esta fase (política v1, §5.3).
4. **Fase 3.** Redactar `SONNET_FABLE_ADAPTER.md` (Capa D) bajo
   `adapters/`.
5. **Fase 4.** Construir `tests/fable-regression/` con casos del dominio
   de `CLAUDEBOT-CONTROL` (§15).
6. **Fase 5.** Evaluar si `CLAUDEBOT` referencia la Capa A de vuelta, sin
   duplicar su propio legado científico (§16).

Cada fase cierra con informe y declaración negativa verificable antes de
que la siguiente pueda abrirse (patrón de fases documentado en
`CLAUDEBOT`, aplicado aquí a la gobernanza en vez de a la ciencia). Esto
no afirma que las fases F10 o F11 de `CLAUDEBOT` hayan sido ejecutadas,
cerradas ni validadas — de hecho, `docs/estado_rector_post_f8.md` §3
registra que ninguna de las dos consta ejecutada en git al 2026-07-19.

### 17.1 Secuencia obligatoria antes de autorizar la Fase 1

**La Fase 1 no queda autorizada por este mandato.** Antes de que Miguel
pueda autorizarla, debe cumplirse, en orden:

A. El plan se versiona mediante commit autorizado explícitamente por
   Miguel — ningún agente commitea este documento por iniciativa
   propia.
B. Codex audita ese commit exacto.
C. El informe de Codex queda versionado y cita el commit auditado.
D. Si el veredicto es `APROBAR`: no se exige commit correctivo; se
   avanza directamente al paso F.
E. Si el veredicto es `RECHAZAR` o `BLOQUEAR`:
   1. se corrigen los hallazgos, bajo autorización de Miguel;
   2. las correcciones quedan en un nuevo commit;
   3. Codex realiza una **nueva auditoría independiente** sobre ese
      nuevo commit;
   4. el nuevo informe también queda versionado y cita el nuevo commit;
   5. el ciclo (B-E) se repite hasta obtener veredicto `APROBAR` sobre
      el **commit objetivo**.
F. Miguel solo puede autorizar la Fase 1 cuando el veredicto vigente
   sobre el **commit objetivo** sea `APROBAR`.

**Definición de "commit objetivo".** En toda esta sección y en §18,
"commit objetivo" es el **último commit, dentro de la rama de entrega
correspondiente, cuyo diff incluye una modificación de**
`docs/plan_arquitectura_gobernanza_multi_ia_v1.md` — comprobable
mediante el historial de ese archivo en esa rama (p. ej.
`git log -1 -- docs/plan_arquitectura_gobernanza_multi_ia_v1.md`). Un
commit posterior que no modifique este archivo —incluidos el commit que
registra decisiones en `decisions/OWNER_DECISIONS.md`, el commit que
versiona un informe de auditoría, o cualquier otro commit ajeno al
plan— **no se convierte en commit objetivo** por el solo hecho de
existir después. Toda mención anterior de "commit más reciente" en
relación con el artefacto que Codex audita se interpreta conforme a
esta definición.

Ningún paso de esta secuencia se salta ni se da por completado sin su
evidencia correspondiente en git (commit, informe de auditoría). Las
definiciones cerradas y no circulares de cada hito están en §18.

---

## 18. Criterios de aceptación

Seis etapas, cada una con una definición cerrada y verificable —
ninguna se da por cumplida por declaración, solo por su evidencia. El
ciclo B-E de §17.1 puede repetir la cuarta etapa tantas veces como haga
falta antes de alcanzar la quinta:

| Etapa | Definición | Evidencia que la satisface |
|---|---|---|
| **Listo para versionar** | Revisión de Miguel y de ChatGPT sobre el borrador completada, sin correcciones pendientes de aplicar. | Registro durable que transcriba o resuma de forma sustantiva: la revisión de ChatGPT (recomienda, no autoriza); la decisión y autorización de Miguel (quien autoriza); la acción concreta autorizada; el alcance; la rama; los archivos autorizados; y las prohibiciones relevantes — en una entrada de `decisions/OWNER_DECISIONS.md` o en un `MANDATE.md`/adenda. La conversación de origen puede citarse como contexto adicional, nunca como evidencia durable única. |
| **Versionado** | Existe un commit de este documento en la rama de entrega correspondiente, creado con autorización expresa de Miguel. | Hash del commit **y** el mismo registro durable sustantivo exigido en la etapa anterior. El hash por sí solo prueba existencia y contenido, no autorización. |
| **Auditado** | Existe un informe de auditoría independiente de Codex sobre el commit objetivo (§17.1), que cita ese commit exacto. | `*_AUDIT.md` con veredicto `APROBAR`/`RECHAZAR`/`BLOQUEAR` (§9), referenciando el hash del commit objetivo auditado. |
| **Hallazgos resueltos y re-auditados** *(solo si el veredicto de la auditoría más reciente no fue `APROBAR`)* | Si la primera auditoría fue `APROBAR`, esta etapa no aplica y se avanza directamente a la siguiente. Si fue `RECHAZAR`/`BLOQUEAR`, exige un commit correctivo más una nueva auditoría versionada sobre ese commit; se repite hasta obtener `APROBAR`. | Commit(s) correctivo(s) + informe(s) de re-auditoría versionados, cada uno citando el commit objetivo exacto que audita. |
| **`APROBAR` vigente** | El veredicto de la auditoría más reciente, sobre el commit objetivo (§17.1), es `APROBAR`. | El informe de auditoría vigente (el último de la cadena) con veredicto `APROBAR`, citando el commit objetivo. |
| **Autorizado para Fase 1 por Miguel** | Miguel emite decisión expresa final autorizando el inicio de la Fase 1 — solo posible con `APROBAR` vigente. | Entrada en `decisions/OWNER_DECISIONS.md` (§4.1.B). |

Cada etapa requiere la anterior completa; ninguna se salta. Para este
plan, el commit `f00c42b626e49ed69816ca6847db164b28219b7d`
registra de forma duradera las decisiones arquitectónicas de la Fase 0,
el primer versionado
`abeccd1ed4757b5abda5cbc7a0a3aae49a2f1838`
y la auditoría inicial
`c7db9a7616e75d502e556a43466762c8aa4623ca`, con veredicto
`RECHAZAR`.

La autorización durable específica para corregir H-01 a H-11 y crear
el versionado correctivo posteriormente materializado en el commit
objetivo `a4b646b780c121598194d56793e6a54d816f8260` está registrada en
el commit `2ac48a65d5c25962dca7c589a6e9fcdef38428cb`
(`decisions/OWNER_DECISIONS.md`, entrada del 2026-07-29).

El versionado correctivo resultante fue el commit objetivo
`a4b646b780c121598194d56793e6a54d816f8260`. La reauditoría
independiente de Codex sobre ese commit quedó versionada en
`8f5734849600c2f02231448422e82bea83671de5`, con veredicto
`RECHAZAR`: declaró cerrados H-01 a H-11 y registró N-01 como único
hallazgo MAYOR abierto.

La decisión sustantiva que distingue `BLOQUEAR` de `RECHAZAR` para
resolver N-01, y la autorización para modificar §9, están registradas
en el commit
`fe748558013fe6c8d42c1ec3fe7ba2360a160be2`
(`decisions/OWNER_DECISIONS.md`, entrada del 2026-07-29).

La autorización durable para conservar esa corrección, actualizar la
trazabilidad de la cabecera y de esta sección, y crear el siguiente
versionado correctivo está registrada en el commit
`04149b6b359d15b3ff79d95993205ddffac8752f`
(`decisions/OWNER_DECISIONS.md`, entrada del 2026-07-29).

Esta edición no se auto-certifica: la etapa `Versionado` se satisface
únicamente mediante un commit objetivo que contenga la corrección N-01
y los ajustes de trazabilidad anteriores, acompañado por las
autorizaciones durables
`fe748558013fe6c8d42c1ec3fe7ba2360a160be2` y
`04149b6b359d15b3ff79d95993205ddffac8752f`.

El paso de esta edición a `Auditado` requiere una nueva auditoría
independiente de Codex sobre ese commit objetivo. Solo un veredicto
`APROBAR` vigente permitirá avanzar posteriormente hacia una decisión
expresa y separada de Miguel sobre la Fase 1.

---

## 19. Riesgos y mecanismos de reversión

| Riesgo | Mitigación |
|---|---|
| Confundir "criterio derivado de Fable" con "Fable operando" | Aclaración obligatoria en cabecera de todo adaptador (§6, §14) |
| Sobreclaim de validación conductual no ejecutada | Prohibición explícita (§6, §15); toda afirmación de prueba exige archivo de resultados citable |
| Duplicar reglas científicas en `CLAUDEBOT-CONTROL` | Integración por referencia, nunca por copia (§16) |
| Fuga de permisos de dominio científico hacia este repo | Tabla de permisos explícita (§10); `AGENTS.md` §7 ya vigente no se modifica |
| Adaptador desactualizado tratado como vigente | Revisión obligatoria por evento, con fecha/versión declarada (§14) |
| Contradicción entre capas o documentos sin resolver | Protocolo de resolución con escalado obligatorio a Miguel (§13) |
| Fase implementada sin autorización explícita | Cada fase de §17 requiere mandato propio; este documento no autoriza ninguna |
| Copiar el corpus completo de Fable Judgment v1 (o cualquier elemento de Capa C) como "espejo" sin decisión separada | Política v1 limita esta fase a un manifiesto de procedencia; un espejo completo requiere decisión arquitectónica y auditoría propias (§5.3, §17 Fase 2) |
| Confundir una autorización operacional puntual de Miguel con una decisión institucional duradera | Distinción explícita §4.1; toda modificación normativa se versiona antes de integrarse (§3, §4.3) |

**Reversión:** toda la arquitectura vive en ramas y commits; nada de esta
fase toca `main` sin merge autorizado. Si una fase posterior resulta
equivocada, revertir es `git revert`/no mergear la rama correspondiente
— no hay estado irreversible creado por este plan.

---

## 20. Uso futuro opcional de Obsidian como interfaz

- Obsidian (u otra herramienta de visualización de Markdown/grafo) puede
  usarse en el futuro como **interfaz de lectura y navegación** sobre los
  documentos ya versionados en git.
- Nunca es fuente de verdad: ningún estado, decisión o veredicto es
  válido por existir en un vault de Obsidian si no tiene su commit
  correspondiente en git. Cualquier nota, canvas o plugin de Obsidian es
  una vista derivada, descartable y regenerable.
- Si se adopta, la integración debe ser de solo lectura sobre el
  repositorio (o sobre una copia sincronizada de solo lectura); escribir
  desde Obsidian hacia el repositorio, si alguna vez se habilita, sigue
  el mismo flujo de mandato/autorización que cualquier otro agente (§8).

---

## Resumen de decisiones abiertas para Miguel

Las seis decisiones planteadas en el borrador anterior (separación en
capas, roles, ubicación de `AGENTS.md`, relación con `STATUS.md`, plazo
de revisión de adaptadores, y el **procedimiento** para una futura
autorización de la Fase 1) quedaron resueltas por la decisión de Miguel
del 2026-07-28, registrada de forma duradera en el commit
`f00c42b626e49ed69816ca6847db164b28219b7d`
(`decisions/OWNER_DECISIONS.md`), y están incorporadas en §5, §7, §9.1,
§14 y §17.1 respectivamente. Esa misma entrada registra también las
autorizaciones operacionales que produjeron el primer versionado
(`abeccd1ed4757b5abda5cbc7a0a3aae49a2f1838`) y la auditoría inicial de
Codex (`c7db9a7616e75d502e556a43466762c8aa4623ca`, veredicto
`RECHAZAR`), y las excepciones de rama `plan/*`/`audit/*` de la Fase 0
(§11).

**Resolver el procedimiento de autorización de la Fase 1 (§17.1) no
equivale a autorizar la Fase 1.** Esa autorización sigue pendiente y
exige, todas a la vez: un commit objetivo versionado de este documento
(§17.1); una auditoría independiente de Codex sobre ese commit
objetivo; veredicto `APROBAR` vigente sobre ese mismo commit objetivo
(§18); y una decisión expresa final y posterior de Miguel, registrada
en `decisions/OWNER_DECISIONS.md`. La entrada del commit
`f00c42b626e49ed69816ca6847db164b28219b7d` **no autoriza el inicio de
la Fase 1**.

Quedan abiertas, como detalles de implementación a resolver en el
mandato de la Fase 1 (no bloquean el cierre de este plan):

1. Nombre y ruta exactos de los documentos canónicos de la Capa A
   (núcleo institucional) y del primer perfil de Capa B (gobernanza de
   proyecto para `CLAUDEBOT`) — §5.1, §5.2.
2. Si el perfil de Capa B se redacta únicamente para `CLAUDEBOT`, o si
   además se deja una plantilla genérica de perfil reutilizable para
   futuros repositorios que `CLAUDEBOT-CONTROL` llegue a coordinar.
3. Mecanismo exacto de registro de cada revisión de adaptador (§14): en
   el propio adaptador, en `decisions/OWNER_DECISIONS.md`, o en un
   registro aparte.

---

*Este documento no autoriza ninguna implementación ni el inicio de la
Fase 1. Toda fase de §17 requiere mandato y autorización explícita de
Miguel cuando corresponda.*
