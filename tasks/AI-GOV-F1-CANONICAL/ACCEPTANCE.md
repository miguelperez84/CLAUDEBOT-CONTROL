# ACCEPTANCE.md — AI-GOV-F1-CANONICAL

Criterios de aceptación verificables para la implementación futura de
la Fase 1 (§17 del plan de arquitectura de gobernanza multi-IA v1).
Ninguno de estos criterios se da por cumplido por declaración; cada uno
exige la evidencia de la columna correspondiente en la matriz de §2.

## 1. Criterios A-01 a A-21

Estos criterios se agrupan en tres etapas verificables por separado:

- **Etapa 1 — auditoría del commit de implementación:** A-01 a A-17 y
  A-20. Codex los evalúa sobre el commit objetivo de implementación
  para emitir su veredicto.
- **Etapa 2 — control posterior del informe de auditoría ya
  versionado:** A-18 y A-19. Comprueban, después y sin efecto
  retroactivo, la integridad del blob de
  `<ruta-informe-auditoría-codex-autorizada>` una vez que Codex lo
  versiona; no condicionan el veredicto que ese mismo informe ya
  emitió sobre la Etapa 1. Su resultado (`CONFORME`/`NO CONFORME`)
  integra la definición de `APROBAR` vigente (§1, antes de A-21).
- **Etapa 3 — cierre posterior:** A-21. Se evalúa en una operación
  separada, después de existir `APROBAR` vigente (Etapa 1 más
  Etapa 2).

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

A-07. Una **referencia normativa documental** a `CLAUDEBOT` es un
puntero usado como fundamento de una regla del perfil: contiene
repositorio, SHA completo de 40 caracteres, ruta literal y función
normativa, presentado en una tabla o registro con esos campos
separados.

Las referencias normativas documentales a los cuatro documentos fuente
de `CLAUDEBOT` deben centralizarse en
`governance/projects/CLAUDEBOT_PROFILE.md`. Las referencias normativas
de esta Fase 1 solo pueden corresponder a estas rutas literales:

- `AGENTS.md`
- `docs/estado_rector_post_f8.md`
- `docs/campania_t1_btcusdt_1h.md`
- `docs/borrador_arquitectura_documental_t2.md`

No se clasifica como referencia normativa documental:

- los SHA operacionales o evidenciales registrados en
  `reports/AI-GOV-F1-CANONICAL/IMPLEMENTATION_REPORT.md`;
- los comandos `git show` y las huellas de estado;
- los identificadores de commits de implementación o de auditoría;
- las menciones institucionales de alcance y prohibición en
  `AGENTS.md`.

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

Se define `<ruta-informe-auditoría-codex-autorizada>` como la ruta
literal fijada por la autorización operacional de la auditoría o
reauditoría cuyo veredicto se pretende usar (p. ej.
`reports/AI-GOV-F1-CANONICAL/AUDIT_CODEX.md` o una ruta versionada
equivalente que una autorización posterior fije expresamente).

A-18 y A-19 pertenecen a la Etapa 2 (control posterior), no a la
Etapa 1 (auditoría de implementación): el informe de auditoría, en
`<ruta-informe-auditoría-codex-autorizada>`, no pertenece al commit
objetivo de implementación — A-01 lo excluye expresamente de las cinco
rutas de la implementación. Codex emite su veredicto sobre A-01 a
A-17 y A-20 sin que A-18 ni A-19 condicionen ese veredicto. Una vez
que Codex versiona su propio commit de auditoría, A-18 y A-19 se
anclan a ese commit exacto (`<commit-auditoría-codex>` en la matriz de
§2) para comprobar, después, la integridad del blob ya versionado —
sin efecto retroactivo sobre el veredicto que ese mismo informe ya
emitió. A-18 y A-19 no cambian el texto ni el hecho histórico de ese
veredicto.

