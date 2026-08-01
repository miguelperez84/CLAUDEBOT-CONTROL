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

---

## 2026-07-29 — Autorización de integración fast-forward del plan multi-IA v1

- Evidencia previa:

  El commit objetivo
  `e492f0efcf206786f935ffb1750236f5d3cfdd0c` fue auditado
  independientemente por Codex en el commit
  `8fda9bc95b60d02f5894dcb9e69bff63522e2d23`, con veredicto
  `APROBAR`.

  El `APROBAR` vigente quedó registrado durablemente en el commit
  `53492a5e9cd7caca7cd13abb7138b83b570f9ed7`.

  N-01 está cerrado; H-01 a H-11 permanecen cerrados; no existen
  hallazgos abiertos, nuevos, regresiones ni hallazgos críticos.

- Verificación de integración:

  Al momento de esta decisión:

  - `main` y `origin/main` resuelven ambos a
    `3ae42cdebbb0a635a85d958684251a6a5769b595`;
  - su divergencia es `0 0`;
  - `main` es ancestro de
    `control/sonnet-ai-governance-v1-approval`;
  - la integración puede realizarse mediante avance lineal
    `--ff-only`, sin commit de merge ni resolución de conflictos.

- Decisión de Miguel:

  Miguel autoriza integrar la rama:

  `control/sonnet-ai-governance-v1-approval`

  en:

  `main`

  exclusivamente mediante:

  `git merge --ff-only control/sonnet-ai-governance-v1-approval`

  La integración deberá realizarse desde el worktree principal:

  `/home/miguel/proyectos/CLAUDEBOT-CONTROL`

  y solo después de comprobar nuevamente que:

  - `main` sigue apuntando a
    `3ae42cdebbb0a635a85d958684251a6a5769b595`;
  - `origin/main` sigue coincidiendo con `main`;
  - el árbol está limpio;
  - `main` continúa siendo ancestro de la rama aprobada.

- Límites:

  Esta autorización permite únicamente registrar esta decisión y,
  posteriormente, realizar el merge local `--ff-only`.

  No autoriza:

  - push;
  - merge que no sea fast-forward;
  - rebase;
  - creación de tags;
  - borrado de ramas o worktrees;
  - modificación posterior del plan;
  - modificación de CLAUDEBOT;
  - inicio de la Fase 1;
  - creación de carpetas o documentos de la Fase 1.

  El push y la autorización de Fase 1 requieren decisiones expresas y
  separadas de Miguel.

---

## 2026-07-29 — Autorización de push del plan multi-IA v1

- Evidencia previa:

  El commit objetivo
  `e492f0efcf206786f935ffb1750236f5d3cfdd0c` fue aprobado por la
  tercera reauditoría independiente de Codex versionada en
  `8fda9bc95b60d02f5894dcb9e69bff63522e2d23`.

  El veredicto `APROBAR` quedó registrado durablemente en
  `53492a5e9cd7caca7cd13abb7138b83b570f9ed7`.

  La integración local fue autorizada en
  `91a8fd5f762fed4215f91ba024dd185b20ea8f8c` y se realizó mediante
  `git merge --ff-only`, dejando `main` y
  `control/sonnet-ai-governance-v1-approval` alineadas en ese hash.

- Estado previo al push:

  Al momento de la integración:

  - `main` local resolvía a
    `91a8fd5f762fed4215f91ba024dd185b20ea8f8c`;
  - `origin/main` resolvía a
    `3ae42cdebbb0a635a85d958684251a6a5769b595`;
  - la divergencia `origin/main...main` era `0 16`;
  - el árbol estaba limpio;
  - no se había ejecutado push, rebase ni tag.

- Decisión de Miguel:

  Miguel autoriza publicar la cadena aprobada en `origin/main`
  exclusivamente mediante:

  `git push origin main`

  Antes del push deberá:

  1. integrarse este registro a `main` mediante fast-forward only;
  2. ejecutarse `git fetch origin main`;
  3. comprobarse que `origin/main` no avanzó desde
     `3ae42cdebbb0a635a85d958684251a6a5769b595`;
  4. comprobarse que el árbol está limpio;
  5. comprobarse que `origin/main` es ancestro de `main`.

  Si `origin/main` cambió, el push queda detenido y deberá revisarse
  nuevamente antes de continuar.

