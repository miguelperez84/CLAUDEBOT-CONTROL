# CLAUDEBOT_PROFILE.md — Perfil de Capa B para CLAUDEBOT

**Estado: BORRADOR — NO CONGELADO.**

## 1. Función de este documento

Este es el primer perfil de Capa B para el proyecto `CLAUDEBOT`. Añade
restricciones específicas de ese proyecto sobre
`governance/core/INSTITUTIONAL_CORE.md` (Capa A); no relaja, sustituye
ni crea excepción a ninguna de sus reglas. Ante cualquier conflicto
aparente entre este perfil y `governance/core/INSTITUTIONAL_CORE.md`,
prevalece la lectura más restrictiva, conforme a
`governance/core/INSTITUTIONAL_CORE.md` §4.

Este documento centraliza exclusivamente aquí toda referencia
normativa documental a `CLAUDEBOT`. Una **referencia normativa
documental** es un puntero usado como fundamento de una regla de este
perfil, que contiene simultáneamente: repositorio, SHA completo de 40
caracteres, ruta literal y función normativa. No se clasifican como
referencia normativa documental —y por tanto no están sujetos a esta
centralización ni a esta restricción de rutas— los SHA operacionales o
evidenciales registrados en
`reports/AI-GOV-F1-CANONICAL/IMPLEMENTATION_REPORT.md`, los comandos
`git show` y las huellas de estado, los identificadores de commits de
implementación o de auditoría, ni las menciones institucionales de
alcance y prohibición en `AGENTS.md`.

## 2. Referencias normativas documentales

Las cuatro referencias siguientes son las únicas referencias
normativas documentales a `CLAUDEBOT` autorizadas en esta Fase 1.
Todas usan el mismo commit inmutable, fijado por decisión durable del
propietario:

| Repositorio | SHA completo | Ruta literal | Función normativa |
|---|---|---|---|
| CLAUDEBOT | `3af01c5e96240bba9f7cf95904844efb15fca6a0` | `AGENTS.md` | Funda las reglas locales propias de operación de `CLAUDEBOT` y su régimen fail-closed; este perfil no las sustituye ni las relaja. |
| CLAUDEBOT | `3af01c5e96240bba9f7cf95904844efb15fca6a0` | `docs/estado_rector_post_f8.md` | Funda la obligación de respetar el estado rector vigente de `CLAUDEBOT` y de no ejecutar ninguna fase pendiente sin mandato propio y autorización propia de su propietario. |
| CLAUDEBOT | `3af01c5e96240bba9f7cf95904844efb15fca6a0` | `docs/campania_t1_btcusdt_1h.md` | Funda el respeto de la carta de campaña congelada de `CLAUDEBOT`, sin modificarla ni actuar sobre su contenido. |
| CLAUDEBOT | `3af01c5e96240bba9f7cf95904844efb15fca6a0` | `docs/borrador_arquitectura_documental_t2.md` | Funda que esa arquitectura documental es un borrador no rector y no congelado, y que no autoriza ejecutar T2. |

No existe ninguna quinta referencia normativa documental a
`CLAUDEBOT` en esta Fase 1. Cualquier otra mención a `CLAUDEBOT` en
los cinco artefactos de esta implementación es operacional o
evidencial (SHA de huella, comandos `git show`, identificadores de
commit) y no funda ninguna regla adicional de este perfil.

## 3. Restricciones adicionales sobre la Capa A

Este perfil añade, sin relajar
`governance/core/INSTITUTIONAL_CORE.md`, las siguientes restricciones
específicas de `CLAUDEBOT`:

1. **No modificar `CLAUDEBOT`.** Ningún agente que opere bajo un
   mandato de `CLAUDEBOT-CONTROL` escribe, edita ni borra ningún
   archivo de `CLAUDEBOT`. Toda lectura de `CLAUDEBOT` autorizada por
   un mandato de esta Fase 1 se realiza exclusivamente mediante
   `git show <SHA>:<ruta>` contra el SHA fijado en §2, nunca contra
   una copia de trabajo móvil.
2. **No abrir ni continuar campañas o fases de investigación de
   `CLAUDEBOT`.** Ningún agente de esta Fase 1 abre, continúa, acelera
   ni ejecuta ninguna de las subfases documentales de cierre o de
   planificación identificadas como pendientes en
   `docs/estado_rector_post_f8.md` o en
   `docs/borrador_arquitectura_documental_t2.md`; esas subfases exigen
   mandato propio y autorización propia del propietario de
   `CLAUDEBOT`. **Durante esta Fase 1 queda prohibido abrir, continuar,
   ejecutar, acelerar o autorizar F-1A, F10, F11 o T2.** Esta
   prohibición es literal e independiente de la prohibición general de
   campañas y fases del párrafo anterior; ninguna de las dos sustituye
   a la otra.
3. **No abrir datos ni resultados.** Ningún agente de esta Fase 1 abre
   archivos de datos, resultados de corridas, código de investigación
   ni artefactos de producción de `CLAUDEBOT`.
