# Auditoría Codex — Plan de arquitectura de gobernanza multi-IA v1

## 1. Identificación

- **Rol:** Codex, auditor independiente y red team.
- **Repositorio:** `/home/miguel/proyectos/CLAUDEBOT-CONTROL-CODEX-AI-GOV`
- **Rama:** `audit/codex-ai-governance-v1`
- **Commit exacto auditado:** `abeccd1ed4757b5abda5cbc7a0a3aae49a2f1838`
- **Documento auditado:** `docs/plan_arquitectura_gobernanza_multi_ia_v1.md`
- **Resultado del preflight:** conforme; se cumplieron las cinco condiciones
  obligatorias de continuación.

## 2. Alcance y método

Se auditó si el plan es internamente coherente, verificable, aplicable y
suficientemente cerrado para servir como arquitectura rectora antes de que
Miguel pueda autorizar la Fase 1. La revisión cubrió las veinte materias
enumeradas en el mandato: capas A/B/C/D; autoridad; precedencia y supersesión;
autorización operacional frente a decisión institucional; Git; independencia;
puerta de integración; corrección y reauditoría; estados; permisos; ramas,
commits y acciones irreversibles; estado único y handoffs; Fable Judgment v1;
adaptadores e hipótesis; benchmark y regresión; referencias cruzadas;
Fases 0–5; criterios de aceptación; decisiones postergadas; y contradicciones,
ambigüedades, circularidades o permisos implícitos.

La auditoría fue documental y de solo lectura, salvo por la creación de este
informe. No se abrieron datasets, CSV, resultados científicos, OOS, scripts de
trading ni producción. La referencia mínima a F10/F11 se limitó a las líneas
43–53 de `docs/estado_rector_post_f8.md` en el commit rector de `CLAUDEBOT`,
para comprobar una afirmación expresa del plan.

## 3. Archivos revisados

### Repositorio auditado

1. `docs/plan_arquitectura_gobernanza_multi_ia_v1.md`
2. `AGENTS.md`
3. `README.md`
4. `decisions/OWNER_DECISIONS.md`
5. `templates/AUDIT_TEMPLATE.md`
6. `templates/REPORT_TEMPLATE.md`
7. `templates/TASK_TEMPLATE.md`

### Referencias mínimas de solo lectura en `CLAUDEBOT`

Todas se consultaron en el commit
`3a749d43d1ece2260ab5a1f1b89460a78d330c9c`:

1. `ai_judgment/TRANSFER_COVERAGE_REPORT.md`
2. `ai_judgment/FABLE_CONSTITUTION.md`
3. `ai_judgment/MODEL_ADAPTER_CLAUDE.md`
4. `ai_judgment/MODEL_ADAPTER_CODEX.md`
5. `ai_judgment/MODEL_ADAPTER_GPT.md`
6. `docs/estado_rector_post_f8.md` (solo extracto mínimo de §3)

La enumeración del árbol mediante `ls-tree` y el resumen del commit mediante
`show --stat` se usaron para comprobar existencia y alcance sin abrir los
restantes archivos listados.

## 4. Verificaciones Git ejecutadas

### 4.1 Preflight obligatorio

```text
$ pwd
/home/miguel/proyectos/CLAUDEBOT-CONTROL-CODEX-AI-GOV

$ git branch --show-current
audit/codex-ai-governance-v1

$ git rev-parse HEAD
abeccd1ed4757b5abda5cbc7a0a3aae49a2f1838

$ git status --short
[sin salida]

$ git diff-tree --no-commit-id --name-status -r HEAD
A	docs/plan_arquitectura_gobernanza_multi_ia_v1.md
```

Conclusión: repositorio, rama y HEAD exactos; árbol limpio; el commit auditado
contiene únicamente el documento autorizado.

### 4.2 Identidad e historia del artefacto

- `git show --format=fuller --stat` confirmó que
  `abeccd1ed4757b5abda5cbc7a0a3aae49a2f1838` fue creado el
  2026-07-28 por Miguel Perez con asunto
  `docs: versiona plan de arquitectura de gobernanza multi-IA v1`.
- `git branch --contains` confirmó que el commit está contenido tanto en
  `plan/ai-governance-v1` como en `audit/codex-ai-governance-v1`.
