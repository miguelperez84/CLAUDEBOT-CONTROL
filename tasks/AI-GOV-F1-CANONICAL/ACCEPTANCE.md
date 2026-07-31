# ACCEPTANCE.md — AI-GOV-F1-CANONICAL

Criterios de aceptación verificables para la implementación futura de
la Fase 1 (§17 del plan de arquitectura de gobernanza multi-IA v1).
Ninguno de estos criterios se da por cumplido por declaración; cada uno
exige la evidencia de la columna correspondiente en la matriz de §2.

## 1. Criterios A-01 a A-21

A-01. El diff completo entre el commit base de implementación fijado
por Miguel y el commit objetivo de implementación modifica
exclusivamente los cinco archivos asignados a Sonnet en `MANDATE.md`
§3.

A-02. `AGENTS.md` permanece como puerta de entrada e índice y conserva
expresamente:

- la autoridad exclusiva de Miguel;
- la taxonomía exacta `APROBAR`/`RECHAZAR`/`BLOQUEAR`;
- el aislamiento entre agentes;
- el bloqueo ante hallazgos críticos;
- la estructura obligatoria de mandatos;
- la estructura obligatoria de informes;
- el control de ramas y merges;
- las prohibiciones de alcance sobre `CLAUDEBOT`.

A-03. `INSTITUTIONAL_CORE.md` es agnóstico de proyecto, modelo y
dominio científico.

A-04. Capa A cubre autoridad, precedencia, permisos, alcance,
veredictos/estados y conflictos.

A-05. Capa A no usa vocabulario científico como regla universal.

A-06. `CLAUDEBOT_PROFILE.md` añade restricciones y no relaja Capa A.

A-07. Toda referencia normativa a `CLAUDEBOT` se presenta en una tabla
o registro que contiene, como campos separados:

- repositorio;
- SHA completo de 40 caracteres;
- ruta literal;
- función o motivo de la referencia.

Las referencias normativas de esta Fase 1 solo pueden corresponder a
estas rutas literales:

- `AGENTS.md`
- `docs/estado_rector_post_f8.md`
- `docs/campania_t1_btcusdt_1h.md`
- `docs/borrador_arquitectura_documental_t2.md`

A-08. CLAUDEBOT mantiene exclusivamente sus reglas científicas, datos,
código, producción y legado.

A-09. El perfil no abre ni continúa F-1A, F10, F11 o T2.

A-10. `ADAPTER_REVIEW_POLICY.md` define:

- todos los campos obligatorios del registro;
- los cinco eventos de revisión del plan;
- la regla de revisión al cumplirse 90 días;
- la ubicación física exacta del registro;
- el procedimiento para crear y actualizar entradas;
- la conservación del historial;
- la separación entre propuesta, auditoría y decisión de Miguel;
- los estados `VIGENTE`, `REVISIÓN REQUERIDA` e
  `HIPÓTESIS NO VALIDADA`.

A-11. Distingue evidencia de `HIPÓTESIS NO VALIDADA`.

A-12. No crea adaptadores ni concede permisos basados solo en hipótesis.

A-13. No crea `judgment/`, `adapters/` o `tests/`.

A-14. La implementación no copia, reproduce ni incorpora contenido
sustantivo del corpus Fable Judgment v1. Solo puede mencionar su
nombre, su condición de sistema documental independiente del proveedor
y referencias por puntero cuando el mandato lo permita.

A-15. No modifica CLAUDEBOT.

A-16. No ejecuta datasets, código científico, discovery, OOS,
producción ni validación conductual.

A-17. El informe de implementación registra archivos abiertos,
modificados, comandos y estado Git.

A-18. Codex audita el commit objetivo exacto y usa solo
`APROBAR`, `RECHAZAR` o `BLOQUEAR`.

A-19. Todo hallazgo crítico produce `BLOQUEAR`.

A-20. Nada se declara congelado antes de `APROBAR` y decisión final.

A-21. Fase 1 solo cierra cuando existen:

- commit de implementación;
- auditoría independiente versionada;
- `APROBAR` vigente;
- decisión final de congelación y cierre de Miguel;
- integración y push autorizados por separado.

## 2. Matriz de verificación

