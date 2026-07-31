# MANDATE.md — AI-GOV-F1-CANONICAL

## 1. Identificación

- **Repositorio objetivo:** CLAUDEBOT-CONTROL
- **Rama prevista de implementación:**
  `control/sonnet-ai-gov-f1-canonical`
- **Commit base documental de este mandato:**
  `129a82cc99913d493290f5f56fd5b2ee18568fb2`
- **Commit base de implementación:**
  PENDIENTE DE FIJACIÓN. Este mandato no es ejecutable mientras una
  autorización operacional posterior de Miguel no registre el SHA
  completo exacto de `main` desde el cual se cree el worktree de
  implementación.
- **Agente implementador:** Sonnet
- **Auditor independiente:** Codex
- **Autoridad final:** Miguel
- **Revisión metodológica:** ChatGPT
- **Fecha del mandato:** 2026-07-31

La autorización operacional posterior deberá fijar también:

1. el SHA completo del commit base de implementación en
   `CLAUDEBOT-CONTROL`;
2. el SHA completo e inmutable de `CLAUDEBOT` autorizado como fuente
   documental secundaria.

Si cualquiera de esos hashes falta, no coincide o cambia antes de
comenzar, corresponde `BLOQUEAR`.

## 2. Objetivo

Definir y redactar la primera versión canónica de:

### Capa A

- autoridad;
- precedencia documental;
- permisos;
- control de alcance;
- veredictos y estados;
- resolución de conflictos.

### Capa B

- primer perfil para `CLAUDEBOT`;
- restricciones adicionales del proyecto;
- referencias inmutables a documentos rectores;
- estado y límites de fases;
- rutas de mandatos, informes y documentos congelados;
- relación con Capa A sin relajar reglas universales.

### AGENTS.md

Actualizarlo para que permanezca como puerta de entrada e índice,
conserve las prohibiciones críticas y enlace los documentos canónicos
sin copiar íntegramente su contenido.

### Revisión de adaptadores

Definir un mecanismo obligatorio que registre:

- modelo y versión;
- fecha de última revisión;
- evento disparador;
- evidencia o commit citable;
- estado `VIGENTE`, `REVISIÓN REQUERIDA` o
  `HIPÓTESIS NO VALIDADA`;
- responsable de la propuesta;
- auditor independiente;
- decisión de Miguel.

Además de estos campos, `governance/core/ADAPTER_REVIEW_POLICY.md`
deberá definir de manera inequívoca:

- la ubicación física exacta donde se registra cada revisión;
- si el registro vive en el encabezado de cada adaptador, en un
  registro central futuro o mediante otro mecanismo único;
- el procedimiento para crear y actualizar una entrada;
- la evidencia Git mínima exigida;
- cuál agente propone;
- cuál agente audita;
- cómo Miguel registra su decisión;
- cómo se conserva el historial sin reescribir entradas anteriores.

La política debe incluir expresamente los cinco eventos de revisión
obligatoria establecidos por el plan, aplicándose el que ocurra
primero:

1. cambio mayor o relevante del modelo;
2. incidente de gobernanza;
3. desviación conductual comprobada;
4. cambio material en las herramientas disponibles para el modelo;
5. cumplimiento de 90 días desde la última revisión.

La Fase 1 define este mecanismo, pero no crea adaptadores ni el
registro operativo futuro si su ruta pertenece a una fase posterior.

No crear adaptadores en esta fase.

## 3. Archivos autorizados

Lista cerrada de rutas literales, aplicable a la implementación futura
de esta tarea (no a esta operación de apertura, que solo redacta
`MANDATE.md` y `ACCEPTANCE.md`).

### Escritura de Sonnet

1. `AGENTS.md`
2. `governance/core/INSTITUTIONAL_CORE.md`
3. `governance/core/ADAPTER_REVIEW_POLICY.md`
4. `governance/projects/CLAUDEBOT_PROFILE.md`
5. `reports/AI-GOV-F1-CANONICAL/IMPLEMENTATION_REPORT.md`

### Escritura exclusiva de Codex

6. `reports/AI-GOV-F1-CANONICAL/AUDIT_CODEX.md`

Sonnet no puede escribir el informe de auditoría.
Codex no puede modificar los artefactos auditados.

### Lectura en CLAUDEBOT-CONTROL

7. `README.md`
8. `templates/TASK_TEMPLATE.md`
9. `templates/REPORT_TEMPLATE.md`
10. `templates/AUDIT_TEMPLATE.md`
11. `decisions/OWNER_DECISIONS.md`
12. `docs/plan_arquitectura_gobernanza_multi_ia_v1.md`
13. `docs/reauditoria_codex_plan_arquitectura_gobernanza_multi_ia_v1_r3.md`
14. `tasks/AI-GOV-F1-CANONICAL/MANDATE.md`
15. `tasks/AI-GOV-F1-CANONICAL/ACCEPTANCE.md`

### Lectura secundaria futura en CLAUDEBOT