- El historial de `docs/plan_arquitectura_gobernanza_multi_ia_v1.md` contiene
  ese único commit.
- El historial y contenido de `decisions/OWNER_DECISIONS.md` solo registran la
  creación del repositorio el 2026-07-25; no contienen una entrada del
  2026-07-28 que congele las decisiones arquitectónicas que el plan declara
  cerradas.

### 4.3 Referencias inmutables a Fable Judgment v1

- El tag `fable-judgment-v1` existe y es un objeto Git anotado (`tag`).
- `fable-judgment-v1^{commit}` resuelve exactamente a
  `3a749d43d1ece2260ab5a1f1b89460a78d330c9c`.
- El tag fue fechado el 2026-07-19.
- `ls-tree` confirmó los ocho documentos raíz de `ai_judgment/` citados por el
  plan y ADR-001 a ADR-010.
- `show --stat` confirmó que el commit rector integra `ai_judgment/`,
  adaptadores, ADR, skills y `evals/`.
- `TRANSFER_COVERAGE_REPORT.md` declara literalmente como estado que la
  transferencia documental está implementada y la transferencia conductual
  está pendiente de benchmark aislado; también indica que ningún modelo fue
  evaluado aún.
- `FABLE_CONSTITUTION.md` §5 exige trazabilidad por commit/hash y distingue lo
  ejecutado de lo meramente declarado.
- El extracto autorizado de `docs/estado_rector_post_f8.md` §3 confirma que
  F10 y F11 no constaban ejecutados en Git al 2026-07-19.

## 5. Criterio de severidad

- **CRÍTICO:** impide completar legítimamente la auditoría o crea una vía
  inmediata para desplazar la autoridad de Miguel, ejecutar una acción
  irreversible o ampliar alcance sin autorización.
- **MAYOR:** defecto corregible que impide usar esta versión como arquitectura
  rectora cerrada y verificable.
- **MENOR:** imprecisión localizada que debe corregirse para evitar deriva,
  aunque por sí sola no invalida el diseño general.
- **OBSERVACIÓN:** nota no bloqueante o mejora aconsejable sin incumplimiento.

## 6. Hallazgos