- Límites:

  Esta autorización permite exclusivamente:

  - registrar esta decisión;
  - integrar este registro a `main` mediante `--ff-only`;
  - ejecutar `git push origin main` después de las verificaciones
    anteriores.

  No autoriza:

  - force push;
  - push de otras ramas;
  - rebase;
  - creación de tags;
  - borrado de ramas o worktrees;
  - modificación posterior del plan;
  - modificación de `CLAUDEBOT`;
  - inicio de la Fase 1;
  - creación de carpetas, mandatos o documentos de la Fase 1.

  La Fase 1 requiere una decisión expresa, separada y posterior de
  Miguel.

---

## 2026-07-31 — Apertura controlada de la Fase 1 de gobernanza multi-IA

- Evidencia habilitante:

  El plan de arquitectura de gobernanza multi-IA v1 está integrado y
  publicado en `main`.

  Su commit objetivo
  `e492f0efcf206786f935ffb1750236f5d3cfdd0c` recibió veredicto
  `APROBAR` en la tercera reauditoría independiente de Codex versionada
  en `8fda9bc95b60d02f5894dcb9e69bff63522e2d23`.

  N-01 y H-01 a H-11 están cerrados, sin hallazgos abiertos,
  regresiones ni severidad residual.

  `main` y `origin/main` están alineados en
  `129a82cc99913d493290f5f56fd5b2ee18568fb2`.

- Decisión de Miguel:

  Miguel autoriza abrir la Fase 1 descrita en §17 del plan de
  arquitectura multi-IA v1.

  La Fase 1 tendrá por objeto:

  1. redactar y preparar para congelamiento los documentos canónicos de
     Capa A;
  2. redactar y preparar para congelamiento el primer perfil de Capa B
     para `CLAUDEBOT`;
  3. actualizar `AGENTS.md` como puerta de entrada e índice, sin
     duplicar íntegramente los documentos canónicos;
  4. fijar la ubicación exacta de Capa A y Capa B;
  5. definir el mecanismo de registro y revisión de adaptadores.

- Apertura controlada:

  En esta primera operación se autoriza exclusivamente redactar,
  revisar, versionar y auditar:

  - `tasks/AI-GOV-F1-CANONICAL/MANDATE.md`;
  - `tasks/AI-GOV-F1-CANONICAL/ACCEPTANCE.md`.

  La implementación no queda autorizada hasta que:

  - ChatGPT revise el mandato;
  - Codex audite el commit exacto del mandato;
  - el informe de auditoría quede versionado;
  - Miguel emita una autorización operacional posterior.

- Prohibiciones:

  Esta decisión no autoriza todavía:

  - modificar `AGENTS.md`;
  - crear archivos bajo `governance/` o `reports/`;
  - crear `judgment/`, `adapters/` o `tests/`;
  - modificar o abrir archivos de `CLAUDEBOT`;
  - abrir datasets, CSV, resultados, discovery, OOS o producción;
  - ejecutar código científico;
  - push, merge, rebase o tags;
  - borrar ramas o worktrees.

---

## 2026-07-31 — Adenda para auditoría independiente del mandato de Fase 1

- Evidencia:

  El mandato y los criterios de aceptación de la Fase 1 quedaron
  versionados en el commit exacto
  `bdeff1eb9b0afcd94be220dd14439c21bd8a7dd8`.

- Decisión de Miguel:

  Miguel autoriza a Codex, como auditor independiente, a auditar
  exclusivamente ese commit exacto.

