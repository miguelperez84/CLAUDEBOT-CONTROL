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