4. **No ejecutar verificación de comportamiento.** Ningún agente de
   esta Fase 1 ejecuta, simula ni certifica el comportamiento del
   sistema de juicio de `CLAUDEBOT` ni de ningún otro corpus de
   criterio operativo de ese proyecto.
5. **No copiar el corpus de juicio de `CLAUDEBOT`.** El sistema de
   juicio documental de `CLAUDEBOT` se identifica literalmente como
   **Fable Judgment v1, sistema documental de juicio independiente del
   proveedor**. Durante esta Fase 1: ningún agente reproduce,
   transcribe ni incorpora su contenido sustantivo en ningún artefacto
   de `CLAUDEBOT-CONTROL`; no se ejecuta validación ni benchmark
   conductual alguno sobre Fable Judgment v1; Fable Judgment v1 no se
   declara aquí conductualmente validado, y este perfil no le atribuye
   tal validación; cualquier benchmark conductual de Fable Judgment v1
   continúa pendiente y queda fuera del alcance de esta Fase 1.
6. **Toda propuesta de adaptación derivada de la observación de
   `CLAUDEBOT` es `HIPÓTESIS NO VALIDADA`** en los términos de
   `governance/core/ADAPTER_REVIEW_POLICY.md` §6, hasta completar su
   propio ciclo de propuesta, auditoría independiente y decisión
   expresa del propietario. Ninguna hipótesis de este tipo concede
   autonomía ni permisos adicionales por sí sola.
7. **No se crean `judgment/`, `adapters/` ni `tests/`** como
   consecuencia de este perfil ni de ninguna referencia de §2; su
   creación, si algún día se autoriza, exige un mandato propio y
   separado.

## 4. Estado operativo de `CLAUDEBOT` para esta operación

El contenido de `CLAUDEBOT` usado como referencia por esta Fase 1
queda anclado, para toda esta operación, al commit inmutable
`3af01c5e96240bba9f7cf95904844efb15fca6a0`. Este anclaje es una medida
de control de esta implementación —garantiza que ninguna lectura de
esta Fase 1 se realice contra un estado distinto del verificado— y no
es una declaración editorial de que `CLAUDEBOT` como proyecto esté
congelado en un sentido distinto al que ya declaran sus propios
documentos rectores citados en §2. Este perfil no modifica, no
reinterpreta y no amplía ninguna prohibición o autorización vigente
dentro de `CLAUDEBOT`; esas reglas siguen gobernadas exclusivamente
por los documentos propios de `CLAUDEBOT`.

## 5. Autoridad y auditoría

- La autoridad final sobre este perfil, sobre cualquier cambio futuro
  a él y sobre cualquier acción derivada de sus referencias es
  exclusivamente Miguel, en su rol de propietario y autoridad final,
  conforme a `governance/core/INSTITUTIONAL_CORE.md` §2 y §2.1.
- Toda modificación futura de este perfil, y en particular cualquier
  ampliación de sus referencias normativas documentales, exige
  auditoría independiente de un agente auditor distinto del que la
  redacte, con veredicto `APROBAR`, `RECHAZAR` o `BLOQUEAR`, antes de
  cualquier decisión de Miguel sobre esa modificación.

## 6. Rutas y artefactos propios del proyecto

1. Los mandatos de tareas de `CLAUDEBOT` coordinadas desde
   `CLAUDEBOT-CONTROL` viven bajo:

   ```text
   tasks/<ID>/MANDATE.md
   ```

2. Sus criterios verificables, cuando correspondan, viven bajo:

   ```text
   tasks/<ID>/ACCEPTANCE.md
   ```

3. Los informes de implementación y auditoría viven bajo:

   ```text
   reports/<ID>/
   ```

   Cada mandato debe identificar las rutas literales concretas que
   pueden crearse o modificarse.

4. Los documentos congelados o rectores propios de `CLAUDEBOT`
   permanecen en su repositorio de origen y en sus rutas nativas. Este
   perfil no los mueve, copia ni presume congelados o rectores.

5. Un documento de `CLAUDEBOT` solo cumple una función normativa para
   una tarea de este marco cuando aparece en la tabla de §2 con:

   - repositorio;
   - SHA completo;
   - ruta literal;
   - función normativa.

6. Las convenciones genéricas `tasks/<ID>/...` y `reports/<ID>/...` son
   declaraciones de ubicación institucional dentro de
   `CLAUDEBOT-CONTROL`. No constituyen referencias normativas
   documentales adicionales a `CLAUDEBOT`.

---

*Este perfil es un borrador de la primera Capa B del marco de
gobernanza multi-IA para `CLAUDEBOT`. Permanece en estado BORRADOR —
NO CONGELADO. Su congelación exige auditoría independiente con
veredicto `APROBAR` vigente y decisión final y expresa del propietario
del proyecto, posterior y separada de esta implementación.*