| ID | Severidad | Ruta | Sección | Evidencia | Impacto |
|---|---|---|---|---|---|
| H-01 | MAYOR | `docs/plan_arquitectura_gobernanza_multi_ia_v1.md` | Cabecera, §17.1, §18 (líneas 3–15, 696–700, 730, 737–739) | El documento versionado afirma que “el versionado todavía no está autorizado”, que versionarlo es un paso futuro y que por sí solo satisface como máximo “Listo para versionar”. Git demuestra que el SHA auditado es precisamente el commit de versionado, contenido en `plan/ai-governance-v1`, y su asunto dice “versiona plan”. | La metadata de ciclo de vida contradice la fuente de verdad que el propio §3 declara. Un lector no puede determinar desde el artefacto si está ante borrador pre-versionado o versión auditada. |
| H-02 | MAYOR | `docs/plan_arquitectura_gobernanza_multi_ia_v1.md`; `decisions/OWNER_DECISIONS.md` | Cabecera, §4.1.B, §13.4, resumen final (líneas 5, 111–117, 562–564, 782–786) | El plan afirma que arquitectura de capas, roles y seis decisiones fueron cerradas por decisión de Miguel el 2026-07-28. Sin embargo, `OWNER_DECISIONS.md` y su historial solo registran la decisión del 2026-07-25. El propio plan exige que una decisión institucional duradera quede registrada/versionada y que una contradicción resuelta por Miguel nunca quede solo en conversación. | Las premisas que hacen “definitivas” partes rectoras del plan no tienen evidencia institucional durable en Git. La arquitectura depende de una memoria conversacional que ella misma declara no vinculante entre sesiones. |
| H-03 | MAYOR | `docs/plan_arquitectura_gobernanza_multi_ia_v1.md`; `templates/AUDIT_TEMPLATE.md` | §4.2, §5.1, §9, §9.1; plantilla §7 (plan líneas 121–142, 213–219, 443–446, 460–492; plantilla líneas 49–64) | La precedencia enumera decisiones, capas A/B, mandato, adaptador y conversación, pero no ubica expresamente el `AGENTS.md` vigente, `README.md`, plantillas, `STATUS.md`, informes ni auditorías. Ya existe un conflicto demostrable: el plan dice que un incumplimiento definitivo de regla congelada produce siempre `RECHAZAR`, mientras `AUDIT_TEMPLATE.md` dice que cualquier hallazgo crítico obliga a `BLOQUEAR`. | Ante un hallazgo crítico que sea a la vez incumplimiento definitivo, el sistema no determina qué regla gana ni qué veredicto emitir. La precedencia no es aplicable a todos los documentos que el propio flujo usa. |
| H-04 | MAYOR | `docs/plan_arquitectura_gobernanza_multi_ia_v1.md` | §4.2–§4.3 (líneas 121–151) | La autorización operacional actual ocupa el nivel 1 y gana al mandato (nivel 5) y al adaptador (nivel 6), pero la regla que exige declarar excepción, regla reemplazada y alcance se limita literalmente a reglas congeladas de los niveles 2–4. | Una instrucción operacional podría desplazar un mandato cerrado o un adaptador sin cumplir la supersesión explícita reforzada. Queda una vía de ampliación implícita de alcance, precisamente lo que la arquitectura pretende impedir. |
| H-05 | MAYOR | `docs/plan_arquitectura_gobernanza_multi_ia_v1.md` | §9–§9.1 (líneas 448–492) | Se definen `BLOQUEADA` y `DETENIDA POR INCIDENTE` como estados transversales, pero no se define transición de salida, estado de retorno, evidencia que levanta el bloqueo ni tratamiento de un `APROBAR` posterior. Para `RECHAZAR` sí se define retorno a `EN IMPLEMENTACIÓN`; para `BLOQUEAR`, no. Tampoco se delimita cuándo es legítimo `EN AUDITORÍA → CERRADA` sin integración. | La máquina de estados no es total ni reproducible. Dos agentes pueden registrar estados distintos después de resolver el mismo bloqueo o cerrar una tarea sin una regla común sobre cuándo se omite integración. |
| H-06 | MAYOR | `docs/plan_arquitectura_gobernanza_multi_ia_v1.md` | §17.1 y §18 (líneas 699–715, 731–734) | “Commit más reciente” no se acota al último commit que modifica el artefacto auditado ni a una cadena identificada. Al versionar el informe de auditoría se crea necesariamente un commit posterior al commit del plan; un commit ajeno posterior también sería “el más reciente”. El informe no audita su propio commit. | La condición `APROBAR vigente` puede volverse falsa o circular por commits de informe o cambios no relacionados. La puerta de Fase 1 necesita definir el commit objetivo más reciente del artefacto y la relación exacta informe→commit. |
| H-07 | MAYOR | `docs/plan_arquitectura_gobernanza_multi_ia_v1.md` | §3 y §18 (líneas 68–93, 727–735) | “Listo para versionar” admite como evidencia revisiones solo en conversación, aunque §3 niega autoridad durable a conversaciones no versionadas. “Versionado” exige autorización expresa de Miguel, pero su única evidencia indicada es un hash: el hash prueba existencia/contenido, no la autorización. En cambio, la etapa final sí exige una entrada en `OWNER_DECISIONS.md`. | Dos criterios de aceptación no verifican todos los elementos de su propia definición y aplican estándares de evidencia incompatibles. No puede reproducirse solo desde Git que la cadena de autorización se cumplió. |
| H-08 | MAYOR | `docs/plan_arquitectura_gobernanza_multi_ia_v1.md` | §8 y §10 (líneas 400–407, 498–505) | Para `tasks/` y `reports/`, la escritura se concede al “agente autor” sin exigir en esa fila mandato, autorización operacional, rama propia ni rutas cerradas. Para `OWNER_DECISIONS.md` se exige decisión real y append, pero no se identifica quién puede materializarla ni bajo qué autorización/mandato. A la vez, planificación supone escribir un mandato antes de su aprobación y dice que ningún agente “ejecuta” en esa etapa. | Los permisos de escritura institucional no quedan cerrados por acción y actor. Ser autor o conocer una decisión de Miguel puede interpretarse erróneamente como permiso de escritura, y el bootstrap de un mandato queda circular o implícito. |
| H-09 | MENOR | `docs/plan_arquitectura_gobernanza_multi_ia_v1.md`; `AGENTS.md` | §11 (plan líneas 511–515; `AGENTS.md` líneas 75–88) | El plan llama “ya vigente” a la convención de `AGENTS.md`, pero agrega `plan/<nombre>-v<N>` sin que `AGENTS.md` la contemple. La auditoría autorizada usa además `audit/codex-ai-governance-v1`, familia que tampoco aparece en ninguna de las dos políticas. | La práctica autorizada y la política publicada divergen. Deben definirse explícitamente las ramas transitorias/de planificación/auditoría o quedar señaladas como excepciones de Miguel. |
| H-10 | MENOR | `docs/plan_arquitectura_gobernanza_multi_ia_v1.md`; `AGENTS.md` | §5.1 (plan líneas 202–204) | El patrón de enumeración cerrada de archivos se atribuye a `AGENTS.md` §7. En el documento vigente, esa obligación está en §4 (líneas 51–60); §7 trata el alcance y las prohibiciones respecto de `CLAUDEBOT`. | La referencia normativa equivocada reduce verificabilidad y puede hacer que un agente busque la regla en la sección incorrecta. |
| H-11 | MENOR | `docs/plan_arquitectura_gobernanza_multi_ia_v1.md` | Cabecera, §17.1, resumen final (líneas 11–15, 691–716, 782–786) | El resumen dice que las seis decisiones anteriores, incluida la “autorización de la Fase 1”, quedaron resueltas; la cabecera y §17.1 dicen que la decisión expresa final de Miguel sigue pendiente y que esta auditoría es previa. El contexto permite inferir que se resolvió el procedimiento de autorización, no la autorización misma, pero el texto no lo dice. | Puede producirse un handoff que trate la Fase 1 como ya autorizada basándose en el resumen aislado. |