- Alcance autorizado para Codex:

  1. auditar como artefactos objetivo exclusivamente:

     - `tasks/AI-GOV-F1-CANONICAL/MANDATE.md`;
     - `tasks/AI-GOV-F1-CANONICAL/ACCEPTANCE.md`;

     ambos exactamente como existen en el commit:

     `bdeff1eb9b0afcd94be220dd14439c21bd8a7dd8`;

  2. verificar el diff exacto entre:

     - padre:
       `129a82cc99913d493290f5f56fd5b2ee18568fb2`;
     - commit objetivo:
       `bdeff1eb9b0afcd94be220dd14439c21bd8a7dd8`;

  3. leer como evidencia institucional de apoyo exclusivamente:

     - `AGENTS.md`;
     - `templates/AUDIT_TEMPLATE.md`;
     - `decisions/OWNER_DECISIONS.md`;
     - `docs/plan_arquitectura_gobernanza_multi_ia_v1.md`;
     - `docs/reauditoria_codex_plan_arquitectura_gobernanza_multi_ia_v1_r3.md`;

  4. consultar metadatos Git de solo lectura necesarios para
     comprobar:

     - rama;
     - HEAD;
     - padre del commit objetivo;
     - diff;
     - archivos incluidos;
     - estado del árbol.

     No se autoriza a Codex a abrir ninguna otra ruta del repositorio
     ni a abrir o consultar `CLAUDEBOT`.

  5. crear exclusivamente el archivo:

     `reports/AI-GOV-F1-CANONICAL/MANDATE_AUDIT_CODEX.md`;

     Codex queda autorizado a agregar al índice exclusivamente ese
     archivo y crear un único commit en su propia rama de auditoría.

     Ese commit deberá contener exclusivamente:

     `reports/AI-GOV-F1-CANONICAL/MANDATE_AUDIT_CODEX.md`

     El mensaje autorizado será:

     `docs: audita mandato de Fase 1`

     La rama, el worktree y el commit base exactos de la auditoría se
     fijarán en la instrucción operacional posterior de Miguel, una
     vez versionada esta adenda.

     Esta autorización de commit no autoriza push, merge, rebase ni
     tags.

  6. emitir exactamente uno de estos veredictos:

     `APROBAR`, `RECHAZAR` o `BLOQUEAR`.

- Prohibiciones:

  Esta autorización no permite a Codex:

  - modificar
    `tasks/AI-GOV-F1-CANONICAL/MANDATE.md`;
  - modificar
    `tasks/AI-GOV-F1-CANONICAL/ACCEPTANCE.md`;
  - modificar `AGENTS.md`;
  - crear o modificar documentos de implementación bajo
    `governance/`;
  - iniciar la implementación de la Fase 1;
  - abrir o modificar `CLAUDEBOT`;
  - modificar ningún archivo distinto de
    `reports/AI-GOV-F1-CANONICAL/MANDATE_AUDIT_CODEX.md`;
  - hacer push, merge, rebase o tags;
  - modificar ni incluir en el commit de auditoría
    `decisions/OWNER_DECISIONS.md`;
  - agregar al índice ningún archivo distinto de
    `reports/AI-GOV-F1-CANONICAL/MANDATE_AUDIT_CODEX.md`;
  - auditar una revisión distinta del commit objetivo
    `bdeff1eb9b0afcd94be220dd14439c21bd8a7dd8`.

- Condición de avance:

  La implementación de la Fase 1 continúa sin autorizarse.

  Solo podrá evaluarse una autorización operacional posterior cuando:

  - Codex haya auditado el commit exacto indicado;
  - el informe haya quedado versionado;
  - el veredicto vigente sea `APROBAR`;
  - Miguel emita una decisión posterior, expresa y durable.

---

## 2026-07-31 — Autorización de corrección H-01 a H-05 del mandato de Fase 1

