# Decisiones del propietario — CLAUDEBOT-CONTROL

Registro cronológico de decisiones explícitas de Miguel que afectan la
coordinación de agentes sobre `CLAUDEBOT` y sobre este propio
repositorio. No es un mandato ni un informe: es el libro de decisiones.

Cada entrada nueva se agrega al final, sin editar entradas anteriores.
Si una decisión queda sin efecto, se agrega una entrada nueva que la
revoca o reemplaza; no se borra la entrada original.

## Formato de entrada

```text
## <FECHA ISO> — <título corto de la decisión>

- Contexto:
- Decisión:
- Alcance / repositorio afectado:
- Referencia (mandato, informe o conversación):
```

---

## 2026-07-25 — Creación del repositorio CLAUDEBOT-CONTROL

- Contexto: se requiere un repositorio separado para coordinar
  mandatos, informes y auditorías de agentes de IA sin mezclar esa
  documentación con el código y los datos científicos de `CLAUDEBOT`.
- Decisión: crear `/home/miguel/proyectos/CLAUDEBOT-CONTROL` con la
  estructura inicial (`README.md`, `AGENTS.md`, `tasks/`, `reports/`,
  `decisions/`, `templates/`), sin mandatos científicos nuevos, sin
  push hasta autorización expresa.
- Alcance / repositorio afectado: `CLAUDEBOT-CONTROL` únicamente;
  `CLAUDEBOT` no fue modificado.
- Referencia: mandato de scaffolding inicial, 2026-07-25.

---

## 2026-07-28 — Decisiones arquitectónicas y autorizaciones operacionales de la Fase 0

- Contexto: durante la redacción, dos rondas de revisión de ChatGPT y la
  auditoría independiente de Codex sobre
  `docs/plan_arquitectura_gobernanza_multi_ia_v1.md` —Fase 0 de la
  estrategia de migración definida en §17 del plan— se resolvieron seis
  decisiones de diseño y se ejecutaron dos autorizaciones operacionales
  puntuales de Miguel en ramas propias.

- Decisión: Miguel registra de forma duradera lo siguiente:

  A. Decisiones arquitectónicas:

  1. La arquitectura queda dividida en cuatro capas:
     - Capa A: núcleo institucional universal;
     - Capa B: gobernanza específica de proyecto;
     - Capa C: legado y dominio;
     - Capa D: adaptadores por modelo.

  2. Los roles quedan definidos así:
     - Miguel: propietario y única autoridad para acciones irreversibles,
       excepciones, integración y cierre;
     - ChatGPT: arquitectura, metodología, evaluación crítica y síntesis;
     - Sonnet: análisis, planificación e implementación dentro del
       mandato autorizado;
     - Codex: auditor independiente y red team;
     - Gemini: investigación, contraste documental y análisis de
       mecanismos.

  3. `AGENTS.md` permanece como punto de entrada e índice operativo de
     la Capa A, sin fusionar en él todo el contenido normativo detallado.

  4. Los estados de tarea propuestos (`INTAKE` a `CERRADA`, junto con
     `BLOQUEADA` y `DETENIDA POR INCIDENTE`) complementan inicialmente
     los vocabularios vigentes de `REPORT_TEMPLATE.md` §8 y
     `AUDIT_TEMPLATE.md` §7; no los reemplazan durante la Fase 0.

  5. Los adaptadores por modelo se revisarán por el primero de los cinco
     eventos establecidos en §14 del plan, incluido un plazo máximo de
     90 días desde la última revisión.

  6. Queda definido el procedimiento para una futura autorización de la
     Fase 1: versionado del plan, auditoría independiente, corrección y
     reauditoría de hallazgos hasta obtener `APROBAR` vigente sobre el
     commit objetivo, y decisión expresa final de Miguel.

  B. Autorizaciones operacionales ya ejecutadas:

  1. Miguel autorizó expresamente el primer versionado documental del
     plan en la rama `plan/ai-governance-v1`, limitado únicamente a
     `docs/plan_arquitectura_gobernanza_multi_ia_v1.md`, sin push,
     merge, rebase, tag ni implementación.

     Esa autorización produjo el commit:

     `abeccd1ed4757b5abda5cbc7a0a3aae49a2f1838`

     con mensaje:

     `docs: versiona plan de arquitectura de gobernanza multi-IA v1`

  2. Miguel autorizó expresamente la auditoría independiente de Codex
     sobre ese commit y el versionado exclusivo de su informe en la rama
     `audit/codex-ai-governance-v1`, sin modificar el plan auditado,
     realizar push, merge, rebase, tag ni implementar hallazgos.

     Esa autorización produjo el commit:

     `c7db9a7616e75d502e556a43466762c8aa4623ca`

     con mensaje:

     `docs: registra auditoria Codex del plan de gobernanza multi-IA v1`

     El informe emitió veredicto `RECHAZAR` sobre el commit
     `abeccd1ed4757b5abda5cbc7a0a3aae49a2f1838`.

  C. Ramas excepcionales de Fase 0:

  Las familias `plan/*` y `audit/*` fueron autorizadas como excepciones
  operacionales para la Fase 0 de este plan. Esta decisión no las
  incorpora como política permanente de `AGENTS.md` §6. Su posible
  incorporación permanente queda reservada para una decisión posterior.

  D. No autorización:

  Esta entrada no autoriza el inicio de la Fase 1.

  Tampoco autoriza push, merge a `main`, tags, implementación de las
  Capas A-D, modificación de `AGENTS.md` o plantillas, ni ninguna
  modificación en `CLAUDEBOT`.

  La Fase 1 continúa pendiente y exige un veredicto `APROBAR` vigente
  sobre el commit objetivo, además de una decisión expresa posterior de
  Miguel registrada en este libro.