### Conteo

| Severidad | Cantidad |
|---|---:|
| CRÍTICO | 0 |
| MAYOR | 8 |
| MENOR | 3 |
| OBSERVACIÓN | 0 |
| **Total** | **11** |

No se clasificó ningún hallazgo como CRÍTICO porque la auditoría pudo
completarse legítimamente y los defectos son corregibles sin ejecutar acciones
irreversibles ni ampliar el alcance. La falta de evidencia durable descrita en
H-02 y H-07 es un defecto verificable del artefacto, no una ausencia que impida
auditarlo.

## 7. Comprobaciones aprobadas

Las siguientes materias superaron la revisión en lo no afectado por los
hallazgos anteriores:

1. **Capas A/B/C/D:** la separación conceptual es coherente; A es universal,
   B encapsula restricciones por proyecto, C permanece en el repositorio de
   origen y D adapta por modelo.
2. **Autoridad:** Miguel conserva de forma explícita la autoridad final; no
   existe decisión por mayoría ni aprobación autónoma de agentes.
3. **Autorización operacional/institucional:** la distinción conceptual es
   clara y útil, aunque su evidencia y supersesión requieren las correcciones
   H-02, H-04 y H-07.
4. **Git y handoffs:** se establece correctamente Git como fuente de verdad,
   el SHA completo como identidad y la obligación de handoff con rama,
   mandato, commit y declaraciones negativas.
5. **Independencia:** implementador y auditor están separados; el auditor no
   edita el artefacto auditado ni aprueba su propia implementación.
6. **Puerta de integración:** exige informe independiente versionado, SHA
   auditado, `APROBAR`, ausencia de bloqueos y autorización expresa de Miguel.
7. **Corrección y reauditoría:** existe un ciclo explícito para producir un
   nuevo commit y una nueva auditoría hasta `APROBAR`; H-05 y H-06 afectan su
   formalización, no la intención del control.
8. **Acciones irreversibles:** push, merge rector, tags y acciones sensibles
   requieren autorización literal; cada fase necesita autorización propia.
9. **Fable Judgment v1:** tag, tipo de tag, commit, corpus y fecha fueron
   comprobados. El plan evita equiparar Fable con Sonnet, evita copiar el
   corpus y no sobreafirma validación conductual.
10. **Adaptadores:** exige fecha, versión, evidencia citable, auditor
    independiente y separación expresa de `HIPÓTESIS NO VALIDADA`; una
    hipótesis no concede autonomía ni permisos.
11. **Benchmark/regresión:** el benchmark pendiente fue comprobado en la
    fuente inmutable. Las pruebas futuras se separan del dominio científico y
    reservan evaluación a fases posteriores.