16. `AGENTS.md`
17. `docs/estado_rector_post_f8.md`
18. `docs/campania_t1_btcusdt_1h.md`
19. `docs/borrador_arquitectura_documental_t2.md`

Estas cuatro rutas (16-19):

- son exclusivamente de lectura;
- solo pueden consultarse contra el SHA completo de `CLAUDEBOT`
  registrado en la autorización operacional posterior;
- la lectura debe realizarse de manera reproducible mediante:

  ```text
  git -C /home/miguel/proyectos/CLAUDEBOT \
    show <SHA-CLAUDEBOT>:<ruta-literal>
  ```

- no se autoriza leer esas rutas desde un working tree móvil;
- no se autoriza seguir enlaces ni abrir archivos adicionales;
- si una ruta no existe en el SHA autorizado, la implementación se
  detiene y se informa; no se sustituye por otra ruta;
- no se autoriza abrir datasets, CSV, resultados, código científico ni
  producción;
- toda referencia normativa debe contener repositorio, SHA completo y
  ruta literal.

## 4. Prohibiciones

Además de las de `AGENTS.md`:

- no modificar `CLAUDEBOT`;
- no crear `judgment/`, `adapters/` o `tests/`;
- no copiar el corpus Fable;
- no crear el manifiesto de Capa C, reservado para Fase 2;
- no crear `SONNET_FABLE_ADAPTER.md`, reservado para Fase 3;
- no crear benchmarks, reservado para Fase 4;
- no ejecutar validación conductual;
- no abrir datasets, CSV, resultados, discovery, OOS o producción;
- no modificar el estado científico de F-1A, F10, F11 o T2;
- no afirmar que Fable es un modelo concreto;
- no afirmar validación conductual inexistente;
- no modificar archivos fuera de la lista cerrada de §3;
- no hacer push, merge, rebase o tags;
- no borrar ramas o worktrees;
- no declarar documentos congelados antes de auditoría y decisión
  final de Miguel;
- no iniciar la implementación mientras no estén fijados el SHA exacto
  de implementación de `CLAUDEBOT-CONTROL` y el SHA exacto de lectura
  de `CLAUDEBOT`.

## 5. Criterios de aceptación

Ver `ACCEPTANCE.md` de esta misma carpeta para el detalle verificable
(A-01 a A-21). Resumen:

1. El diff de implementación modifica exclusivamente los archivos
   asignados a Sonnet en §3 (A-01).
2. `AGENTS.md` permanece como puerta de entrada e índice y conserva
   expresamente la autoridad exclusiva de Miguel, la taxonomía exacta
   `APROBAR`/`RECHAZAR`/`BLOQUEAR`, el aislamiento entre agentes, el
   bloqueo ante hallazgos críticos, la estructura obligatoria de
   mandatos, la estructura obligatoria de informes, el control de
   ramas y merges, y las prohibiciones de alcance sobre `CLAUDEBOT`,
   sin duplicar el contenido normativo detallado (A-02).
3. Capa A es agnóstica de proyecto, modelo y dominio científico, y
   cubre autoridad, precedencia, permisos, alcance, veredictos/estados
   y conflictos (A-03 a A-05).
4. El perfil de Capa B para `CLAUDEBOT` añade restricciones sin
   relajar Capa A, usa referencias con SHA completo y no reabre fases
   científicas (A-06 a A-09).
5. La política de revisión de adaptadores define campos, los cinco
   eventos de revisión obligatoria (incluido el plazo de 90 días), la
   ubicación exacta del registro, el procedimiento de creación y
   actualización de entradas, la conservación del historial, la
   separación entre propuesta/auditoría/decisión de Miguel, y los
   estados `VIGENTE`/`REVISIÓN REQUERIDA`/`HIPÓTESIS NO VALIDADA`,
   distinguiendo evidencia de hipótesis no validada (A-10 a A-12).
6. No se crean `judgment/`, `adapters/`, `tests/`, ni se copia Fable
   Judgment v1, ni se modifica `CLAUDEBOT` (A-13 a A-16).
7. El informe de implementación y la auditoría independiente de Codex
   cumplen su estructura obligatoria y su veredicto (A-17 a A-19).
8. Nada se declara congelado antes de `APROBAR` y decisión final de
   Miguel, y la Fase 1 solo cierra con todos los requisitos de A-21.

## 6. Autorización

- Este mandato no autoriza por sí mismo la implementación.
- Requiere revisión de ChatGPT y auditoría independiente de Codex
  sobre el commit exacto que contenga este mandato.
- La implementación exige autorización posterior y expresa de Miguel,
  registrada en `decisions/OWNER_DECISIONS.md`.
- La congelación de los documentos canónicos exige veredicto `APROBAR`
  vigente y decisión final de Miguel.
- Cualquier ampliación de alcance requiere una adenda o un mandato
  nuevo aprobado por Miguel.
- Este mandato no autoriza push ni merge a rama rectora.