- Alcance / repositorio afectado:

  `CLAUDEBOT-CONTROL` únicamente. `CLAUDEBOT` no fue modificado; solo se
  consultaron referencias y verificaciones de procedencia de solo lectura
  durante la auditoría.

- Referencias:

  - plan inicial:
    `abeccd1ed4757b5abda5cbc7a0a3aae49a2f1838`;
  - auditoría Codex:
    `c7db9a7616e75d502e556a43466762c8aa4623ca`;
  - informe:
    `docs/auditoria_codex_plan_arquitectura_gobernanza_multi_ia_v1.md`.

---

## 2026-07-29 — Autorización de corrección y segundo versionado del plan de gobernanza multi-IA v1

- Contexto:

  El plan inicial fue versionado en el commit
  `abeccd1ed4757b5abda5cbc7a0a3aae49a2f1838` y auditado
  independientemente por Codex. El informe quedó versionado en
  `c7db9a7616e75d502e556a43466762c8aa4623ca`, con veredicto
  `RECHAZAR` y once hallazgos: H-01 a H-11.

  Sonnet preparó en la rama
  `control/sonnet-ai-governance-v1-r1` una corrección limitada a
  `docs/plan_arquitectura_gobernanza_multi_ia_v1.md`.

  ChatGPT revisó el documento corregido completo y su diff. Confirmó
  que las correcciones H-01 a H-11 fueron incorporadas materialmente
  y que el diff modifica únicamente el plan, pero detectó tres ajustes
  residuales obligatorios antes de versionarlo:

  1. esta edición no debe atribuir su autorización al commit
     `f00c42b626e49ed69816ca6847db164b28219b7d`, porque ese commit
     registra las decisiones arquitectónicas y las autorizaciones
     operacionales anteriores, no la autorización del segundo
     versionado correctivo;

  2. la metadata de rama debe identificar la rama de entrega de esta
     corrección, `control/sonnet-ai-governance-v1-r1`, y no presentar
     `plan/ai-governance-v1` como su rama actual;

  3. en §6, la frase “confirmado en esta misma revisión” debe
     reemplazarse por una formulación reproducible basada en el comando
     Git indicado.