- Evidencia:

  La auditoría independiente de Codex sobre el commit objetivo
  `bdeff1eb9b0afcd94be220dd14439c21bd8a7dd8`
  (`tasks/AI-GOV-F1-CANONICAL/MANDATE.md` y
  `tasks/AI-GOV-F1-CANONICAL/ACCEPTANCE.md`) quedó versionada en el
  commit `749ab3c73383984a2f893236835387d20709c71c`
  (`reports/AI-GOV-F1-CANONICAL/MANDATE_AUDIT_CODEX.md`, rama
  `audit/codex-ai-gov-f1-mandate`), con veredicto `RECHAZAR`.

  El informe registró cinco hallazgos, todos de severidad MAYOR, sin
  hallazgos críticos ni menores:

  - H-01: la descripción de la operación de apertura como limitada a
    redactar `MANDATE.md` y `ACCEPTANCE.md` no coincidía con el diff
    real del commit objetivo, que también modifica
    `decisions/OWNER_DECISIONS.md`;
  - H-02: la matriz de `ACCEPTANCE.md` verificaba A-02 a A-12
    principalmente contra el working tree, sin anclar la lectura al
    commit objetivo mediante `git show`;
  - H-03: `MANDATE.md` restringe la lectura de `CLAUDEBOT` a cuatro
    rutas mediante `git show <SHA>:<ruta>`, mientras A-15 y A-17 de
    `ACCEPTANCE.md` exigían `rev-parse HEAD` y `status --short` sobre
    un working tree móvil, sin autorización expresa para ello;
  - H-04: A-21 exigía una entrada que cite un commit de auditoría con
    `APROBAR`, creando una circularidad con la propia auditoría de
    implementación que debe emitir ese `APROBAR`;
  - H-05: A-20 usaba `governance/` completo como alcance de lectura,
    en vez de la lista literal cerrada de rutas autorizadas en
    `MANDATE.md`.

- Decisión de Miguel:

  Miguel autoriza a Sonnet a corregir exclusivamente H-01 a H-05 en:

  - `tasks/AI-GOV-F1-CANONICAL/MANDATE.md`;
  - `tasks/AI-GOV-F1-CANONICAL/ACCEPTANCE.md`.

  Para H-03, Miguel autoriza específicamente sustituir la exposición
  de los dos comandos de metadatos Git de `CLAUDEBOT` por un único
  concepto cerrado, la **huella de estado de `CLAUDEBOT`**: el par de
  resultados producido por

  ```text
  git -C /home/miguel/proyectos/CLAUDEBOT rev-parse HEAD

  git -C /home/miguel/proyectos/CLAUDEBOT \
    status --porcelain=v1 -z | sha256sum
  ```

  es decir, el SHA completo de `HEAD` y el SHA-256 de la salida de
  `status --porcelain=v1 -z`, comparados entre el momento anterior y
  el posterior a la lectura autorizada de las cuatro rutas: ambos
  resultados deben ser exactamente iguales. No se registra ni se
  expone la salida textual de `status`, ni nombres de archivos o
  rutas provenientes de ella; un estado previo ajeno a la tarea, si
  existiera, queda representado únicamente por su SHA-256. Esta
  huella no autoriza ejecutar ningún comando Git distinto de los dos
  anteriores ni abrir ningún archivo adicional de `CLAUDEBOT`.

- Alcance autorizado para Sonnet:

  1. en `MANDATE.md` §3, aclarar que la operación de apertura redactó
     exclusivamente `MANDATE.md` y `ACCEPTANCE.md`, y que la
     modificación de `decisions/OWNER_DECISIONS.md` en el commit
     objetivo es una acción separada, bajo la facultad exclusiva de
     `append` de Miguel sobre ese libro (H-01);
  2. en `ACCEPTANCE.md`, anclar al commit objetivo de implementación,
     mediante `git show <commit-objetivo-implementación>:<ruta>`, la
     verificación de A-02 a A-12 (H-02);
  3. en `MANDATE.md` §3, sustituir la restricción de lectura de
     `CLAUDEBOT` por la huella de estado definida arriba, y reflejar
     ese mismo nombre en A-15 y A-17 de `ACCEPTANCE.md` (H-03);
  4. en `ACCEPTANCE.md`, separar A-21 como criterio de cierre de la
     Fase 1, evaluado en una operación posterior y distinta de la
     auditoría de implementación de A-01 a A-20, sin que A-21
     condicione el veredicto de esa auditoría (H-04);
  5. en `ACCEPTANCE.md`, reemplazar en A-20 el alcance `governance/`
     completo por la lista literal cerrada de los tres documentos
     autorizados en `MANDATE.md` §3 (H-05).