12. **Integración con `CLAUDEBOT`:** usa repositorio + tag/commit + ruta, SHA
    completo y referencias inmutables; no admite ramas móviles como fuente
    normativa.
13. **Fases 0–5:** el orden de núcleo/perfil, procedencia, adaptador,
    regresión y eventual referencia desde `CLAUDEBOT` respeta dependencias y
    no autoriza fases científicas.
14. **Restricciones de dominio:** datasets, resultados, OOS y producción
    quedan fuera de lectura/escritura desde tareas de control.

## 8. Decisiones abiertas legítimamente postergables

Estas decisiones pueden resolverse en el mandato de Fase 1 sin bloquear por sí
mismas el cierre conceptual del plan:

1. Nombre y ruta exactos de los documentos canónicos de Capa A y del primer
   perfil de Capa B.
2. Crear solo el perfil de `CLAUDEBOT` o además una plantilla genérica de
   perfil para repositorios futuros.
3. Ubicar el registro de revisión de adaptadores en el propio adaptador,
   `OWNER_DECISIONS.md` o un registro separado.

También es legítimo reservar para Fase 2 el manifiesto de procedencia con hash
por archivo, para Fase 3 el primer adaptador, para Fase 4 los casos de regresión
y para Fase 5 la eventual adopción desde `CLAUDEBOT`. Esas postergaciones son
dependencias secuenciadas, no permisos implícitos.

No son postergables como mero detalle de Fase 1 los hallazgos MAYORES: afectan
la capacidad del propio plan v1 para ser la arquitectura rectora que gobernará
esa fase.

## 9. Comandos ejecutados