- Autorización operacional de Miguel:

  Miguel ratifica la autorización para corregir H-01 a H-11 y autoriza
  que Sonnet aplique exclusivamente los tres ajustes residuales
  enumerados arriba al archivo:

  `docs/plan_arquitectura_gobernanza_multi_ia_v1.md`

  Después de una revisión final del diff, Miguel autoriza crear un único
  commit correctivo de ese archivo en la rama:

  `control/sonnet-ai-governance-v1-r1`

- Alcance autorizado:

  - un único archivo:
    `docs/plan_arquitectura_gobernanza_multi_ia_v1.md`;
  - incorporación de H-01 a H-11;
  - sustitución de la referencia de autorización de esta edición por el
    commit que contenga esta entrada;
  - corrección de la metadata de rama;
  - reemplazo de la frase dependiente de “esta misma revisión” en §6;
  - creación de un único commit documental posterior.

- Prohibiciones:

  Esta autorización no permite modificar nuevamente
  `decisions/OWNER_DECISIONS.md` después de esta entrada, ni modificar
  la auditoría Codex, `AGENTS.md`, `README.md`, plantillas u otros
  archivos.

  Tampoco permite push, merge, rebase, tag, eliminación de ramas,
  implementación de la Fase 1 ni modificación de `CLAUDEBOT`.

- No autorización:

  Esta entrada no autoriza el inicio de la Fase 1. El inicio continúa
  condicionado a una nueva auditoría independiente de Codex con
  veredicto `APROBAR` vigente sobre el nuevo commit objetivo y a una
  decisión posterior y expresa de Miguel.

---

## 2026-07-29 — Autorización de corrección N-01 del plan de gobernanza multi-IA v1

- Contexto:

  La reauditoría independiente de Codex sobre el commit objetivo
  `a4b646b780c121598194d56793e6a54d816f8260` quedó versionada en el
  commit `8f5734849600c2f02231448422e82bea83671de5`, con veredicto
  `RECHAZAR`.

  La reauditoría declaró cerrados H-01 a H-11 y registró un único
  hallazgo nuevo, N-01, de severidad MAYOR: §9 del plan no distingue
  inequívocamente entre una falta de autorización o evidencia que
  impide continuar legítimamente y una deficiencia documental no
  crítica dentro de un artefacto completamente auditable.

- Decisión interpretativa de Miguel:

  1. Corresponde `BLOQUEAR` cuando se cumpla al menos una de estas
     condiciones:

     - falta la autorización vigente necesaria para ejecutar o
       continuar la acción;
     - falta evidencia indispensable para determinar legítimamente el
       objeto, el alcance o la continuidad de la auditoría;
     - la auditoría no puede completarse legítimamente;
     - existe un hallazgo CRÍTICO.

  2. Corresponde `RECHAZAR` cuando el artefacto puede auditarse
     completamente y la ausencia o insuficiencia de autorización
     documentada o evidencia constituye un defecto no crítico,
     corregible y que no impide completar la auditoría.

  3. Que un artefacto sea completamente auditable no autoriza
     retroactivamente una acción ejecutada sin autorización. Un
     veredicto `RECHAZAR` impide aprobar, integrar o avanzar hasta que
     la deficiencia sea corregida y reauditorada.

  4. Esta interpretación queda alineada con
     `templates/AUDIT_TEMPLATE.md` §7 y mantiene coherente el precedente
     histórico de la auditoría inicial, que emitió `RECHAZAR` ante
     deficiencias documentales no críticas dentro de un artefacto
     completamente auditable.

- Autorización operacional:

  Miguel autoriza a Sonnet a corregir exclusivamente N-01 en §9 de:

  `docs/plan_arquitectura_gobernanza_multi_ia_v1.md`

  y, tras revisión del diff, a crear posteriormente un único commit
  correctivo del plan en la rama:

  `control/sonnet-ai-governance-v1-r2`

- Prohibiciones:

  Esta entrada no autoriza modificar todavía el plan durante esta
  operación.

  Tampoco autoriza modificar:

  - el informe de reauditoría;
  - la auditoría inicial;
  - `AGENTS.md`;
  - `README.md`;
  - `templates/`;
  - ningún otro archivo;
  - `CLAUDEBOT`.

  No autoriza push, merge, rebase, tags ni el inicio de la Fase 1.