- Prohibiciones:

  Esta autorización no permite:

  - modificar ningún archivo distinto de
    `tasks/AI-GOV-F1-CANONICAL/MANDATE.md` y
    `tasks/AI-GOV-F1-CANONICAL/ACCEPTANCE.md`;
  - modificar `decisions/OWNER_DECISIONS.md` fuera de esta misma
    entrada;
  - modificar `AGENTS.md`, `README.md` ni `templates/`;
  - crear archivos bajo `governance/` o `reports/`;
  - iniciar la implementación de la Fase 1;
  - abrir o modificar `CLAUDEBOT`;
  - declarar cerrados H-01 a H-05 antes de una nueva auditoría
    independiente de Codex con veredicto `APROBAR` sobre el nuevo
    commit objetivo;
  - push, merge, rebase o tags;
  - borrar ramas o worktrees.

- Condición de avance:

  La implementación de la Fase 1 continúa sin autorizarse.

  Antes de continuar, se requiere:

  - un único commit correctivo que contenga exclusivamente
    `tasks/AI-GOV-F1-CANONICAL/MANDATE.md` y
    `tasks/AI-GOV-F1-CANONICAL/ACCEPTANCE.md`;
  - una nueva auditoría independiente de Codex sobre ese commit
    objetivo;
  - el informe de esa auditoría versionado, citando el commit exacto;
  - veredicto `APROBAR` vigente sobre ese commit;
  - una decisión posterior, expresa y durable de Miguel.

---

## 2026-07-31 — Adenda para reauditoría independiente del mandato de Fase 1

- Evidencia:

  El commit correctivo que aplica H-01 a H-05 quedó versionado en
  `3fd6eec12abc33666a6286a337a38899839039cd`, hijo directo de
  `33a437ff0b77128d197cc93a3cc17aafc41aa7b7` (la decisión durable que
  autorizó esas correcciones), y modifica exclusivamente
  `tasks/AI-GOV-F1-CANONICAL/MANDATE.md` y
  `tasks/AI-GOV-F1-CANONICAL/ACCEPTANCE.md`.

  La primera auditoría independiente de Codex quedó versionada en
  `749ab3c73383984a2f893236835387d20709c71c`
  (`reports/AI-GOV-F1-CANONICAL/MANDATE_AUDIT_CODEX.md`, rama
  `audit/codex-ai-gov-f1-mandate`), con veredicto `RECHAZAR` y cinco
  hallazgos MAYOR (H-01 a H-05), sin críticos ni menores.

- Decisión de Miguel:

  Miguel autoriza a Codex, como auditor independiente, a reauditar
  exclusivamente el commit `3fd6eec12abc33666a6286a337a38899839039cd`.