| Criterio | Archivo o evidencia | Comando verificable | Resultado esperado |
|---|---|---|---|
| A-01 | Diff completo entre el commit base de implementación y el commit objetivo de implementación | `git diff --name-status <commit-base-implementación> <commit-objetivo-implementación>` | Aparecen exactamente estas cinco rutas y ninguna otra: `AGENTS.md`, `governance/core/INSTITUTIONAL_CORE.md`, `governance/core/ADAPTER_REVIEW_POLICY.md`, `governance/projects/CLAUDEBOT_PROFILE.md`, `reports/AI-GOV-F1-CANONICAL/IMPLEMENTATION_REPORT.md`. No se usa `git diff-tree`, porque solo comprobaría un commit individual y podría omitir cambios anteriores de la misma implementación |
| A-02 | `AGENTS.md` | `git diff <commit-base-implementación> <commit-objetivo-implementación> -- AGENTS.md` | El texto final de `AGENTS.md` conserva de forma verificable los ocho elementos: autoridad exclusiva de Miguel, taxonomía `APROBAR`/`RECHAZAR`/`BLOQUEAR`, aislamiento entre agentes, bloqueo ante hallazgos críticos, estructura obligatoria de mandatos, estructura obligatoria de informes, control de ramas y merges, y prohibiciones de alcance sobre `CLAUDEBOT`. Los cambios de `AGENTS.md` se limitan a conservar las ocho reglas críticas, establecer o reforzar su función de puerta de entrada e índice y enlazar las tres rutas canónicas (`governance/core/INSTITUTIONAL_CORE.md`, `governance/core/ADAPTER_REVIEW_POLICY.md`, `governance/projects/CLAUDEBOT_PROFILE.md`); no duplica íntegramente el contenido normativo detallado. No se exige que el diff sea únicamente aditivo |
| A-03 | `governance/core/INSTITUTIONAL_CORE.md` | `grep -inE "dataset|discovery|OOS|trading|quintil|BTCUSDT" governance/core/INSTITUTIONAL_CORE.md` | Sin coincidencias |
| A-04 | `governance/core/INSTITUTIONAL_CORE.md` | `grep -inE "^##" governance/core/INSTITUTIONAL_CORE.md` | Existen secciones para autoridad, precedencia, permisos, alcance, veredictos/estados y conflictos |
| A-05 | `governance/core/INSTITUTIONAL_CORE.md` | Lectura manual del documento completo | Ningún vocabulario de dominio científico presentado como regla universal |
| A-06 | `governance/projects/CLAUDEBOT_PROFILE.md` | Lectura manual comparando contra `INSTITUTIONAL_CORE.md` | El perfil solo añade restricciones; ninguna cláusula relaja una regla de Capa A |
| A-07 | `governance/projects/CLAUDEBOT_PROFILE.md` | Lectura completa de la tabla de referencias y búsqueda de hashes con: `grep -nE '[0-9a-f]{40}' governance/projects/CLAUDEBOT_PROFILE.md` | Cada referencia normativa tiene, simultáneamente: repositorio identificado como CLAUDEBOT; el mismo SHA completo autorizado por Miguel; una de las cuatro rutas literales (`AGENTS.md`, `docs/estado_rector_post_f8.md`, `docs/campania_t1_btcusdt_1h.md`, `docs/borrador_arquitectura_documental_t2.md`); función o motivo de la referencia. Ninguna referencia normativa apunta a otra ruta. Ninguna referencia se sustenta únicamente en `main`, nombre de rama, tag móvil o hash abreviado |
| A-08 | `governance/projects/CLAUDEBOT_PROFILE.md` | Lectura manual | No se transcriben reglas científicas, datos ni código; solo referencias por puntero |
| A-09 | `governance/projects/CLAUDEBOT_PROFILE.md` | `grep -inE "F-1A|F10|F11|\bT2\b"  governance/projects/CLAUDEBOT_PROFILE.md` | Toda mención es descriptiva del estado existente (referenciado, no abierto ni continuado) |
| A-10 | `governance/core/ADAPTER_REVIEW_POLICY.md` | Lectura completa de `governance/core/ADAPTER_REVIEW_POLICY.md`; búsqueda de apoyo de los campos, los tres estados, los cinco eventos y "90 días" con `grep -inE "modelo|versión|fecha|evento|evidencia|estado|responsable|auditor|decisión|90 días" governance/core/ADAPTER_REVIEW_POLICY.md` | Todos los campos, los cinco eventos, la regla de 90 días, la ubicación exacta del registro, el procedimiento de creación/actualización, la conservación del historial, la separación propuesta/auditoría/decisión y los tres estados están definidos normativamente; no quedan frases como "ubicación por definir", "mecanismo pendiente" o equivalentes |
| A-11 | `governance/core/ADAPTER_REVIEW_POLICY.md` | `grep -n "HIPÓTESIS NO VALIDADA" governance/core/ADAPTER_REVIEW_POLICY.md` | El estado existe y está definido en sección separada de la evidencia observada |
| A-12 | `governance/core/ADAPTER_REVIEW_POLICY.md` | Lectura manual | Ninguna cláusula concede permiso o autonomía basándose solo en una hipótesis no validada |
| A-13 | Diff del commit objetivo de implementación contra el commit base de implementación | `git diff --name-only <commit-base-implementación> <commit-objetivo-implementación> | grep -E '^(judgment|adapters|tests)(/|$)'` | Sin coincidencias; la comprobación se limita a rutas creadas o modificadas por la implementación y no al árbol histórico completo |
| A-14 | Diff completo de los cinco archivos de implementación | `git diff <commit-base-implementación> <commit-objetivo-implementación> -- AGENTS.md governance/core/INSTITUTIONAL_CORE.md governance/core/ADAPTER_REVIEW_POLICY.md governance/projects/CLAUDEBOT_PROFILE.md reports/AI-GOV-F1-CANONICAL/IMPLEMENTATION_REPORT.md` más lectura manual completa | No aparece contenido copiado del corpus; no se reproducen constitución, modelos de decisión, patrones de falla, adaptadores o ADR del corpus; cualquier mención a Fable es terminológica o mediante referencia; no se afirma validación conductual |
| A-15 | Preflight y cierre del informe de implementación | `git -C /home/miguel/proyectos/CLAUDEBOT rev-parse HEAD` y `git -C /home/miguel/proyectos/CLAUDEBOT status --short`, ejecutados antes y después de la lectura autorizada; como apoyo, `grep -n "git -C /home/miguel/proyectos/CLAUDEBOT.*show" reports/AI-GOV-F1-CANONICAL/IMPLEMENTATION_REPORT.md`, más lectura manual obligatoria del informe (los comandos pueden estar divididos en varias líneas) | El informe registra el HEAD y status iniciales de CLAUDEBOT; el informe registra el HEAD y status finales; ambos HEAD coinciden; no se crean cambios nuevos ni commits en CLAUDEBOT; cualquier cambio previo ajeno se registra y permanece intacto; toda lectura se realiza mediante `git show` contra el SHA autorizado; el listado de archivos abiertos en el informe contiene únicamente estas cuatro rutas de CLAUDEBOT: `AGENTS.md`, `docs/estado_rector_post_f8.md`, `docs/campania_t1_btcusdt_1h.md`, `docs/borrador_arquitectura_documental_t2.md`; no aparece ninguna otra ruta de CLAUDEBOT en los comandos de lectura |
| A-16 | Informe de implementación §3 (comandos ejecutados) | Lectura manual del informe | Sin comandos sobre datasets, CSV, discovery, OOS, producción ni scripts de validación conductual |
| A-17 | `reports/AI-GOV-F1-CANONICAL/IMPLEMENTATION_REPORT.md` | Lectura contra `templates/REPORT_TEMPLATE.md` §3-§6 | Contiene las cuatro secciones exigidas con datos reales, no descriptivos; registra también los dos SHA fijados por Miguel (commit base de implementación en CLAUDEBOT-CONTROL y SHA de lectura de CLAUDEBOT); registra preflight y cierre de CLAUDEBOT (HEAD y status antes/después); registra las cuatro rutas exactas leídas mediante `git show`; incluye declaración negativa de que no abrió rutas adicionales |
| A-18 | `reports/AI-GOV-F1-CANONICAL/AUDIT_CODEX.md` | `grep -n "commit auditado\|APROBAR\|RECHAZAR\|BLOQUEAR"  reports/AI-GOV-F1-CANONICAL/AUDIT_CODEX.md` como apoyo, más lectura manual obligatoria de la sección final de veredicto | El informe cita el SHA completo del commit objetivo; contiene una sección final de veredicto; esa sección contiene exactamente uno de: `APROBAR`, `RECHAZAR` o `BLOQUEAR`; no utiliza estados intermedios |
| A-19 | `reports/AI-GOV-F1-CANONICAL/AUDIT_CODEX.md` §5 (hallazgos) | Lectura manual de la tabla de hallazgos | Si existe severidad "crítico", el veredicto de §7 es `BLOQUEAR` |
| A-20 | `governance/` completo y `decisions/OWNER_DECISIONS.md` | Lectura de los encabezados de todos los documentos creados bajo `governance/`; revisión del diff completo de implementación; revisión de `OWNER_DECISIONS.md` únicamente para determinar si existe una decisión posterior a un `APROBAR` | Antes del cierre, los documentos se identifican como `BORRADOR`, `NO CONGELADO` o equivalente inequívoco; no existe una declaración afirmativa de congelación o vigencia definitiva; las apariciones negativas o procedimentales de la palabra "congelado" no se clasifican como incumplimiento |
| A-21 | `decisions/OWNER_DECISIONS.md` (entrada de cierre de Fase 1) | Lectura manual de la entrada final | Cita explícitamente: commit de implementación, commit de auditoría con `APROBAR`, decisión de cierre de Miguel, y autorización separada de integración/push |

No se han inventado hashes futuros: ninguna celda de la matriz cita un
commit que no exista todavía; los comandos se ejecutan sobre los
commits reales una vez creados durante la implementación autorizada.