---

## 2026-07-29 — Autorización de ajustes de trazabilidad para la corrección N-01

- Contexto:

  Sonnet aplicó en §9 de
  `docs/plan_arquitectura_gobernanza_multi_ia_v1.md` la corrección del
  hallazgo N-01, bajo la autorización registrada en el commit
  `fe748558013fe6c8d42c1ec3fe7ba2360a160be2`.

  ChatGPT revisó el diff completo y determinó que la clasificación entre
  `BLOQUEAR` y `RECHAZAR` quedó correctamente cerrada y alineada con
  `AUDIT_TEMPLATE.md` §7.

  Antes de crear el nuevo commit objetivo, deben actualizarse tres datos
  de trazabilidad para evitar que el plan quede documentalmente
  desactualizado:

  1. la rama de entrega de la nueva edición será
     `control/sonnet-ai-governance-v1-r2`, no
     `control/sonnet-ai-governance-v1-r1`;

  2. la historia fija debe registrar la reauditoría versionada en
     `8f5734849600c2f02231448422e82bea83671de5`, con veredicto
     `RECHAZAR`, H-01 a H-11 cerrados y N-01 como único hallazgo MAYOR
     abierto;

  3. §18 debe registrar
     `fe748558013fe6c8d42c1ec3fe7ba2360a160be2` como la autorización
     durable específica para corregir N-01 y crear el siguiente
     versionado correctivo.

- Supersesión explícita y temporal:

  Esta decisión amplía únicamente para esta corrección N-01 la
  restricción anterior que autorizaba modificar exclusivamente §9.

  La excepción permite editar además:

  - la cabecera del plan, solo para actualizar la historia de auditoría,
    la descripción de esta edición y la rama de entrega;
  - §18, solo para incorporar la autorización durable
    `fe748558013fe6c8d42c1ec3fe7ba2360a160be2`.

  No autoriza cambios sustantivos adicionales ni modificaciones en otras
  secciones.

  La ampliación termina con la creación del siguiente commit objetivo del
  plan en la rama `control/sonnet-ai-governance-v1-r2`.

- Autorización operacional:

  Miguel autoriza a Sonnet, después de versionar esta entrada, a mantener
  la corrección ya aplicada en §9 y realizar exclusivamente los ajustes
  de trazabilidad indicados en la cabecera y §18 de:

  `docs/plan_arquitectura_gobernanza_multi_ia_v1.md`

  Después de la revisión final del diff completo, podrá crearse un único
  commit objetivo en la rama:

  `control/sonnet-ai-governance-v1-r2`

- Prohibiciones:

  Esta operación actual no autoriza modificar todavía el plan.

  No autoriza modificar:

  - los informes de auditoría o reauditoría;
  - `AGENTS.md`;
  - `README.md`;
  - `templates/`;
  - ningún otro archivo;
  - `CLAUDEBOT`.

  Tampoco autoriza push, merge, rebase, tags ni el inicio de la Fase 1.

---

## 2026-07-29 — Autorización para cierre definitivo de N-01

- Contexto:

  La segunda reauditoría correctiva de Codex sobre el commit objetivo
  `4729f431207f903c7a0a8c344bd992c76c5ed3e6` quedó versionada en el
  commit `b601dc5d5e0ac4808d68e1bc1d46bd1698f90b75`, con veredicto
  `RECHAZAR`.

  H-01 a H-11 continúan cerrados y no se detectaron regresiones ni
  hallazgos nuevos independientes.

  N-01 permanece abierto, con severidad MAYOR, porque la lista
  exhaustiva de causales de `BLOQUEAR` en §9 restringe la imposibilidad
  de completar la auditoría al caso de ausencia de evidencia, mientras
  la decisión durable de Miguel y `templates/AUDIT_TEMPLATE.md` §7
  establecen como causal autónoma toda imposibilidad legítima de
  completar o continuar una auditoría.