- Alcance autorizado para Codex:

  1. auditar como artefactos objetivo exclusivamente:

     - `tasks/AI-GOV-F1-CANONICAL/MANDATE.md`;
     - `tasks/AI-GOV-F1-CANONICAL/ACCEPTANCE.md`;

     ambos exactamente como existen en el commit:

     `3fd6eec12abc33666a6286a337a38899839039cd`;

  2. verificar el diff exacto entre:

     - padre: `33a437ff0b77128d197cc93a3cc17aafc41aa7b7`;
     - commit objetivo: `3fd6eec12abc33666a6286a337a38899839039cd`;

  3. leer, como evidencia institucional de apoyo exclusivamente:

     - `AGENTS.md`;
     - `templates/AUDIT_TEMPLATE.md`;
     - `decisions/OWNER_DECISIONS.md`;
     - `docs/plan_arquitectura_gobernanza_multi_ia_v1.md`;
     - `docs/reauditoria_codex_plan_arquitectura_gobernanza_multi_ia_v1_r3.md`;

  4. leer, exclusivamente por su commit fijo e inmutable, el informe
     de la primera auditoría:

     `749ab3c73383984a2f893236835387d20709c71c:reports/AI-GOV-F1-CANONICAL/MANDATE_AUDIT_CODEX.md`

     únicamente para verificar si H-01 a H-05 quedaron corregidos; no
     se autoriza leer ningún otro archivo de esa rama ni de ese commit;

     El informe anterior constituye exclusivamente evidencia
     comparativa auxiliar para verificar el tratamiento de H-01 a
     H-05. Su lectura no sustituye, reduce ni limita la obligación de
     Codex de realizar una reauditoría completa, independiente y
     desde cero de los dos artefactos objetivo tal como existen en el
     commit `3fd6eec12abc33666a6286a337a38899839039cd`. Codex deberá
     evaluar nuevamente el mandato completo, la matriz A-01 a A-21,
     las contradicciones internas, los permisos, las rutas, la
     ejecutabilidad y la conformidad institucional, aunque un aspecto
     no haya sido objeto de los cinco hallazgos anteriores.

  5. consultar metadatos Git de solo lectura necesarios para
     comprobar: rama; HEAD; padre del commit objetivo; diff; archivos
     incluidos; estado del árbol;

     No se autoriza a Codex a abrir ninguna otra ruta del repositorio
     ni a abrir o consultar `CLAUDEBOT`.

  6. crear exclusivamente el archivo:

     `reports/AI-GOV-F1-CANONICAL/MANDATE_AUDIT_CODEX_R2.md`;

     Codex queda autorizado a agregar al índice exclusivamente ese
     archivo y crear un único commit en su propia rama de auditoría.

     Ese commit deberá contener exclusivamente:

     `reports/AI-GOV-F1-CANONICAL/MANDATE_AUDIT_CODEX_R2.md`

     El mensaje autorizado será:

     `docs: reaudita mandato de Fase 1`

     La rama, el worktree y el commit base exactos de la auditoría se
     fijarán en la instrucción operacional posterior de Miguel, una
     vez versionada esta adenda.

     Esta autorización de commit no autoriza push, merge, rebase ni
     tags.

  7. emitir exactamente uno de estos veredictos:

     `APROBAR`, `RECHAZAR` o `BLOQUEAR`.

- Prohibiciones:

  Esta autorización no permite a Codex:

  - modificar `tasks/AI-GOV-F1-CANONICAL/MANDATE.md`;
  - modificar `tasks/AI-GOV-F1-CANONICAL/ACCEPTANCE.md`;
  - modificar `AGENTS.md`;
  - crear o modificar documentos de implementación bajo `governance/`;
  - iniciar la implementación de la Fase 1;
  - abrir o modificar `CLAUDEBOT`;
  - modificar ningún archivo distinto de
    `reports/AI-GOV-F1-CANONICAL/MANDATE_AUDIT_CODEX_R2.md`;
  - modificar ni incluir en el commit de auditoría
    `decisions/OWNER_DECISIONS.md`;
  - agregar al índice ningún archivo distinto de
    `reports/AI-GOV-F1-CANONICAL/MANDATE_AUDIT_CODEX_R2.md`;
  - auditar una revisión distinta del commit objetivo
    `3fd6eec12abc33666a6286a337a38899839039cd`;
  - abrir, consultar o usar el working tree o la rama anterior
    `audit/codex-ai-gov-f1-mandate`; la única evidencia autorizada de
    la auditoría anterior es el blob literal del informe obtenido
    mediante `git show` contra el commit exacto indicado en esta
    adenda;
  - hacer push, merge, rebase o tags.

- Condición de avance:

  La implementación de la Fase 1 continúa sin autorizarse.

  Solo podrá evaluarse una autorización operacional posterior cuando:

  - Codex haya reauditado el commit exacto indicado;
  - el informe haya quedado versionado;
  - el veredicto vigente sea `APROBAR`;
  - Miguel emita una decisión posterior, expresa y durable.