**`APROBAR` vigente** es el veredicto `APROBAR` de Codex sobre A-01 a
A-17 y A-20, sumado a que A-18 y A-19 hayan resultado `CONFORME` sobre
el blob versionado de su propio informe; sin ambos elementos a la vez,
el veredicto no es `APROBAR` vigente. Hasta que A-18 y A-19 resulten
`CONFORME`, ese veredicto no puede tratarse como `APROBAR` vigente. Si
A-18 o A-19 resulta `NO CONFORME`, corresponde `BLOQUEAR` la
integración, el push, la congelación y el cierre. El commit de
`decisions/OWNER_DECISIONS.md` que autorice la congelación y la
integración debe citar: el commit exacto de la auditoría; la ruta
literal exacta de su informe
(`<ruta-informe-auditoría-codex-autorizada>`); y la confirmación
durable de que A-18 y A-19 resultaron `CONFORME`.

A-18. Codex audita el commit objetivo exacto y usa solo
`APROBAR`, `RECHAZAR` o `BLOQUEAR`.

A-19. Todo hallazgo crítico produce `BLOQUEAR`.

A-20. Nada se declara congelado antes de `APROBAR` y decisión final.

A-01 a A-17 y A-20 (Etapa 1) son los criterios de aceptación del
**commit de implementación** de la Fase 1: la auditoría independiente
de Codex sobre ese commit los evalúa y, si corresponde, emite
`APROBAR` sobre ellos exclusivamente, sin que A-18 ni A-19 condicionen
ese veredicto. A-18 y A-19 (Etapa 2) comprueban, después y sin efecto
retroactivo, la integridad del propio informe de auditoría una vez
versionado. El criterio A-21 (Etapa 3) no forma parte de ninguna de
las dos etapas anteriores: es el criterio de **cierre de la Fase 1**,
evaluado en una operación posterior y separada, con su propio mandato
o autorización y su propia evidencia, una vez que exista `APROBAR`
vigente sobre el commit de implementación. Ningún elemento de A-18,
A-19 o A-21 puede exigirse como condición para que la auditoría de
implementación emita su veredicto sobre A-01 a A-17 y A-20.

A-21. *(Criterio de cierre de Fase 1, Etapa 3, evaluado en una
operación posterior y separada a la auditoría de implementación de
A-01 a A-17 y A-20, y al control posterior de A-18 y A-19).* Fase 1
cierra mediante exactamente una de estas dos vías, cada una definida
por el plan de arquitectura de gobernanza multi-IA v1 (§8.6 y §9.1),
y toda su evidencia debe citar commits exactos por SHA completo —
ninguna referencia móvil ("la entrada final", "el último commit")
constituye evidencia suficiente por sí sola:

**Vía normal (integración, §8.6): siete pasos — seis commits exactos
(pasos 1, 2, 3, 4, 6 y 7) y una acción de push (paso 5, que no crea
por sí misma un commit nuevo):**

1. commit exacto de implementación;
2. commit exacto del informe de auditoría, cuyo veredicto es
   `APROBAR` vigente (`APROBAR` de Codex sobre A-01 a A-17 y A-20, más
   A-18 y A-19 en `CONFORME`) sobre ese commit de implementación;
3. commit exacto de `decisions/OWNER_DECISIONS.md` con la decisión de
   Miguel de congelación y autorización expresa de integración, que
   cite el commit de auditoría, la ruta exacta de su informe y la
   confirmación de que A-18 y A-19 resultaron `CONFORME`;
4. commit exacto de integración en `main`, verificado mediante dos
   comprobaciones de ancestría, ambas con código de salida `0`:

   - `git merge-base --is-ancestor <commit-de-implementación> <commit-de-integración>`,
     que prueba que el commit de implementación del paso 1 está
     contenido en el commit de integración — sin esta comprobación,
     un commit cualquiera ya presente en `main` podría presentarse
     como commit de integración aunque el commit de implementación
     nunca hubiese sido integrado;
   - `git merge-base --is-ancestor <commit-de-integración> main`, que
     prueba que el commit de integración está contenido en `main`.

   La cadena que debe quedar probada es:
   `<commit-de-implementación>` → `<commit-de-integración>` →
   `main` local → `origin/main`. En una integración fast-forward, el
   commit de implementación y el commit de integración pueden ser el
   mismo, y la primera comprobación se satisface trivialmente;
5. push efectivo a `origin/main`: una acción, no un commit — el push
   publica en el remoto el mismo commit de integración del paso 4; no
   se le llama "commit del push";
