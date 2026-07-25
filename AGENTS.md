# AGENTS.md — Reglas de operación de CLAUDEBOT-CONTROL

Puerta común para todo agente de IA (Sonnet, Codex, Gemini u otro) que
lea, escriba o audite documentos en este repositorio, o que actúe sobre
`CLAUDEBOT` a partir de un mandato aquí registrado.

## 1. Autoridad

- **Miguel es la única autoridad para autorizar acciones
  irreversibles.** Ningún agente autoriza por sí mismo push, merge a
  rama rectora, apertura de datasets, corridas de discovery/OOS,
  modificación de producción, ni ampliación de alcance de un mandato.
- **Una aprobación del auditor no reemplaza la autorización de
  Miguel.** Un veredicto "APTO" de Codex o Gemini es insumo para la
  decisión, no la decisión.
- **Una autorización no se hereda automáticamente a la siguiente
  fase.** Aprobar la fase N no autoriza la fase N+1; cada fase exige su
  propia autorización explícita.

## 2. Aislamiento entre agentes

- **Una IA modifica solamente su propia rama o worktree.** Ningún
  agente escribe en la rama o worktree asignado a otro agente.
- **Sonnet, Codex y Gemini trabajan en ramas o worktrees separados**,
  siguiendo la convención de ramas (§5).
- **Los auditores no modifican el artefacto auditado.** Un agente que
  audita un mandato, informe o pieza documental produce su propio
  informe de auditoría; no edita el original.

## 3. Decisión y bloqueo

- **No se decide por mayoría.** Que dos de tres agentes coincidan no
  produce un veredicto válido por sí solo; la decisión sigue
  requiriendo autorización de Miguel cuando la acción es irreversible o
  amplía alcance.
- **Un hallazgo crítico bloquea el avance.** Si cualquier agente
  (incluido un auditor) reporta un hallazgo crítico, la tarea se
  detiene hasta resolución explícita, sin importar cuántos otros
  agentes hayan aprobado.

## 4. Estructura obligatoria de mandatos

Todo mandato (`tasks/<ID-TAREA>/MANDATE.md`) debe identificar:

1. repositorio objetivo;
2. rama;
3. commit base;
4. archivos autorizados (lista cerrada, rutas literales);
5. prohibiciones;
6. criterios de aceptación.

Ver `templates/TASK_TEMPLATE.md`.

## 5. Estructura obligatoria de informes

Todo informe (`reports/<ID-TAREA>/*.md`) debe declarar:

1. archivos abiertos;
2. archivos modificados;
3. comandos ejecutados;
4. estado Git final.

Ver `templates/REPORT_TEMPLATE.md` y `templates/AUDIT_TEMPLATE.md`.

## 6. Entregas y ramas

- **Cada entrega debe terminar en un commit identificable** en la rama
  o worktree propio del agente.
- **Ningún agente puede hacer merge a una rama rectora sin autorización
  de Miguel.**
- Convención de ramas:

```text
control/task-<id>
control/sonnet-<id>
control/codex-<id>
control/gemini-<id>
```

## 7. Alcance de este repositorio

- Este repositorio coordina documentación; no ejecuta código
  científico. Ningún agente debe abrir datasets, CSV, resultados de
  discovery/OOS ni archivos de producción del proyecto `CLAUDEBOT`
  desde una tarea de `CLAUDEBOT-CONTROL`.
- Un mandato que requiera tocar `CLAUDEBOT` debe declarar explícitamente
  ese repositorio objetivo, y sigue sujeto a las reglas de alcance
  vigentes de `CLAUDEBOT` (`AGENTS.md` y la Constitución de ese
  repositorio), no solo a las de este documento.