- Decisión interpretativa definitiva de Miguel:

  Corresponde `BLOQUEAR` siempre que una auditoría no pueda completarse
  o continuar legítimamente, con independencia de que la causa sea una
  ausencia de evidencia u otra circunstancia que impida realizarla
  válidamente.

  Esta causal es autónoma y no depende de las otras causales de
  `BLOQUEAR`.

  Se mantiene sin modificación que:

  - todo hallazgo CRÍTICO obliga a `BLOQUEAR`;
  - una falta de autorización vigente indispensable para actuar obliga
    a `BLOQUEAR`;
  - la falta de evidencia indispensable para identificar legítimamente
    objeto, alcance o continuidad obliga a `BLOQUEAR`;
  - una deficiencia documental no crítica y corregible dentro de un
    artefacto completamente auditable produce `RECHAZAR`;
  - `RECHAZAR` impide aprobar, integrar o avanzar y no autoriza
    retroactivamente ninguna acción.

- Corrección textual autorizada:

  En §9 de:

  `docs/plan_arquitectura_gobernanza_multi_ia_v1.md`

  reemplazar exclusivamente la causal:

  “la ausencia de evidencia impide completar legítimamente la
  auditoría;”

  por:

  “la auditoría no puede completarse o continuar legítimamente, sea por
  ausencia de evidencia o por cualquier otra causa que impida
  realizarla válidamente;”

- Ajustes de trazabilidad autorizados:

  Para que la siguiente edición permanezca coherente con Git, también se
  autoriza actualizar exclusivamente:

  1. la cabecera del plan, para registrar:

     - `4729f431207f903c7a0a8c344bd992c76c5ed3e6` como commit objetivo
       anterior;
     - `b601dc5d5e0ac4808d68e1bc1d46bd1698f90b75` como segunda
       reauditoría correctiva con veredicto `RECHAZAR`;
     - H-01 a H-11 cerrados;
     - N-01 todavía abierto por la causal autónoma pendiente;
     - la rama de entrega
       `control/sonnet-ai-governance-v1-r3`;

  2. §18, únicamente para incorporar esa cadena y citar como
     autorización durable el commit que contenga esta entrada.

  La cabecera y §18 no pueden declarar que N-01 está cerrado ni que
  existe `APROBAR` antes de la siguiente auditoría independiente.

- Autorización operacional:

  Después de versionar esta entrada y recibir revisión del diff,
  Miguel autoriza a Sonnet a:

  - aplicar la sustitución textual exacta en §9;
  - actualizar únicamente la trazabilidad de la cabecera y §18;
  - preparar un único nuevo commit objetivo en la rama
    `control/sonnet-ai-governance-v1-r3`.

  La creación del commit del plan requiere revisión previa del diff
  final por ChatGPT.

- Prohibiciones:

  Esta operación actual no autoriza modificar todavía el plan.

  No autoriza modificar:

  - informes de auditoría o reauditoría;
  - `AGENTS.md`;
  - `README.md`;
  - `templates/`;
  - ningún otro archivo;
  - `CLAUDEBOT`.

  No autoriza push, merge, rebase, tags ni el inicio de la Fase 1.

---

## 2026-07-29 — Autorización de ajustes residuales finales para N-01

- Contexto:

  Sonnet aplicó la causal autónoma de `BLOQUEAR` autorizada en el commit
  `8605c11f06bc925da695b40f274a11533485934b` y actualizó la
  trazabilidad de la cabecera y §18 del plan.

  ChatGPT revisó el diff completo y confirmó que la corrección
  sustantiva de N-01 está correctamente formulada, pero detectó dos
  expresiones residuales que deben corregirse antes del siguiente
  versionado:

  1. §9 todavía atribuye la clasificación vigente únicamente al commit
     `fe748558013fe6c8d42c1ec3fe7ba2360a160be2`, aunque la causal
     autónoma definitiva fue establecida por la decisión registrada en
     `8605c11f06bc925da695b40f274a11533485934b`;

  2. la cabecera afirma que esta edición “incorpora el cierre documental
     definitivo de N-01” y después aclara que todavía no declara N-01
     cerrado, generando una contradicción textual.