6. un checkpoint ejecutado inmediatamente después del push efectivo
   del paso 5 y antes de crear el commit de evidencia de este mismo
   paso, que comprueba exactamente:

   - SHA local observado de `main` = `<commit-de-integración>`;
   - SHA remoto observado de `refs/heads/main`, obtenido mediante
     `git ls-remote origin refs/heads/main`, = `<commit-de-integración>`;
   - por tanto: SHA local observado = SHA remoto observado.

   El commit exacto posterior de `decisions/OWNER_DECISIONS.md` que
   registra este checkpoint declara durablemente: el commit de
   integración; el SHA local observado; el SHA remoto observado; la
   igualdad de ambos con el commit de integración; la fecha; el
   comando ejecutado; el resultado del push; y el código de salida
   exitoso. Este commit registra la observación posterior al push,
   pero no es "el commit del push". La salida de `git ls-remote` es
   evidencia viva y auxiliar; la evidencia durable es esta entrada de
   `OWNER_DECISIONS.md`;
7. commit exacto posterior con la decisión de cierre.

**Vía excepcional (cierre sin integración, siguiendo literalmente
§9.1 del plan):**

1. decisión expresa y durable de Miguel de cerrar la tarea sin
   fusionar el cambio a rama rectora;
2. el motivo de esa decisión;
3. identificación exacta de `<commit-cerrado-sin-integrar>`: el commit
   o artefacto que se cierra sin integrar;
4. evidencia negativa reproducible, registrada en un commit exacto de
   `decisions/OWNER_DECISIONS.md`, de que `<commit-cerrado-sin-integrar>`
   no fue integrado a `main` y no fue empujado a `origin/main`:

   - comprobación local:
     `git merge-base --is-ancestor <commit-cerrado-sin-integrar> main`,
     con resultado esperado de código de salida `1` (el commit no es
     ancestro de `main`);
   - para comprobar `origin/main`, la futura operación de cierre debe
     autorizar expresamente, sin ejecutarlos ahora:

     ```text
     git ls-remote origin refs/heads/main
     git fetch --no-tags origin <sha-remoto-main>
     git merge-base --is-ancestor <commit-cerrado-sin-integrar> FETCH_HEAD
     ```

     con resultado esperado de código de salida `1` en el último
     comando; `git fetch` en esta comprobación no integra ni modifica
     archivos del working tree;
   - la entrada durable de cierre excepcional registra los comandos
     ejecutados, el SHA remoto obtenido y los códigos de salida;
   - si cualquiera de los dos controles devuelve código de salida `0`,
     no existe cierre sin integración válido;
5. cerrar sin integración nunca equivale a integrar ni a congelar
   como rector, y nunca se interpreta como una excepción a la puerta
   de integración de §8.6: cerrar sin integrar no es integrar.

## 2. Matriz de verificación

Salvo que una fila indique explícitamente lo contrario, toda lectura o
búsqueda de esta matriz se ancla al commit objetivo de implementación
mediante `git show <commit-objetivo-implementación>:<ruta>`; ninguna
lectura ni búsqueda se realiza contra un working tree que no sea
exactamente ese commit. Un diff entre dos commits (p. ej.
`git diff <commit-base-implementación> <commit-objetivo-implementación>`)
también satisface este anclaje, porque ambos extremos son commits, no
un working tree móvil.