```text
pwd
git branch --show-current
git rev-parse HEAD
git status --short
git diff-tree --no-commit-id --name-status -r HEAD

rg --files -g 'AGENTS.md' -g 'README.md' \
  -g 'docs/plan_arquitectura_gobernanza_multi_ia_v1.md' \
  -g 'templates/**' -g 'decisions/OWNER_DECISIONS.md' | sort

wc -l AGENTS.md README.md decisions/OWNER_DECISIONS.md \
  templates/AUDIT_TEMPLATE.md templates/REPORT_TEMPLATE.md \
  templates/TASK_TEMPLATE.md \
  docs/plan_arquitectura_gobernanza_multi_ia_v1.md

nl -ba AGENTS.md
nl -ba README.md
nl -ba decisions/OWNER_DECISIONS.md
nl -ba templates/AUDIT_TEMPLATE.md
nl -ba templates/REPORT_TEMPLATE.md
nl -ba templates/TASK_TEMPLATE.md
nl -ba docs/plan_arquitectura_gobernanza_multi_ia_v1.md | sed -n '1,280p'
nl -ba docs/plan_arquitectura_gobernanza_multi_ia_v1.md | sed -n '281,560p'
nl -ba docs/plan_arquitectura_gobernanza_multi_ia_v1.md | sed -n '561,804p'

git show --no-ext-diff --format=fuller --stat \
  abeccd1ed4757b5abda5cbc7a0a3aae49a2f1838
git branch --contains abeccd1ed4757b5abda5cbc7a0a3aae49a2f1838
git log --oneline --decorate --all -- \
  docs/plan_arquitectura_gobernanza_multi_ia_v1.md
git log --oneline --decorate --all -- decisions/OWNER_DECISIONS.md

git -C /home/miguel/proyectos/CLAUDEBOT tag -l fable-judgment-v1
git -C /home/miguel/proyectos/CLAUDEBOT cat-file -t fable-judgment-v1
git -C /home/miguel/proyectos/CLAUDEBOT rev-parse \
  'fable-judgment-v1^{commit}'
git -C /home/miguel/proyectos/CLAUDEBOT for-each-ref \
  refs/tags/fable-judgment-v1 \
  --format='%(refname:short) %(taggerdate:iso-strict) %(objectname)'
git -C /home/miguel/proyectos/CLAUDEBOT ls-tree -r \
  fable-judgment-v1 --name-only -- ai_judgment/
git -C /home/miguel/proyectos/CLAUDEBOT show --no-ext-diff \
  --format=fuller --stat \
  3a749d43d1ece2260ab5a1f1b89460a78d330c9c

git -C /home/miguel/proyectos/CLAUDEBOT grep -n \
  -E 'benchmark|Benchmark|ejecutad|conductual|aislad' \
  3a749d43d1ece2260ab5a1f1b89460a78d330c9c -- \
  ai_judgment/TRANSFER_COVERAGE_REPORT.md
git -C /home/miguel/proyectos/CLAUDEBOT grep -n \
  -E '^## 5|Git|commit|fuente de verdad' \
  3a749d43d1ece2260ab5a1f1b89460a78d330c9c -- \
  ai_judgment/FABLE_CONSTITUTION.md
git -C /home/miguel/proyectos/CLAUDEBOT grep -n \
  -E 'evidencia|HIPÓTESIS|hipótesis|valid' \
  3a749d43d1ece2260ab5a1f1b89460a78d330c9c -- \
  ai_judgment/MODEL_ADAPTER_CLAUDE.md \
  ai_judgment/MODEL_ADAPTER_CODEX.md \
  ai_judgment/MODEL_ADAPTER_GPT.md

git -C /home/miguel/proyectos/CLAUDEBOT show \
  3a749d43d1ece2260ab5a1f1b89460a78d330c9c:ai_judgment/TRANSFER_COVERAGE_REPORT.md \
  | nl -ba | sed -n '1,22p;108,132p'
git -C /home/miguel/proyectos/CLAUDEBOT show \
  3a749d43d1ece2260ab5a1f1b89460a78d330c9c:ai_judgment/FABLE_CONSTITUTION.md \
  | nl -ba | sed -n '125,146p'
git -C /home/miguel/proyectos/CLAUDEBOT grep -n \
  -E 'F10|F11|no consta|no constan' \
  3a749d43d1ece2260ab5a1f1b89460a78d330c9c -- \
  docs/estado_rector_post_f8.md
git -C /home/miguel/proyectos/CLAUDEBOT show \
  3a749d43d1ece2260ab5a1f1b89460a78d330c9c:docs/estado_rector_post_f8.md \
  | nl -ba | sed -n '43,53p'

rg -n \
  "commit más reciente|autorización expresa|solo se agrega|agente autor|supersede|niveles 2-4|BLOQUEADA|DETENIDA POR INCIDENTE|incumplimiento definitivo|hallazgo crítico|plan/|audit/|AGENTS.md.*§7|quedaron resueltas|no está autorizado|como máximo" \
  docs/plan_arquitectura_gobernanza_multi_ia_v1.md

git status --short

git status --short
git diff --name-status
git diff --check
wc -l docs/auditoria_codex_plan_arquitectura_gobernanza_multi_ia_v1.md
```

## 10. Estado Git final

```text
$ git status --short
?? docs/auditoria_codex_plan_arquitectura_gobernanza_multi_ia_v1.md

$ git diff --name-status
[sin salida; el único archivo creado aún no está rastreado]

$ git diff --check
[sin salida]

$ wc -l docs/auditoria_codex_plan_arquitectura_gobernanza_multi_ia_v1.md
352 docs/auditoria_codex_plan_arquitectura_gobernanza_multi_ia_v1.md
```

- **Archivo creado:** `docs/auditoria_codex_plan_arquitectura_gobernanza_multi_ia_v1.md`
- **Otros archivos modificados, creados o eliminados:** ninguno.
- **Commits creados por Codex:** ninguno.

## 11. Declaración de independencia

Codex no implementó ni corrigió el plan auditado. Codex **no modificó**
`docs/plan_arquitectura_gobernanza_multi_ia_v1.md`, `AGENTS.md`, `README.md`,
las plantillas, `decisions/OWNER_DECISIONS.md` ni ninguna referencia de
`CLAUDEBOT`. Este informe es el único archivo creado.

## 12. Veredicto final

```text
RECHAZAR
```

El plan fue completamente auditable, pero los ocho hallazgos MAYORES impiden
usarlo en este commit como arquitectura rectora vigente y suficientemente
cerrada. Son defectos corregibles: requieren una nueva entrega autorizada y
una nueva auditoría sobre el nuevo commit. Este veredicto no autoriza
correcciones, commits, integración ni el inicio de la Fase 1; la decisión final
sigue perteneciendo exclusivamente a Miguel.