- Autorización operacional:

  Miguel autoriza a Sonnet, después de versionar esta entrada, a realizar
  exclusivamente estos dos reemplazos en:

  `docs/plan_arquitectura_gobernanza_multi_ia_v1.md`

  Primer reemplazo, en §9:

  Reemplazar:

  Sin estados intermedios. La clasificación entre `BLOQUEAR` y
  `RECHAZAR` se determina mediante las siguientes reglas, registradas por
  decisión de Miguel en el commit
  `fe748558013fe6c8d42c1ec3fe7ba2360a160be2` y alineadas con
  `AUDIT_TEMPLATE.md` §7:

  por:

  Sin estados intermedios. La clasificación entre `BLOQUEAR` y
  `RECHAZAR` se determina mediante las siguientes reglas, consolidadas
  por la decisión interpretativa definitiva de Miguel registrada en el
  commit `8605c11f06bc925da695b40f274a11533485934b` y alineadas con
  `AUDIT_TEMPLATE.md` §7:

  Segundo reemplazo, en la cabecera:

  Reemplazar:

  **Esta edición** conserva cerrados H-01 a H-11 e incorpora el cierre
  documental definitivo de N-01 en §9, estableciendo como causal autónoma
  de `BLOQUEAR` toda imposibilidad legítima de completar o continuar una
  auditoría, con independencia de que se origine en ausencia de evidencia
  o en otra causa que impida realizarla válidamente.

  por:

  **Esta edición** conserva cerrados H-01 a H-11 e incorpora la
  corrección documental definitiva propuesta para cerrar N-01 en §9,
  estableciendo como causal autónoma de `BLOQUEAR` toda imposibilidad
  legítima de completar o continuar una auditoría, con independencia de
  que se origine en ausencia de evidencia o en otra causa que impida
  realizarla válidamente.

  Después de la revisión final del diff, podrá crearse un único commit
  objetivo del plan en la rama:

  `control/sonnet-ai-governance-v1-r3`

- Alcance y duración:

  Esta autorización amplía exclusivamente la operación N-01 para los dos
  reemplazos anteriores.

  La ampliación termina cuando se cree el siguiente commit objetivo del
  plan. No autoriza ningún otro cambio sustantivo o de trazabilidad.

- Prohibiciones:

  Esta operación actual no autoriza modificar todavía el plan.

  No autoriza modificar:

  - informes de auditoría o reauditoría;
  - `AGENTS.md`;
  - `README.md`;
  - `templates/`;
  - ningún otro archivo;
  - `CLAUDEBOT`.

  No autoriza push, merge, rebase, tags ni el inicio de la Fase 1.

---

## 2026-07-29 — Registro del APROBAR vigente del plan de gobernanza multi-IA v1

- Evidencia auditada:

  El commit objetivo vigente del plan es:

  `e492f0efcf206786f935ffb1750236f5d3cfdd0c`

  La tercera reauditoría correctiva independiente de Codex quedó
  versionada en:

  `8fda9bc95b60d02f5894dcb9e69bff63522e2d23`

  El informe cita y audita exactamente el commit objetivo anterior.

- Resultado:

  Codex emitió el veredicto:

  `APROBAR`

  La auditoría confirmó:

  - N-01 `CERRADO`, sin severidad residual;
  - H-01 a H-11 `CERRADOS`, sin regresiones;
  - ningún hallazgo nuevo;
  - ningún hallazgo abierto;
  - ningún hallazgo `CRÍTICO`.

- Decisión de Miguel:

  Miguel acepta y registra como vigente el veredicto `APROBAR` de Codex
  sobre el commit objetivo
  `e492f0efcf206786f935ffb1750236f5d3cfdd0c`.

  Con esta decisión queda satisfecha la etapa `APROBAR vigente`
  definida en §18 del plan.

- Límites de esta decisión:

  Este registro no autoriza todavía:

  - merge a `main`;
  - push;
  - creación de tags;
  - borrado de ramas o worktrees;
  - inicio de la Fase 1;
  - creación de documentos o carpetas de la Fase 1;
  - modificación de `CLAUDEBOT`.

  La integración del plan y la posible autorización de la Fase 1 serán
  decisiones expresas, separadas y posteriores de Miguel.