| Criterio | Archivo o evidencia | Comando verificable | Resultado esperado |
|---|---|---|---|
| A-01 | Diff completo entre el commit base de implementación y el commit objetivo de implementación | `git diff --name-status <commit-base-implementación> <commit-objetivo-implementación>` | Aparecen exactamente estas cinco rutas y ninguna otra: `AGENTS.md`, `governance/core/INSTITUTIONAL_CORE.md`, `governance/core/ADAPTER_REVIEW_POLICY.md`, `governance/projects/CLAUDEBOT_PROFILE.md`, `reports/AI-GOV-F1-CANONICAL/IMPLEMENTATION_REPORT.md`. No se usa `git diff-tree`, porque solo comprobaría un commit individual y podría omitir cambios anteriores de la misma implementación |
| A-02 | `AGENTS.md` en el commit objetivo | `git diff <commit-base-implementación> <commit-objetivo-implementación> -- AGENTS.md` para el diff, más `git show <commit-objetivo-implementación>:AGENTS.md` para leer el archivo final completo | El texto final de `AGENTS.md`, leído en su totalidad desde el commit objetivo, conserva de forma verificable los ocho elementos: autoridad exclusiva de Miguel, taxonomía `APROBAR`/`RECHAZAR`/`BLOQUEAR`, aislamiento entre agentes, bloqueo ante hallazgos críticos, estructura obligatoria de mandatos, estructura obligatoria de informes, control de ramas y merges, y prohibiciones de alcance sobre `CLAUDEBOT`. Los cambios de `AGENTS.md` se limitan a conservar las ocho reglas críticas, establecer o reforzar su función de puerta de entrada e índice y enlazar las tres rutas canónicas (`governance/core/INSTITUTIONAL_CORE.md`, `governance/core/ADAPTER_REVIEW_POLICY.md`, `governance/projects/CLAUDEBOT_PROFILE.md`); no duplica íntegramente el contenido normativo detallado. No se exige que el diff sea únicamente aditivo |
| A-03 | `governance/core/INSTITUTIONAL_CORE.md` en el commit objetivo | `git grep -in -e dataset -e discovery -e OOS -e trading -e quintil -e BTCUSDT <commit-objetivo-implementación> -- governance/core/INSTITUTIONAL_CORE.md` | Sin coincidencias |
| A-04 | `governance/core/INSTITUTIONAL_CORE.md` en el commit objetivo | `git grep -n -e '^##' <commit-objetivo-implementación> -- governance/core/INSTITUTIONAL_CORE.md`, más lectura manual completa mediante `git show <commit-objetivo-implementación>:governance/core/INSTITUTIONAL_CORE.md` | Existen secciones para autoridad, precedencia, permisos, alcance, veredictos/estados y conflictos |
| A-05 | `governance/core/INSTITUTIONAL_CORE.md` en el commit objetivo | `git show <commit-objetivo-implementación>:governance/core/INSTITUTIONAL_CORE.md`, seguido de lectura manual completa de esa salida | Ningún vocabulario de dominio científico presentado como regla universal |
| A-06 | `governance/projects/CLAUDEBOT_PROFILE.md` e `governance/core/INSTITUTIONAL_CORE.md` en el commit objetivo | `git show <commit-objetivo-implementación>:governance/projects/CLAUDEBOT_PROFILE.md` y `git show <commit-objetivo-implementación>:governance/core/INSTITUTIONAL_CORE.md`, leídos y comparados manualmente | El perfil solo añade restricciones; ninguna cláusula relaja una regla de Capa A |
| A-07 | Los cinco artefactos de implementación, todos en el commit objetivo | `git grep -nE -e 'CLAUDEBOT' -e '[0-9a-f]{40}' <commit-objetivo-implementación> -- AGENTS.md governance/core/INSTITUTIONAL_CORE.md governance/core/ADAPTER_REVIEW_POLICY.md governance/projects/CLAUDEBOT_PROFILE.md reports/AI-GOV-F1-CANONICAL/IMPLEMENTATION_REPORT.md`, más lectura manual de cada coincidencia | Toda coincidencia se revisa manualmente. En `governance/projects/CLAUDEBOT_PROFILE.md`, cada referencia normativa documental tiene, simultáneamente: repositorio identificado como CLAUDEBOT; el mismo SHA completo autorizado por Miguel; una de las cuatro rutas literales (`AGENTS.md`, `docs/estado_rector_post_f8.md`, `docs/campania_t1_btcusdt_1h.md`, `docs/borrador_arquitectura_documental_t2.md`); función o motivo de la referencia; ninguna se sustenta únicamente en `main`, nombre de rama, tag móvil o hash abreviado. `governance/core/INSTITUTIONAL_CORE.md` y `governance/core/ADAPTER_REVIEW_POLICY.md` no incorporan reglas específicas tomadas de CLAUDEBOT. `AGENTS.md` solo conserva menciones institucionales de alcance, prohibición o índice ya autorizadas. `reports/AI-GOV-F1-CANONICAL/IMPLEMENTATION_REPORT.md` puede contener SHA, comandos y referencias operacionales o evidenciales sin restricción de cantidad, pero no puede introducir una nueva regla normativa tomada de CLAUDEBOT. No se exige cero coincidencias de hash en `IMPLEMENTATION_REPORT.md` |
| A-08 | `governance/projects/CLAUDEBOT_PROFILE.md` en el commit objetivo | `git show <commit-objetivo-implementación>:governance/projects/CLAUDEBOT_PROFILE.md`, lectura manual completa | No se transcriben reglas científicas, datos ni código; solo referencias por puntero |
| A-09 | `governance/projects/CLAUDEBOT_PROFILE.md` en el commit objetivo | `git grep -in -e 'F-1A' -e F10 -e F11 -e T2 <commit-objetivo-implementación> -- governance/projects/CLAUDEBOT_PROFILE.md` | Toda coincidencia se revisa manualmente y es descriptiva del estado existente (referenciado, no abierto ni continuado; no autoriza ni continúa una fase) |
| A-10 | `governance/core/ADAPTER_REVIEW_POLICY.md` en el commit objetivo | `git show <commit-objetivo-implementación>:governance/core/ADAPTER_REVIEW_POLICY.md`, lectura completa como comprobación principal; búsqueda de apoyo con `git grep -in -e modelo -e versión -e fecha -e evento -e evidencia -e estado -e responsable -e auditor -e decisión -e '90 días' <commit-objetivo-implementación> -- governance/core/ADAPTER_REVIEW_POLICY.md` | Todos los campos, los cinco eventos, la regla de 90 días, la ubicación exacta del registro, el procedimiento de creación/actualización, la conservación del historial, la separación propuesta/auditoría/decisión y los tres estados están definidos normativamente; no quedan frases como "ubicación por definir", "mecanismo pendiente" o equivalentes |
| A-11 | `governance/core/ADAPTER_REVIEW_POLICY.md` en el commit objetivo | `git grep -nF -e 'HIPÓTESIS NO VALIDADA' <commit-objetivo-implementación> -- governance/core/ADAPTER_REVIEW_POLICY.md`, como apoyo; la separación semántica se verifica mediante lectura manual | El estado existe; la coincidencia textual es solo apoyo y la lectura manual confirma que está definido en sección separada de la evidencia observada |
| A-12 | `governance/core/ADAPTER_REVIEW_POLICY.md` en el commit objetivo | `git show <commit-objetivo-implementación>:governance/core/ADAPTER_REVIEW_POLICY.md`, lectura manual completa | Ninguna cláusula concede permiso o autonomía basándose solo en una hipótesis no validada |
| A-13 | Diff del commit objetivo de implementación contra el commit base de implementación | `git diff --name-only <commit-base-implementación> <commit-objetivo-implementación> -- judgment adapters tests` | Sin salida; la comprobación cubre creación, modificación o eliminación de rutas exactamente bajo `judgment/`, `adapters/` o `tests/`, sin usar tubería dentro de la tabla, y se limita a lo creado o modificado por la implementación, no al árbol histórico completo |
| A-14 | Diff completo de los cinco archivos de implementación | `git diff <commit-base-implementación> <commit-objetivo-implementación> -- AGENTS.md governance/core/INSTITUTIONAL_CORE.md governance/core/ADAPTER_REVIEW_POLICY.md governance/projects/CLAUDEBOT_PROFILE.md reports/AI-GOV-F1-CANONICAL/IMPLEMENTATION_REPORT.md` más lectura manual completa | No aparece contenido copiado del corpus; no se reproducen constitución, modelos de decisión, patrones de falla, adaptadores o ADR del corpus; cualquier mención a Fable es terminológica o mediante referencia; no se afirma validación conductual |
| A-15 | Preflight y cierre del informe de implementación, en el commit objetivo | Huella de estado de `CLAUDEBOT` definida en `MANDATE.md` §3 (SHA completo de `HEAD` + SHA-256 de `status --porcelain=v1 -z`), capturada antes y después de la lectura autorizada; como apoyo, `git grep -n -e 'git -C /home/miguel/proyectos/CLAUDEBOT' <commit-objetivo-implementación> -- reports/AI-GOV-F1-CANONICAL/IMPLEMENTATION_REPORT.md`; la lectura principal continúa siendo `git show <commit-objetivo-implementación>:reports/AI-GOV-F1-CANONICAL/IMPLEMENTATION_REPORT.md`, más lectura manual obligatoria del informe (los comandos pueden estar divididos en varias líneas) | El informe registra la huella de estado inicial y la huella de estado final de CLAUDEBOT, cada una compuesta por el SHA completo de `HEAD` y el SHA-256 del estado; ambas huellas son idénticas; el informe registra que ambos comandos de la huella se ejecutaron con éxito (código de salida verificado) en ambas capturas; el informe no expone la salida textual de `status` ni nombres de archivo o rutas provenientes de ella; no se crean cambios nuevos ni commits en CLAUDEBOT; cualquier cambio previo ajeno queda representado únicamente por su SHA-256 y permanece intacto; la igualdad de la huella se registra como evidencia del estado Git observable en ambos extremos, no como demostración absoluta de ausencia de modificación (no cubre archivos ignorados ni cambios transitorios restaurados); toda lectura de archivos (no de metadatos) se realiza mediante `git show` contra el SHA autorizado; el listado de archivos abiertos en el informe contiene únicamente estas cuatro rutas de CLAUDEBOT: `AGENTS.md`, `docs/estado_rector_post_f8.md`, `docs/campania_t1_btcusdt_1h.md`, `docs/borrador_arquitectura_documental_t2.md`; no aparece ninguna otra ruta de CLAUDEBOT en los comandos de lectura |
| A-16 | Informe de implementación §3 (comandos ejecutados) | Lectura manual del informe | Sin comandos sobre datasets, CSV, discovery, OOS, producción ni scripts de validación conductual |
| A-17 | `reports/AI-GOV-F1-CANONICAL/IMPLEMENTATION_REPORT.md` | Lectura contra `templates/REPORT_TEMPLATE.md` §3-§6 | Contiene las cuatro secciones exigidas con datos reales, no descriptivos; registra también los dos SHA fijados por Miguel (commit base de implementación en CLAUDEBOT-CONTROL y SHA de lectura de CLAUDEBOT); registra preflight y cierre de CLAUDEBOT mediante la huella de estado definida en `MANDATE.md` §3 (SHA completo de `HEAD` + SHA-256 de `status --porcelain=v1 -z`), capturada antes y después, sin exponer la salida textual de `status` ni rutas provenientes de ella; registra las cuatro rutas exactas leídas mediante `git show`; incluye declaración negativa de que no abrió rutas adicionales |
| A-18 *(Etapa 2, anclado a `<commit-auditoría-codex>`, no al commit objetivo de implementación; `CONFORME`/`NO CONFORME` requerido para `APROBAR` vigente)* | `<ruta-informe-auditoría-codex-autorizada>` | `git grep -n -e 'commit auditado' -e APROBAR -e RECHAZAR -e BLOQUEAR <commit-auditoría-codex> -- <ruta-informe-auditoría-codex-autorizada>` como apoyo, más lectura manual obligatoria mediante `git show <commit-auditoría-codex>:<ruta-informe-auditoría-codex-autorizada>` de la sección final de veredicto | El informe cita el SHA completo del commit objetivo de implementación; contiene una sección final de veredicto; esa sección contiene exactamente uno de: `APROBAR`, `RECHAZAR` o `BLOQUEAR`; no utiliza estados intermedios. Si NO CONFORME, `BLOQUEAR` integración, push, congelación y cierre |
| A-19 *(Etapa 2, anclado a `<commit-auditoría-codex>`, no al commit objetivo de implementación; `CONFORME`/`NO CONFORME` requerido para `APROBAR` vigente)* | `<ruta-informe-auditoría-codex-autorizada>` §5 (hallazgos) | `git show <commit-auditoría-codex>:<ruta-informe-auditoría-codex-autorizada>`, mismo blob exacto que A-18, lectura manual de la tabla de hallazgos | Si existe severidad "crítico", el veredicto de §7 es `BLOQUEAR`. Si NO CONFORME, `BLOQUEAR` integración, push, congelación y cierre |
| A-20 | Los tres documentos canónicos autorizados (`governance/core/INSTITUTIONAL_CORE.md`, `governance/core/ADAPTER_REVIEW_POLICY.md`, `governance/projects/CLAUDEBOT_PROFILE.md`) y `decisions/OWNER_DECISIONS.md`, todos en el commit objetivo | `git show <commit-objetivo-implementación>:governance/core/INSTITUTIONAL_CORE.md`; `git show <commit-objetivo-implementación>:governance/core/ADAPTER_REVIEW_POLICY.md`; `git show <commit-objetivo-implementación>:governance/projects/CLAUDEBOT_PROFILE.md`; `git show <commit-objetivo-implementación>:decisions/OWNER_DECISIONS.md`; y `git diff --name-status <commit-base-implementación> <commit-objetivo-implementación>` para confirmar que no se creó ningún otro documento bajo `governance/` | Los tres documentos canónicos siguen como `BORRADOR`, `NO CONGELADO` o equivalente inequívoco; no existe en el commit objetivo, dentro de `OWNER_DECISIONS.md`, una decisión afirmativa de congelación o cierre de esta implementación; el diff base-objetivo no contiene ninguna ruta bajo `governance/` distinta de esas tres; una decisión de cierre es materia de A-21, evaluada en una operación posterior y separada |
| A-21 *(Etapa 3, evaluada en operación posterior separada; no forma parte de las Etapas 1 y 2)* | `decisions/OWNER_DECISIONS.md`, entradas de cierre citadas cada una por su commit exacto (nunca "la entrada final" ni "el último commit") | Vía normal, paso 1: `git show --check --stat --oneline <commit-de-implementación>` y `git diff --name-status <commit-base-de-implementación> <commit-de-implementación>`. Paso 2: `git show <commit-de-auditoría>:<ruta-informe-auditoría-codex-autorizada>`. Pasos 3, 6 y 7: `git show <commit-de-decisión>:decisions/OWNER_DECISIONS.md` (un commit de decisión distinto para cada paso). Paso 4: `git merge-base --is-ancestor <commit-de-implementación> <commit-de-integración>` (código de salida `0`) para probar que el commit de implementación está contenido en el commit de integración, más `git merge-base --is-ancestor <commit-de-integración> main` (código de salida `0`) para probar que el commit de integración está contenido en `main`. Paso 5: sin comando propio, es la acción de push; se verifica indirectamente por el checkpoint del paso 6. Paso 6: `git ls-remote origin refs/heads/main` como verificación viva auxiliar, más `git show <commit-de-decisión>:decisions/OWNER_DECISIONS.md` para leer el registro durable de esa observación. Vía excepcional: `git merge-base --is-ancestor <commit-cerrado-sin-integrar> main` (código de salida `1` esperado) y, cuando la operación de cierre lo autorice expresamente, `git ls-remote origin refs/heads/main`, `git fetch --no-tags origin <sha-remoto-main>` y `git merge-base --is-ancestor <commit-cerrado-sin-integrar> FETCH_HEAD` (código de salida `1` esperado); más `git show <commit-de-decisión>:decisions/OWNER_DECISIONS.md` para leer la decisión expresa de cierre sin integración | Vía normal: existen, cada uno citado por SHA completo, los seis commits de los pasos 1, 2, 3, 4, 6 y 7, y la acción de push efectivo del paso 5 (que no es un commit); el paso 4 exige código de salida `0` en ambas comprobaciones de ancestría (implementación→integración e integración→`main`), probando la cadena completa `<commit-de-implementación>` → `<commit-de-integración>` → `main` local → `origin/main`; el commit del paso 6 registra el commit de integración, el SHA local observado de `main`, el SHA remoto observado de `refs/heads/main`, la igualdad exacta entre ambos y el commit de integración, la fecha, el comando ejecutado, el resultado del push y el código de salida exitoso. Vía excepcional: existe un commit con la decisión expresa y durable de Miguel, su motivo, la identificación exacta de `<commit-cerrado-sin-integrar>`, y la evidencia negativa reproducible (ambos controles de ancestría con código de salida `1`) de que no hubo integración ni push. En ambos casos, ninguna referencia móvil sustituye la cita del commit exacto, y todo `git show` de esta fila especifica su ruta completa, sin dejar ningún segmento pendiente |

No se han inventado hashes futuros: ninguna celda de la matriz cita un
commit que no exista todavía; los comandos se ejecutan sobre los
commits reales una vez creados durante la implementación autorizada.
