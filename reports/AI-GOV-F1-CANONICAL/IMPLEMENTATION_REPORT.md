# IMPLEMENTATION_REPORT.md — Implementación documental de la Fase 1

## 1. Identificación

- **Tarea:** `AI-GOV-F1-CANONICAL`.
- **Agente implementador:** Sonnet.
- **Repositorio y worktree:**
  `/home/miguel/proyectos/CLAUDEBOT-CONTROL-SONNET-AI-GOV-F1-IMPLEMENTATION`.
- **Rama:** `control/sonnet-ai-gov-f1-implementation`.
- **Commit base exacto de implementación (fijado por Miguel):**
  `00649d65760255f1e186f82a997de915afa41b73`.
- **Mandato aprobado (`MANDATE.md` y `ACCEPTANCE.md`):**
  `aa965803f103bfd3923ddd8fdbd04dd87253367a`.
- **Auditoría independiente R4 con veredicto `APROBAR`
  (`reports/AI-GOV-F1-CANONICAL/MANDATE_AUDIT_CODEX_R4.md`):**
  `449d958fedef5a76e630ea9a8eb78061c26cb3ce`.
- **SHA inmutable de lectura secundaria de `CLAUDEBOT` (fijado por
  Miguel):** `3af01c5e96240bba9f7cf95904844efb15fca6a0`.

Este informe se redactó bajo la instrucción operacional de inicio
efectivo de implementación documental de la Fase 1, sujeta
estrictamente al mandato aprobado y a la decisión durable versionada en
el commit base de implementación. No autoriza por sí mismo integración,
push, congelación ni cierre.

## 2. Preflight

```text
$ pwd
/home/miguel/proyectos/CLAUDEBOT-CONTROL-SONNET-AI-GOV-F1-IMPLEMENTATION

$ git branch --show-current
control/sonnet-ai-gov-f1-implementation

$ git rev-parse HEAD
00649d65760255f1e186f82a997de915afa41b73

$ git status --short
[sin salida]
```

El directorio, la rama, el HEAD y el árbol limpio coincidieron
exactamente con la instrucción operacional. La implementación
continuó.

## 3. Fuentes normativas abiertas en `CLAUDEBOT-CONTROL`

Leídas exclusivamente mediante `git show` contra los commits exactos
indicados por la instrucción operacional, sin sustituir ningún blob
por el working tree, `main`, `origin/main`, ramas, tags ni hashes
abreviados:

1. `aa965803f103bfd3923ddd8fdbd04dd87253367a:tasks/AI-GOV-F1-CANONICAL/MANDATE.md`.
2. `aa965803f103bfd3923ddd8fdbd04dd87253367a:tasks/AI-GOV-F1-CANONICAL/ACCEPTANCE.md`.
3. `00649d65760255f1e186f82a997de915afa41b73:decisions/OWNER_DECISIONS.md`.
4. `00649d65760255f1e186f82a997de915afa41b73:AGENTS.md`.
5. `449d958fedef5a76e630ea9a8eb78061c26cb3ce:reports/AI-GOV-F1-CANONICAL/MANDATE_AUDIT_CODEX_R4.md`.

No se abrió ninguna otra ruta de `CLAUDEBOT-CONTROL` con fines
normativos.

## 4. Huella de estado de `CLAUDEBOT` — captura inicial

Ejecutada antes de leer las cuatro rutas secundarias de `CLAUDEBOT`,
exactamente conforme a `MANDATE.md` §3:

```text
$ git -C /home/miguel/proyectos/CLAUDEBOT rev-parse HEAD
3af01c5e96240bba9f7cf95904844efb15fca6a0
código de salida: 0

$ bash -o pipefail -c \
    'git -C /home/miguel/proyectos/CLAUDEBOT status --porcelain=v1 -z | sha256sum'
e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855  -
código de salida: 0
```

Ambos comandos terminaron con código de salida `0`. El HEAD obtenido
coincide exactamente con el SHA fijado por Miguel
(`3af01c5e96240bba9f7cf95904844efb15fca6a0`) y el digest obtenido
coincide exactamente con el digest fijado por Miguel
(`e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855`).
La captura es válida y la implementación continuó.

No se registra ni se expone la salida textual de `status`, ni nombres
de archivo o rutas provenientes de ella.

## 5. Cuatro blobs de `CLAUDEBOT` abiertos

Leídos exclusivamente mediante `git show` contra el SHA fijado
`3af01c5e96240bba9f7cf95904844efb15fca6a0`, sin abrir el working tree
de `CLAUDEBOT` y sin ejecutar `cat`, `sed`, `rg`, `grep`, `find` ni
`ls` sobre rutas de `CLAUDEBOT`:

1. `git -C /home/miguel/proyectos/CLAUDEBOT show 3af01c5e96240bba9f7cf95904844efb15fca6a0:AGENTS.md`.
2. `git -C /home/miguel/proyectos/CLAUDEBOT show 3af01c5e96240bba9f7cf95904844efb15fca6a0:docs/estado_rector_post_f8.md`.
3. `git -C /home/miguel/proyectos/CLAUDEBOT show 3af01c5e96240bba9f7cf95904844efb15fca6a0:docs/campania_t1_btcusdt_1h.md`.
4. `git -C /home/miguel/proyectos/CLAUDEBOT show 3af01c5e96240bba9f7cf95904844efb15fca6a0:docs/borrador_arquitectura_documental_t2.md`.

No se leyó ninguna quinta ruta de `CLAUDEBOT`. No se modificó
`CLAUDEBOT`.

## 6. Archivos creados y modificados

Exclusivamente las cinco rutas autorizadas en `MANDATE.md` §3 para
escritura de Sonnet:

| Ruta | Operación |
|---|---|
| `AGENTS.md` | Modificado (añadida §8, sin tocar §1-§7) |
| `governance/core/INSTITUTIONAL_CORE.md` | Creado |
| `governance/core/ADAPTER_REVIEW_POLICY.md` | Creado |
| `governance/projects/CLAUDEBOT_PROFILE.md` | Creado |
| `reports/AI-GOV-F1-CANONICAL/IMPLEMENTATION_REPORT.md` | Creado (este archivo) |

No se modificó ni creó ninguna otra ruta.

## 7. Estructura de cada documento

### 7.1 `AGENTS.md`

Se añadió la §8 ("Documentos canónicos de la Fase 1 de gobernanza
multi-IA"), que: distingue expresamente que el mandato y sus criterios
de aceptación se encuentran bajo `tasks/AI-GOV-F1-CANONICAL/`, mientras
que los tres documentos canónicos producidos por la implementación son
las rutas literales bajo `governance/` enumeradas a continuación —
corrigiendo la formulación anterior, que presentaba
`tasks/AI-GOV-F1-CANONICAL/` como la ubicación de los documentos
canónicos—; enlaza las tres rutas canónicas por ruta literal; explica
brevemente la función de cada una; fija el orden de lectura y
precedencia (Capa A > Capa A > Capa B); declara el estado `BORRADOR —
NO CONGELADO` de los tres; y reitera, sin duplicarlas, las ocho reglas
críticas ya existentes en §1-§7 (autoridad exclusiva de Miguel,
taxonomía `APROBAR`/`RECHAZAR`/`BLOQUEAR`, aislamiento entre agentes
—incluida la separación Sonnet implementador/Codex auditor—, bloqueo
ante hallazgos críticos, estructura de mandatos, estructura de
informes, control de ramas y merges, y prohibiciones de alcance sobre
`CLAUDEBOT`). El cambio es puramente aditivo; §1-§7 permanecen
textualmente intactas. `AGENTS.md` continúa siendo únicamente la
puerta de entrada y el índice; no reproduce el contenido normativo
detallado de los documentos canónicos.

### 7.2 `governance/core/INSTITUTIONAL_CORE.md`

Documento de Capa A, agnóstico de proveedor, modelo, herramienta,
proyecto, repositorio y dominio de aplicación. Contiene 19 secciones:
propósito; autoridad exclusiva (§2), con una nueva subsección §2.1 que
fija el titular vigente del rol abstracto "propietario" en esta
instalación del marco: exclusivamente **Miguel**, sin que ningún
agente, persona, herramienta o responsable de proyecto pueda asumir
ese rol por inferencia, delegación implícita, costumbre o
disponibilidad técnica, y sin que ningún cambio de titular pueda
ocurrir sin una decisión previa, expresa y durable de Miguel; separación
de funciones; **precedencia normativa (§4, corregida en esta revisión:
jerarquía completa de siete niveles — autorización operacional actual
del propietario, decisiones institucionales duraderas, esta Capa A,
Capa B, mandato vigente, adaptador de Capa D e instrucción
conversacional —, la regla de que un nivel inferior nunca relaja uno
superior, la regla de superación explícita de cuatro elementos
[excepción, regla reemplazada, alcance, duración], y la aclaración de
que la Capa C no ocupa ningún nivel de esta lista)**; listas cerradas de
permisos; control de alcance; principio de mínima autoridad;
trazabilidad e historia inmutable; evidencia fijada por commit y ruta
literal; prohibición de referencias móviles; auditoría independiente;
veredictos válidos (`APROBAR`/`RECHAZAR`/`BLOQUEAR`), **con una §12.1
que define los estados de tarea: las siete etapas ordinarias `INTAKE →
PLANIFICADA → AUTORIZADA → EN IMPLEMENTACIÓN → EN AUDITORÍA → INTEGRADA
→ CERRADA`, sus once transiciones normativas exactas (incluidas las
condiciones completas para `EN AUDITORÍA → INTEGRADA` —informe
versionado, commit exacto auditado, veredicto vigente `APROBAR`,
ausencia de hallazgos bloqueantes, autorización expresa del propietario
para el merge—, para `EN AUDITORÍA → CERRADA` y para `EN AUDITORÍA → EN
IMPLEMENTACIÓN` ante `RECHAZAR`) y los dos estados transversales
`BLOQUEADA` y `DETENIDA POR INCIDENTE` con sus reglas de salida,
distinguidos expresamente de los estados institucionales de un
adaptador definidos en `governance/core/ADAPTER_REVIEW_POLICY.md`**;
regla del hallazgo crítico; manejo de conflictos entre instrucciones; prohibición de
autoautorización (§15, actualizada para remitir a §2.1); prohibición de
acciones irreversibles sin decisión del propietario (§16, actualizada
para remitir a §2.1); tratamiento de la incertidumbre; diferencia entre
hipótesis, evidencia y regla validada; e imposibilidad de que una
Capa B relaje esta Capa A. Declarado `BORRADOR — NO CONGELADO` en
cabecera y cierre. No contiene vocabulario científico, de mercado ni de
`CLAUDEBOT`.

**Comprobación de la definición del titular (resultado real):**

```text
$ grep -n 'Miguel' governance/core/INSTITUTIONAL_CORE.md
40:  exclusivamente a **Miguel**.
45:  expresa y durable de Miguel, registrada conforme a §8 (trazabilidad e
50:  Miguel.
192:  expresa y registrada del propietario (en esta instalación, Miguel,
202:  instalación, Miguel, conforme a §2.1) que la autorice específicamente.
```

Las cinco coincidencias son exactamente: la asignación exclusiva de
§2.1 (línea 40), la exigencia de decisión previa, expresa y durable
para cambiar de titular (línea 45), el cierre de §2.1 (línea 50), y
las remisiones de §15 y §16 a esa misma asignación (líneas 192 y 202).
Ninguna otra persona, agente o herramienta aparece como titular
alternativo del rol de propietario en este documento.

### 7.3 `governance/core/ADAPTER_REVIEW_POLICY.md`

Documento de Capa A, estructurado alrededor de un **registro
estrictamente append-only** (§3). Toda entrada declara **dieciocho
campos comunes** (§3.1), incluidos **autor material** (campo 17:
identidad y rol exacto, `PROPONENTE AUTORIZADO` o
`REGISTRADOR AUTORIZADO`) y **autorización de escritura** (campo 18).
Las entradas de `AUDITORÍA` y `DECISIÓN` declaran además los campos
19-20: **propuesta raíz del ciclo** y **propuesta exacta evaluada o
decidida**.

**Dos estructuras de referencia distintas (§3.1):** (A) el **puntero
durable completo entre entradas** (campos 8, 9, 10, 19 y 20: cinco
datos — repositorio, commit, ruta del registro, identificador estable
del adaptador, identificador de entrada); y (B) la **referencia
durable de autorización de escritura** (campo 18, exclusivamente:
repositorio, commit, ruta del mandato o decisión, identificador de
tarea, ruta autorizada del registro, y tipos de entrada permitidos),
que **no exige** identificador de adaptador ni de entrada, porque
autoriza una escritura y no apunta a una entrada ya existente.

**Campo 8 causal frente a campo 9 global (§3.1, §4):** el campo 8 es
la entrada causal anterior dentro del mismo ciclo (la `PROPUESTA` que
audita una `AUDITORÍA`, la `AUDITORÍA` sobre la que decide una
`DECISIÓN`, la `DECISIÓN` `VIGENTE` que activa un `DISPARADOR`); el
campo 9 es la cabeza global única real del adaptador en el commit
base de la operación. Ambos pueden coincidir, pero no están obligados
a coincidir: si media una `SUPERSESIÓN` administrativa, el campo 8
conserva el hito causal y el campo 9 apunta a esa `SUPERSESIÓN`.

**Definición de entrada válida (§3.2):** una entrada solo es válida si
concurren ocho requisitos: campos completos; autor material
identificado; autorización de escritura previa, existente y
pertinente al tipo; punteros que resuelven a commits y entradas
preexistentes; ausencia de autorreferencia Git; entrada precedente
global igual a la cabeza global única cuando el campo 9 no es
`NO APLICA` (con la excepción expresa de la primera `PROPUESTA`
histórica); cumplimiento de las reglas propias del tipo; y versionado
sin tocar rutas no autorizadas. Se **eliminó** el requisito de "no
contradecir una entrada durable posterior": una entrada de `DECISIÓN`
o `SUPERSESIÓN` posterior puede reemplazar, rechazar o superseder
efectos hacia adelante sin invalidar retroactivamente la entrada
histórica anterior. Una entrada inválida no determina estado: es una
**condición operacional de bloqueo**, no el veredicto formal
`BLOQUEAR` — ese veredicto es exclusivo del auditor independiente
(§12).

**Cabeza global única, definición determinista (§3.3):** en un commit
exacto del registro, la cabeza global de un adaptador es la única
entrada válida de ese adaptador que no aparece referenciada en el
campo 9 de ninguna otra entrada válida del mismo adaptador presente en
ese mismo commit. Exactamente una cabeza habilita la lectura; cero
cabezas (cadena circular o corrupta) o más de una cabeza (bifurcación)
son condiciones operacionales de bloqueo; el orden visual y las fechas
no resuelven la cabeza. Ante bifurcación, el estado es ambiguo, ningún
`VIGENTE` es invocable, no se usa `SUPERSESIÓN` ordinaria, y la
recuperación exige mandato específico, auditoría independiente y
decisión durable de Miguel.

**El registrador no emite veredictos (§3.2, §4.2, §4.3, §5):** ante
datos faltantes, discordantes o ambiguos (incluida una bifurcación de
cabeza global), el registrador se detiene, no agrega la entrada,
reporta una condición operacional de bloqueo, y solicita la
corrección, la nueva auditoría o la decisión durable que corresponda;
nunca convierte ese reporte en un veredicto propio. Los únicos
veredictos institucionales (`APROBAR`, `RECHAZAR`, `BLOQUEAR`) los
emite exclusivamente el auditor independiente.

**Separación auditor/informe/registro y Miguel/decisión/registro**
(§4.2, §4.3, §5, §10, §12): el auditor produce su informe —con
repositorio, commit del artefacto, ruta, punteros a propuesta raíz y
exacta, ciclo, veredicto y hallazgos— en un commit propio; no modifica
el registro ni agrega la entrada de `AUDITORÍA`. Miguel emite su
decisión —con los mismos punteros más el resultado exacto
`ACTIVAR`/`REACTIVAR`/`RECHAZAR` y fecha— en
`decisions/OWNER_DECISIONS.md`; no modifica el registro bajo ninguna
forma, **ni siquiera para registrar directamente un rechazo** (§6.2,
corregido: el flujo de rechazo siempre pasa primero por la decisión
durable de Miguel y solo después por la transcripción del
registrador). Solo después, el registrador autorizado transcribe
exactamente esas entradas.

**Reporte de hipótesis frente a registro autorizado (§8, §4.1, §5):**
cualquier agente puede reportar una posible hipótesis; reportarla no
concede permiso de escritura. Solo un proponente autorizado, con
mandato expreso y permiso literal, puede materializarla; sin ese
mandato, permanece reportada pero no registrada.

**`SUPERSESIÓN` completa (§4.5, §9-C):** abre su propio ciclo
administrativo (identificador de ciclo nuevo); campo 7 = `SUPERSESIÓN`;
campo 8 = `NO APLICA`; campo 9 = puntero a la cabeza global real;
campo 10 = puntero a la entrada histórica corregida, que **no necesita
ser la cabeza global**; repite, sin alterarlos, el campo 11 y la fecha
de última revisión concluida de la entrada precedente global (campo
9), no necesariamente los de la entrada supersedida; corrige
exclusivamente datos descriptivos no sustantivos; y **ya no puede
modificar la fecha de última revisión concluida bajo ninguna
justificación**. Queda **eliminada** de la secuencia numerada del
ciclo de revalidación de §9-C: es una operación administrativa
separada, no un hito obligatorio de ese ciclo.

**Origen, estado y fecha completos por tipo (§4.1, §6.1):** una
`PROPUESTA` de revalidación y su `AUDITORÍA` subsiguiente permanecen
`REVISIÓN REQUERIDA`; solo la propuesta inicial, su corrección dentro
del mismo ciclo, y el ciclo nuevo tras el rechazo de una activación
inicial producen `HIPÓTESIS NO VALIDADA`. §6.1 ya no afirma que
"cualquier `PROPUESTA`" origina `HIPÓTESIS NO VALIDADA`.

**Vencimiento automático de 90 días (§6, §7, §9-A, §9-B):** el quinto
disparador ocurre automáticamente al cumplirse el plazo desde la
fecha de última revisión concluida, sin depender de que un agente lo
advierta; antes de cada uso se compara la fecha actual con esa fecha
durable; al cumplirse 90 días, el adaptador pasa de inmediato a
`REVISIÓN REQUERIDA` aunque no exista todavía la entrada de
`DISPARADOR`, que el registrador debe formalizar después. La condición
"conocido y verificable" rige exclusivamente los otros cuatro eventos.

**Definición completa de `VIGENTE` (§6):** exige, todos a la vez: campo
11 de la cabeza global única en `VIGENTE`; propuesta exacta
identificada; auditoría independiente sobre esa misma propuesta;
veredicto exacto `APROBAR`; ausencia de hallazgos críticos; ausencia
de propuesta posterior pendiente; decisión previa, expresa y durable
de Miguel que autoriza exactamente `ACTIVAR`/`REACTIVAR` esa misma
propuesta; y entrada de `DECISIÓN` agregada después por el registrador
que transcribe esa decisión sin discordancia. Las seis comprobaciones
técnicas de §4.3 **no sustituyen** la decisión durable de Miguel:
ambas son necesarias conjuntamente. El campo 13 de `DECISIÓN` debe
citar el mismo artefacto exacto que la propuesta exacta, el informe,
la entrada de `AUDITORÍA` y la decisión durable; cualquier diferencia
es una condición operacional de bloqueo.

**Secuencia de commits con correcciones (§10):** la ruta limpia tiene
seis commits (artefacto, `PROPUESTA`, informe, `AUDITORÍA`, decisión
durable, `DECISIÓN`); cada corrección posterior a una `AUDITORÍA` con
`RECHAZAR`/`BLOQUEAR` inserta cuatro commits adicionales (artefacto
corregido, `PROPUESTA` corregida, informe, `AUDITORÍA`) antes de los
commits 5 y 6, elevando una corrección a diez commits; cada corrección
adicional agrega otros cuatro. Ningún hito puede omitirse, agruparse
ni colapsarse.

Los cinco eventos de revisión obligatoria (§7) —el primero de ellos
corregido en esta revisión a su formulación exacta, **"cambio mayor o
relevante del modelo, incluida su versión o revisión identificada"**,
en reemplazo de la formulación anterior ("cualquier cambio de modelo...
sin evaluación previa de materialidad")—; la incompatibilidad de un
adaptador con la Capa A (§11); y los veredictos y la autoridad final
(§12), reforzando que ninguna discordancia de punteros ni ninguna
bifurcación de cabeza global permite `VIGENTE`. La referencia de §6 a
las comprobaciones técnicas de §4.3 se corrigió en esta revisión de
"cinco" a **"seis"**, para que coincida con las seis condiciones
numeradas que §4.3 exige efectivamente. Declarado `BORRADOR — NO
CONGELADO`. No contiene vocabulario específico de `CLAUDEBOT`.

### 7.4 `governance/projects/CLAUDEBOT_PROFILE.md`

Primer perfil de Capa B para `CLAUDEBOT`. Centraliza exclusivamente
aquí las cuatro referencias normativas documentales autorizadas
(repositorio, SHA completo `3af01c5e96240bba9f7cf95904844efb15fca6a0`,
ruta literal y función normativa, en tabla). Las cuatro funciones
normativas quedan reducidas a explicar, en una frase breve, qué
restricción funda cada documento —sin trasladar resultados
científicos, valores ni parámetros, presupuesto ni conteo de
hipótesis, reglas de muerte, resultados de discovery/OOS, descripción
de campañas sucesoras ni conclusiones científicas—: `AGENTS.md` funda
las reglas locales de operación y el régimen fail-closed de
`CLAUDEBOT`; `docs/estado_rector_post_f8.md` funda la obligación de
respetar el estado rector vigente y no ejecutar fases pendientes sin
mandato propio; `docs/campania_t1_btcusdt_1h.md` funda el respeto de
la carta de campaña congelada sin modificarla; y
`docs/borrador_arquitectura_documental_t2.md` funda que esa
arquitectura es un borrador no rector y no congelado que no autoriza
ejecutar T2.

Añade siete restricciones adicionales sin relajar la Capa A: no
modificar `CLAUDEBOT`; no abrir ni continuar campañas o fases de
investigación de `CLAUDEBOT`, con la prohibición literal e
independiente de abrir, continuar, ejecutar, acelerar o autorizar
`F-1A`, `F10`, `F11` o `T2` durante esta Fase 1; no abrir datos ni
resultados; no ejecutar verificación de comportamiento; no copiar el
corpus de juicio de `CLAUDEBOT` —identificado literalmente en el punto
5 de §3 como **Fable Judgment v1, sistema documental de juicio
independiente del proveedor**, con declaración expresa de que durante
esta Fase 1 no se reproduce, transcribe ni incorpora su contenido
sustantivo, no se ejecuta validación ni benchmark conductual sobre él,
no se declara conductualmente validado, y cualquier benchmark
conductual continúa pendiente y fuera del alcance de esta Fase 1—;
toda hipótesis de adaptación derivada de `CLAUDEBOT` es
`HIPÓTESIS NO VALIDADA`; no se crean `judgment/`, `adapters/` ni
`tests/`. Fija el estado operativo de `CLAUDEBOT` para esta operación
(anclado al SHA, sin declaración editorial adicional sobre `CLAUDEBOT`
como proyecto) y mantiene, en §5, la autoridad final de **Miguel, en su
rol de propietario y autoridad final** (remitiendo a
`governance/core/INSTITUTIONAL_CORE.md` §2 y §2.1), y la exigencia de
auditoría independiente para cualquier ampliación futura de sus
referencias. **La §6 ("Rutas y artefactos propios del proyecto"), cuyo
texto se corrigió íntegramente en esta corrección (Revisión 13)**,
declara las convenciones genéricas de ubicación institucional dentro de
`CLAUDEBOT-CONTROL` para cualquier tarea que coordine a `CLAUDEBOT`:
`tasks/<ID>/MANDATE.md` para el mandato, `tasks/<ID>/ACCEPTANCE.md`
para sus criterios verificables cuando correspondan, y `reports/<ID>/`
para los informes de implementación y auditoría, exigiendo que cada
mandato identifique las rutas literales concretas que puede crear o
modificar. Declara expresamente que los documentos congelados o
rectores propios de `CLAUDEBOT` **permanecen en su repositorio de
origen y en sus rutas nativas** —este perfil no los mueve, copia ni
presume congelados o rectores— y que un documento de `CLAUDEBOT` solo
cumple función normativa para una tarea de este marco cuando aparece en
la tabla de §2 con repositorio, SHA completo, ruta literal y función
normativa. Aclara que las convenciones genéricas `tasks/<ID>/...` y
`reports/<ID>/...` son declaraciones de ubicación institucional, no
referencias normativas documentales adicionales a `CLAUDEBOT`. Declarado
`BORRADOR — NO CONGELADO`. No transcribe contenido científico de
`CLAUDEBOT`: usa exclusivamente punteros y funciones normativas breves.
Esta corrección no abrió ninguna ruta adicional de `CLAUDEBOT`: la §6
corregida solo declara convenciones genéricas de `CLAUDEBOT-CONTROL`,
sin consultar ningún blob nuevo de `CLAUDEBOT`.

### 7.5 `reports/AI-GOV-F1-CANONICAL/IMPLEMENTATION_REPORT.md`

Este mismo documento.

## 8. Comandos ejecutados

```text
pwd
git branch --show-current
git rev-parse HEAD
git status --short

git show aa965803f103bfd3923ddd8fdbd04dd87253367a:tasks/AI-GOV-F1-CANONICAL/MANDATE.md
git show aa965803f103bfd3923ddd8fdbd04dd87253367a:tasks/AI-GOV-F1-CANONICAL/ACCEPTANCE.md
git show 00649d65760255f1e186f82a997de915afa41b73:AGENTS.md
git show 00649d65760255f1e186f82a997de915afa41b73:decisions/OWNER_DECISIONS.md
git show 449d958fedef5a76e630ea9a8eb78061c26cb3ce:reports/AI-GOV-F1-CANONICAL/MANDATE_AUDIT_CODEX_R4.md

git -C /home/miguel/proyectos/CLAUDEBOT rev-parse HEAD
bash -o pipefail -c \
  'git -C /home/miguel/proyectos/CLAUDEBOT status --porcelain=v1 -z | sha256sum'

git -C /home/miguel/proyectos/CLAUDEBOT show 3af01c5e96240bba9f7cf95904844efb15fca6a0:AGENTS.md
git -C /home/miguel/proyectos/CLAUDEBOT show 3af01c5e96240bba9f7cf95904844efb15fca6a0:docs/estado_rector_post_f8.md
git -C /home/miguel/proyectos/CLAUDEBOT show 3af01c5e96240bba9f7cf95904844efb15fca6a0:docs/campania_t1_btcusdt_1h.md
git -C /home/miguel/proyectos/CLAUDEBOT show 3af01c5e96240bba9f7cf95904844efb15fca6a0:docs/borrador_arquitectura_documental_t2.md

mkdir -p governance/core governance/projects
[creación de governance/core/INSTITUTIONAL_CORE.md]
[creación de governance/core/ADAPTER_REVIEW_POLICY.md]
[creación de governance/projects/CLAUDEBOT_PROFILE.md]
[edición de AGENTS.md — añadida §8]

grep -in -e dataset -e discovery -e OOS -e trading -e quintil -e BTCUSDT governance/core/INSTITUTIONAL_CORE.md
grep -n 'Miguel' governance/core/INSTITUTIONAL_CORE.md
git diff --name-only 00649d65760255f1e186f82a997de915afa41b73 -- judgment adapters tests
git status --short --untracked-files=all -- judgment adapters tests
git status --short --untracked-files=all
grep -in -e 'F-1A' -e F10 -e F11 -e T2 governance/projects/CLAUDEBOT_PROFILE.md

grep -nE \
  -e 'CLAUDEBOT' \
  -e '[0-9a-f]{40}' \
  AGENTS.md \
  governance/core/INSTITUTIONAL_CORE.md \
  governance/core/ADAPTER_REVIEW_POLICY.md \
  governance/projects/CLAUDEBOT_PROFILE.md \
  reports/AI-GOV-F1-CANONICAL/IMPLEMENTATION_REPORT.md

git -C /home/miguel/proyectos/CLAUDEBOT rev-parse HEAD
bash -o pipefail -c \
  'git -C /home/miguel/proyectos/CLAUDEBOT status --porcelain=v1 -z | sha256sum'

git diff --check
git status --short
git status --short --untracked-files=all
git diff --cached --name-status
git status --short --untracked-files=all -- judgment adapters tests
git diff --name-status
git diff --stat
```

El comando de A-07 se ejecuta sobre los cinco artefactos, incluido
este propio informe, una vez que su texto queda finalizado; su
resultado real y su clasificación manual se registran en §12.1. Tras
ejecutar ese control, ninguno de los cinco artefactos vuelve a
editarse; si alguno se editara, el control debería repetirse.

Ningún comando anterior abrió datasets, CSV, resultados, discovery,
OOS, producción ni ejecutó código científico o de validación
conductual.

## 9. Huella de estado de `CLAUDEBOT` — captura final

Ejecutada después de redactar los cinco artefactos y antes de cerrar
este informe:

```text
$ git -C /home/miguel/proyectos/CLAUDEBOT rev-parse HEAD
3af01c5e96240bba9f7cf95904844efb15fca6a0
código de salida: 0

$ bash -o pipefail -c \
    'git -C /home/miguel/proyectos/CLAUDEBOT status --porcelain=v1 -z | sha256sum'
e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855  -
código de salida: 0
```

Ambos comandos terminaron con código de salida `0`.

## 10. Comparación inicial/final y límites probatorios

| | HEAD | Digest | Código HEAD | Código estado |
|---|---|---|---|---|
| Captura inicial | `3af01c5e96240bba9f7cf95904844efb15fca6a0` | `e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855` | 0 | 0 |
| Captura final | `3af01c5e96240bba9f7cf95904844efb15fca6a0` | `e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855` | 0 | 0 |

Las dos huellas son exactamente iguales. Esta igualdad es evidencia del
estado Git observable en `HEAD` y en `status --porcelain=v1 -z` en
ambos límites de la tarea; **no cubre archivos ignorados por Git ni un
cambio transitorio restaurado antes de la segunda captura**, y no
constituye una demostración absoluta de ausencia de modificación. No
se creó ningún cambio ni commit nuevo en `CLAUDEBOT`. Un estado previo
ajeno a esta tarea, si existiera, queda representado únicamente por su
SHA-256, y permanece intacto.

## 11. Comprobación de alcance

```text
$ git diff --check
[sin salida; código de salida 0]

$ git status --short
 M AGENTS.md
?? governance/core/ADAPTER_REVIEW_POLICY.md
?? governance/core/INSTITUTIONAL_CORE.md
?? governance/projects/CLAUDEBOT_PROFILE.md
?? reports/AI-GOV-F1-CANONICAL/IMPLEMENTATION_REPORT.md

$ git status --short --untracked-files=all
 M AGENTS.md
?? governance/core/ADAPTER_REVIEW_POLICY.md
?? governance/core/INSTITUTIONAL_CORE.md
?? governance/projects/CLAUDEBOT_PROFILE.md
?? reports/AI-GOV-F1-CANONICAL/IMPLEMENTATION_REPORT.md

$ git diff --cached --name-status
[sin salida]

$ git status --short --untracked-files=all -- judgment adapters tests
[sin salida]

$ git diff --name-status
M	AGENTS.md
```

El estado completo del árbol de trabajo (`git status --short
--untracked-files=all`, sin filtrar) muestra exactamente las cinco
rutas autorizadas en `MANDATE.md` §3 para escritura de Sonnet, y
ninguna otra — no queda "sin salida": su salida son esas cinco líneas.
El control limitado a `judgment/`, `adapters/` y `tests/`
(`git status --short --untracked-files=all -- judgment adapters
tests`) sí queda sin salida, igual que `git diff --name-only
<commit-base> -- judgment adapters tests`; este último, por sí solo,
no cubre archivos no rastreados por Git, por lo que se complementa con
el primero, que sí los cubre mediante `--untracked-files=all`. El
índice está vacío (`git diff --cached --name-status` sin salida). No
se ejecutó `git add` ni se creó ningún commit en este repositorio
durante esta operación.

## 12. Evidencia individual — A-01 a A-17 y A-20

| Criterio | Evidencia |
|---|---|
| A-01 | El árbol de trabajo, comparado contra el commit base `00649d65760255f1e186f82a997de915afa41b73`, contiene exclusivamente los cinco archivos de §6 como cambios (uno modificado, cuatro creados). Ningún otro archivo cambia. |
| A-02 | `AGENTS.md` conserva íntegras §1-§7 (autoridad, veredictos, aislamiento, bloqueo crítico, estructura de mandatos, estructura de informes, ramas/merges, alcance sobre `CLAUDEBOT`) y añade §8 como índice hacia los tres documentos canónicos, sin duplicar su contenido normativo detallado. |
| A-03 | `grep -in -e dataset -e discovery -e OOS -e trading -e quintil -e BTCUSDT governance/core/INSTITUTIONAL_CORE.md` no produjo coincidencias (código de salida 1). |
| A-04 | `governance/core/INSTITUTIONAL_CORE.md` contiene secciones explícitas de autoridad (§2), precedencia (§4, con la jerarquía completa de siete niveles, la regla de superación explícita, la aclaración de Capa C y, agregada en esta corrección, la aclaración de que informes, estados documentales y evidencia Git no constituyen un nivel normativo autónomo), permisos (§5), alcance (§6), veredictos/estados (§12-§13, con la §12.1 de estados de tarea que ahora contiene tanto la taxonomía de siete etapas y dos estados transversales como sus once transiciones normativas exactas y las condiciones completas de integración, cierre y reapertura, agregadas en esta corrección) y conflictos (§14). |
| A-05 | Lectura manual completa de `governance/core/INSTITUTIONAL_CORE.md`: ningún vocabulario de dominio científico se presenta como regla universal. |
| A-06 | Comparación manual de `governance/projects/CLAUDEBOT_PROFILE.md` §3 y §6 (esta última, con su texto corregido en esta corrección para declarar únicamente convenciones genéricas `tasks/<ID>/...` y `reports/<ID>/...`, sin presumir congelados los documentos de §2 ni introducir una quinta referencia normativa) contra `governance/core/INSTITUTIONAL_CORE.md`: el perfil solo añade restricciones y declara convenciones de ubicación; ninguna cláusula relaja una regla de Capa A. |
| A-07 | Control real sobre los cinco artefactos, incluido este propio informe, ejecutado y clasificado en §12.1 después de finalizar textualmente los cinco archivos. Es el autocontrol provisional del working tree de Sonnet, no anclado a commit; Codex deberá repetirlo anclado al futuro commit exacto de implementación. |
| A-08 | `governance/projects/CLAUDEBOT_PROFILE.md` §2 reduce las cuatro funciones normativas a una frase breve por documento, sin trasladar resultados científicos, valores ni parámetros, presupuesto ni conteo de hipótesis, reglas de muerte, resultados de discovery/OOS, descripción de campañas sucesoras ni conclusiones científicas (ver texto exacto en §7.4 de este informe); usa exclusivamente punteros (SHA, ruta) y funciones normativas descriptivas. |
| A-09 | `grep -in -e 'F-1A' -e F10 -e F11 -e T2 governance/projects/CLAUDEBOT_PROFILE.md` coincide con el nombre de archivo `docs/borrador_arquitectura_documental_t2.md` (referencia documental existente) y con la prohibición literal añadida en §3.2 del perfil ("Durante esta Fase 1 queda prohibido abrir, continuar, ejecutar, acelerar o autorizar F-1A, F10, F11 o T2"); ambas coincidencias son descriptivas del estado existente o prohibitivas, y ninguna abre, continúa ni autoriza una fase. |
| A-10 | `governance/core/ADAPTER_REVIEW_POLICY.md` define el esquema de **dieciocho campos comunes** (§3.1), con dos estructuras de referencia distintas —puntero durable completo entre entradas (campos 8, 9, 10, 19, 20) y referencia durable de autorización de escritura (campo 18, sin exigir identificador de adaptador ni de entrada)—; la diferenciación entre campo 8 (causal, dentro del ciclo) y campo 9 (cabeza global real, puede diferir por `SUPERSESIÓN`); la **definición de entrada válida** (§3.2, ocho requisitos, sin el requisito eliminado de "no contradecir una entrada posterior"); la **cabeza global única determinista** (§3.3: exactamente una cabeza, cero cabezas o más de una cabeza, sin resolver por orden visual ni fechas); el registrador que nunca emite el veredicto formal `BLOQUEAR`, sino que reporta una condición operacional de bloqueo (§3.2, §4.2, §4.3, §5); la separación auditor/informe/registro y Miguel/decisión/registro, sin que Miguel escriba nunca directamente en el registro, ni siquiera para un rechazo (§4.3, §5, §6.2); `SUPERSESIÓN` completa con ciclo administrativo propio (§4.5, §9-C); el vencimiento automático de 90 días (§6, §7, §9-A, §9-B); la secuencia de commits con inserciones por corrección (§10); y la definición completa de `VIGENTE` (§6). El primer evento de §7 quedó corregido en esta revisión a su formulación exacta ("cambio mayor o relevante del modelo, incluida su versión o revisión identificada"), y la referencia de §6 a las comprobaciones técnicas de §4.3 quedó corregida de "cinco" a "seis", conforme a las seis condiciones numeradas que §4.3 exige efectivamente. |
| A-11 | `governance/core/ADAPTER_REVIEW_POLICY.md` §6 define los tres estados institucionales por el campo 11 de la **cabeza global única**, determinista, válida y no supersedida (§3.2, §3.3), cualquiera sea su tipo; §6.1 fija el origen exacto de cada uno, distinguiendo expresamente que una `PROPUESTA`/`AUDITORÍA` de revalidación permanece `REVISIÓN REQUERIDA` y no origina `HIPÓTESIS NO VALIDADA` (corregido: ya no se afirma que "cualquier `PROPUESTA`" la origina); §6.2 corrige el flujo de rechazo para que Miguel decida y registre durablemente primero, y el registrador transcriba después, sin excepción, en ambos casos del Caso A; §3.2 aclara que una entrada inválida no determina estado (condición operacional de bloqueo, no veredicto); §8 distingue expresamente reportar una hipótesis (cualquier agente) de registrarla como `PROPUESTA` (solo el proponente autorizado). |
| A-12 | `governance/core/ADAPTER_REVIEW_POLICY.md` §8: ninguna entrada `HIPÓTESIS NO VALIDADA` concede permiso ni autonomía por sí sola, y reportar una hipótesis nunca concede permiso de escritura; §6.1/§6: ninguna entrada de `DECISIÓN` puede producir `VIGENTE` sobre `RECHAZAR`/`BLOQUEAR` o hallazgos críticos, con independencia de la voluntad de Miguel; §4.2/§4.3/§5: si el informe o la decisión durable carecen de los datos exigidos o presentan discordancias, el registrador se detiene, no completa ni infiere, y reporta una condición operacional de bloqueo — nunca emite el veredicto `BLOQUEAR`, exclusivo del auditor (§12); §3.3: una bifurcación de cabeza global impide invocar `VIGENTE` y exige tratamiento fail-closed, cerrando la posibilidad de que un fork no resuelto habilite autonomía; §5: el registrador no dictamina veredictos, no decide activaciones y no puede autoautorizarse ni autodesignarse. |
| A-13 | El estado completo del árbol (§11: `git status --short --untracked-files=all`) muestra exclusivamente las cinco rutas autorizadas, no ausencia de salida. El control limitado a `judgment/`, `adapters/` y `tests/` sí queda sin salida: `git status --short --untracked-files=all -- judgment adapters tests` (§11) y `git diff --name-only 00649d65760255f1e186f82a997de915afa41b73 -- judgment adapters tests` (§8), ambos sin salida; este segundo comando, por sí solo, no cubre archivos untracked, por lo que se complementa con el primero. Este control cubre el working tree de Sonnet; Codex deberá repetir la comprobación anclada al futuro commit exacto de implementación. |
| A-14 | Ningún artefacto de esta implementación transcribe contenido del corpus de juicio de `CLAUDEBOT` (identificado literalmente como Fable Judgment v1, sistema documental de juicio independiente del proveedor); las menciones son terminológicas y por referencia (§3 de `governance/projects/CLAUDEBOT_PROFILE.md`); no se afirma validación conductual ni se ejecuta benchmark alguno; cualquier benchmark conductual queda declarado pendiente y fuera de alcance. |
| A-15 | §4, §9 y §10 de este informe: huellas inicial y final idénticas, ambos comandos con código de salida `0` en ambas capturas, sin exponer salida textual de `status`; solo se leyeron las cuatro rutas de `CLAUDEBOT` listadas en §5; no se crearon cambios en `CLAUDEBOT`. |
| A-16 | §8 de este informe: ningún comando ejecutado abrió datasets, CSV, discovery, OOS, producción ni scripts de validación conductual. |
| A-17 | Este informe declara archivos abiertos (§3, §5), archivos modificados (§6), comandos ejecutados (§8) y estado Git final (§11), conforme a `AGENTS.md` §5; registra los dos SHA fijados por Miguel (§1); registra la huella inicial y final de `CLAUDEBOT` sin exponer la salida textual de `status` (§4, §9); registra las cuatro rutas exactas leídas (§5); e incluye declaración negativa de que no se abrieron rutas adicionales (§5, §11, §13). |
| A-20 | Evidencia provisional del working tree, antes de que exista ningún commit objetivo de implementación: los tres documentos canónicos declaran `BORRADOR — NO CONGELADO` en cabecera y cierre (§7.2, §7.3, §7.4); `decisions/OWNER_DECISIONS.md` no está modificado (ausente de `git status --short --untracked-files=all`, §11); el estado completo del working tree (§11) muestra exactamente tres rutas bajo `governance/` (las tres canónicas) y ninguna cuarta ruta bajo ese directorio. Esto no es un diff base-objetivo: no existe todavía ningún commit objetivo de implementación. Codex deberá verificar, después de que ese commit exista, `git diff --name-status 00649d65760255f1e186f82a997de915afa41b73 <commit-objetivo-implementación>`; solo ese control futuro, sobre dos commits reales, puede acreditar el intervalo Git completo entre el commit base y el commit objetivo. |

### 12.1 Control final de A-07 sobre los cinco artefactos

Ejecutado después de finalizar textualmente los cinco artefactos, sin
que ninguno de ellos vuelva a editarse a partir de este punto:

```text
$ grep -nE \
    -e 'CLAUDEBOT' \
    -e '[0-9a-f]{40}' \
    AGENTS.md \
    governance/core/INSTITUTIONAL_CORE.md \
    governance/core/ADAPTER_REVIEW_POLICY.md \
    governance/projects/CLAUDEBOT_PROFILE.md \
    reports/AI-GOV-F1-CANONICAL/IMPLEMENTATION_REPORT.md
```

Clasificación manual de las coincidencias, en tres categorías:

1. **Referencias normativas documentales** — permitidas exclusivamente
   en `governance/projects/CLAUDEBOT_PROFILE.md` §2: las cuatro filas
   de su tabla, cada una con repositorio, SHA completo, ruta literal y
   función normativa. Ninguna otra coincidencia de los cinco
   artefactos pertenece a esta categoría.
2. **Referencias operacionales o evidenciales** — los SHA de mandato,
   commit base de implementación y auditoría R4, y los comandos y
   huellas de estado de `CLAUDEBOT` registrados en este informe
   (§1, §3-§5, §8-§10), sin restricción de cantidad conforme a la
   excepción de `ACCEPTANCE.md` A-07 para
   `IMPLEMENTATION_REPORT.md`.
3. **Menciones institucionales de alcance o prohibición** — las
   apariciones de `CLAUDEBOT` en `AGENTS.md` §1, §5, §7 y §8, y en la
   prosa de `governance/projects/CLAUDEBOT_PROFILE.md` fuera de la
   tabla de §2 (§1, §3, §4), que describen o aplican las restricciones
   ya centralizadas en esa tabla, sin constituir referencias
   normativas nuevas.

`governance/core/INSTITUTIONAL_CORE.md` y
`governance/core/ADAPTER_REVIEW_POLICY.md` no produjeron ninguna
coincidencia de `CLAUDEBOT` ni de un SHA de 40 caracteres.

Este control se ejecutó sobre el working tree de Sonnet en esta rama,
sin anclarlo a ningún commit; es el autocontrol provisional de esta
implementación. Codex deberá repetir este mismo control, anclado
mediante `git show <commit-objetivo-implementación>:<ruta>` o
`git grep <commit-objetivo-implementación>`, sobre el futuro commit
exacto de implementación, conforme a la fila A-07 de la matriz de
`ACCEPTANCE.md` §2.

## 13. Declaraciones negativas de alcance

- No se abrió ninguna ruta de `CLAUDEBOT` distinta de las cuatro
  enumeradas en §5.
- No se abrió el working tree de `CLAUDEBOT`; toda lectura fue
  mediante `git show` contra el SHA fijo.
- No se modificó `CLAUDEBOT` bajo ninguna forma.
- No se abrieron datasets, CSV, resultados, discovery, OOS, código
  científico ni producción, ni de `CLAUDEBOT` ni de ningún otro
  repositorio.
- No se ejecutó validación conductual.
- No se abrió, continuó ni aceleró F-1A, F10, F11 ni T2.
- No se copió, transcribió ni incorporó contenido sustantivo de Fable
  Judgment v1 (sistema documental de juicio independiente del
  proveedor, identificado literalmente en
  `governance/projects/CLAUDEBOT_PROFILE.md` §3 punto 5).
- No se ejecutó validación ni benchmark conductual sobre Fable
  Judgment v1; no se declaró conductualmente validado; cualquier
  benchmark conductual queda pendiente y fuera del alcance de esta
  Fase 1.
- No se crearon `judgment/`, `adapters/` ni `tests/`.
- No se amplió el alcance de escritura más allá de las cinco rutas
  autorizadas.
- No se ejecutó `git add`.
- No se creó ningún commit.
- No se hizo push, merge, rebase ni se crearon tags.
- No se declaró congelación, integración ni cierre de ningún
  documento ni de la Fase 1.
- No se borraron ramas ni worktrees.

## 14. Desviaciones e incidentes

**Incidentes operacionales y de alcance: ninguno.** Ambas huellas de
estado de `CLAUDEBOT` (inicial y final) coincidieron exactamente entre
sí y con los valores fijados por Miguel; ambos comandos de cada
captura terminaron con código de salida `0`; `CLAUDEBOT` no fue
modificado bajo ninguna forma; no hubo rutas no autorizadas fuera de
las cinco rutas de `MANDATE.md` §3; no se ejecutó `git add`, ni se creó
commit, ni se hizo push, merge, rebase, tag o congelación; el
preflight y el autocontrol de alcance no detectaron ninguna diferencia
respecto de lo autorizado.

**Hallazgos documentales precommit: sí, corregidos antes del staging y
del commit.** Durante la redacción de estos cinco artefactos, varias
revisiones de ChatGPT (recibidas como instrucciones operacionales
sucesivas de Miguel) detectaron defectos en los borradores previos de
`governance/core/ADAPTER_REVIEW_POLICY.md`,
`governance/projects/CLAUDEBOT_PROFILE.md`, `AGENTS.md` §8 y este
propio informe —entre otros: una referencia de sección incorrecta, una
ubicación mal atribuida en `AGENTS.md`, funciones normativas
sobrecargadas con contenido científico, definiciones de estado no
disjuntas, ausencia de exigencia de `APROBAR` para `VIGENTE`, un
mecanismo de registro mutable incompatible con la trazabilidad
append-only exigida, un esquema de entrada incompleto y sin
encadenamiento global entre ciclos, un tratamiento de un disparador
conocido que retrasaba su efecto operacional hasta su registro
documental, un ejemplo de agrupación de commits que habría producido
una autorreferencia Git imposible, una lectura del estado documental
condicionada por el tipo de entrada en vez del campo común, una
entrada `SUPERSESIÓN` sin límites estrictos que hubiera permitido
alterar la fecha de última revisión concluida, ausencia de un rol
diferenciado para registrar disparadores y supersesiones, un
tratamiento indiferenciado de la corrección de una propuesta tras
`RECHAZAR`/`BLOQUEAR` que remitía incorrectamente a la sección de
revalidación por disparador, referencias entre entradas basadas en un
identificador aislado en vez de un puntero durable completo, un
registrador que podía transcribir directamente el resultado de su
propia auditoría o decisión sin separación de commits, una afirmación
que trataba el registro desactualizado como fuente suficiente del
estado operacional, y una ausencia de distinción entre la propuesta
raíz de un ciclo y la propuesta exacta efectivamente auditada o
decidida, lo que habría permitido declarar `VIGENTE` sobre una
propuesta distinta de la auditada; una formulación residual que
permitía a Miguel agregar directamente una entrada `DECISIÓN` de
rechazo, sin pasar por el registrador; una regla que permitía a
cualquier agente registrar directamente una hipótesis mediante
`PROPUESTA` sin mandato de proponente autorizado; ausencia de campos
de autor material y de autorización de escritura en cada entrada;
ausencia de una definición verificable de "entrada válida"; y
ausencia de una regla de cabeza global única que previniera
bifurcaciones (forks) documentales del registro—. Todos esos defectos
fueron corregidos en el
propio working tree antes de cualquier `git add` y antes de crear
ningún commit. Ninguna de esas correcciones amplió el alcance de
escritura más allá de las cinco rutas autorizadas, ni ejecutó ciencia,
datos ni validación conductual. Estas revisiones históricas de ChatGPT
**no son un veredicto de Codex** y no sustituyen, en ningún grado, la
auditoría independiente de Codex sobre el commit de implementación,
que sigue pendiente (§15). Los borradores sucesivamente corregidos no
constituyen implementaciones versionadas ni integradas: solo el
contenido final, textualmente cerrado en el momento de esta entrega,
es el que se somete a ese commit y a esa auditoría futura.

**Revisión 10: RECHAZADA PARA COMMIT.** La Revisión 10 de
`governance/core/ADAPTER_REVIEW_POLICY.md` no llegó a versionarse: fue
rechazada antes de cualquier `git add` o commit, por los siguientes
defectos documentales precommit, todos corregidos en esta corrección
localizada (Revisión 11):

- mezcla entre el veredicto formal del auditor y una condición de
  bloqueo operacional del registrador (el registrador "emitía
  `BLOQUEAR`");
- definición incompatible del campo 18 (autorización de escritura),
  tratado como el mismo puntero durable completo usado entre entradas
  del registro;
- cabeza global no determinista (sin una regla exacta y verificable
  para resolverla en un commit dado, y sin tratamiento explícito de
  cero o más de una cabeza);
- encadenamiento incorrecto de `SUPERSESIÓN` (sin ciclo administrativo
  propio, sin distinguir el campo 8 causal del campo 9 global, y
  presentada como hito numerado del ciclo de revalidación de §9-C);
- origen, estado y fecha incompletos en varias entradas (en particular,
  una regla que trataba genéricamente toda `PROPUESTA` como origen de
  `HIPÓTESIS NO VALIDADA`, sin excluir la revalidación);
- vencimiento de 90 días no automático (dependiente, en su
  formulación, de la misma condición de "conocido y verificable" que
  los otros cuatro disparadores);
- secuencia de commits incompleta para correcciones (sin distinguir la
  ruta limpia de seis commits de la ruta con corrección, que exige
  cuatro commits adicionales por cada corrección).

Esta Revisión 11 corrige localizadamente los siete defectos anteriores
sin rediseñar la arquitectura del registro, sin agregar campos, roles
o tipos de entrada nuevos, y sin declarar que la Revisión 10 hubiera
resuelto los defectos de revisiones anteriores a ella.

**Auditoría independiente de Codex sobre el commit de implementación
`309c6b23317da8b1906d4ebcdb6a8507079e2151`: veredicto `RECHAZAR`.**
Codex auditó de forma independiente ese commit —el que contiene la
Revisión 11 de los cinco artefactos, ya versionado— y versionó su
informe en el commit
`786db86cf04b855de6c8f46bba151873e212c9f5`
(`reports/AI-GOV-F1-CANONICAL/AUDIT_CODEX.md`). El veredicto de esa
auditoría es `RECHAZAR`, con la matriz de aceptación marcando `A-04` y
`A-10` como `NO CONFORME` y las dieciséis restantes como `CONFORME`, sin
ningún hallazgo de severidad crítica. Los hallazgos exigidos como
corrección son:

- **H-01 (mayor):** el perfil de Capa B omitía declarar dónde viven los
  mandatos, informes y documentos congelados del proyecto
  (`governance/projects/CLAUDEBOT_PROFILE.md`, contraste con
  `tasks/AI-GOV-F1-CANONICAL/MANDATE.md` §2 y
  `docs/plan_arquitectura_gobernanza_multi_ia_v1.md` §5.2).
- **H-02 (mayor):** la precedencia de Capa A declaraba al núcleo como
  "norma de mayor precedencia" y solo ordenaba Capa A frente a Capa B,
  sin la jerarquía completa de siete niveles
  (`governance/core/INSTITUTIONAL_CORE.md` §4, contraste con
  `docs/plan_arquitectura_gobernanza_multi_ia_v1.md` §4.2).
- **H-03 (mayor):** el núcleo institucional no definía estados de tarea
  ni sus transiciones (`governance/core/INSTITUTIONAL_CORE.md`,
  contraste con `docs/plan_arquitectura_gobernanza_multi_ia_v1.md` §9 y
  `tasks/AI-GOV-F1-CANONICAL/MANDATE.md`).
- **H-04 (mayor):** el primer disparador de revisión sustituía "cambio
  mayor o relevante del modelo" por "cualquier cambio" de modelo,
  versión o revisión, sin evaluación de materialidad
  (`governance/core/ADAPTER_REVIEW_POLICY.md` §7, contraste con
  `tasks/AI-GOV-F1-CANONICAL/MANDATE.md` y
  `docs/plan_arquitectura_gobernanza_multi_ia_v1.md` §7 del mecanismo de
  adaptadores).
- **H-05 (menor):** la política enumeraba seis comprobaciones técnicas
  para permitir `VIGENTE` en §4.3, pero §6 las llamaba "las cinco
  comprobaciones técnicas" (`governance/core/ADAPTER_REVIEW_POLICY.md`
  §4.3 y §6, y este mismo informe).

Esta corrección localizada (Revisión 13) aplica exclusivamente las
cinco correcciones anteriores, sin rediseñar la arquitectura de ninguno
de los cuatro artefactos que autoriza modificar la instrucción
operacional correspondiente, y sin tocar `AGENTS.md`. **No se afirma
que Codex haya emitido `APROBAR` sobre esta corrección ni sobre ningún
commit derivado de ella; los cinco hallazgos anteriores no quedan
declarados institucionalmente cerrados por este informe: su resolución
efectiva solo puede acreditarla una nueva auditoría independiente sobre
el commit corrector que contenga esta Revisión 13, una vez que Miguel
lo autorice y se versione.**

## 15. Estado y próximos pasos

Los tres documentos canónicos permanecen `BORRADOR — NO CONGELADO`.
Este informe no declara, ni puede declarar, `APROBAR` sobre esta
corrección, ni sobre el commit de implementación previamente auditado
y rechazado (`309c6b23317da8b1906d4ebcdb6a8507079e2151`), ni sobre el
futuro commit corrector que la contenga. La auditoría de Codex sobre
ese commit previo ya existe, con veredicto `RECHAZAR`
(`786db86cf04b855de6c8f46bba151873e212c9f5`); esta corrección (Revisión
13) intenta resolver únicamente los hallazgos H-01 a H-05 de esa
auditoría, y **su resolución efectiva no queda declarada ni cerrada
institucionalmente por este informe: solo una nueva auditoría
independiente sobre el futuro commit corrector, con veredicto vigente,
puede acreditarla.** Esa nueva auditoría independiente sigue
pendiente. Los criterios A-18, A-19 y A-21 no forman parte de esta
operación: A-18 y A-19 se evalúan sobre el commit propio del futuro
informe de auditoría una vez que Codex lo versione, y A-21 es el
criterio de cierre de la Fase 1, evaluado en una operación posterior y
separada. Ninguna integración, push, congelación o cierre puede
realizarse sin una nueva decisión expresa y durable de Miguel,
posterior a esa nueva auditoría.

## 16. Procedimiento reproducible de generación del diff sin staging

### 16.1 Revisiones históricas (contexto, no el archivo actual)

- **Revisión 2** usó `git diff --binary -- AGENTS.md` sin
  `--exit-code`, junto con `git diff --no-index --binary -- /dev/null
  <archivo>` para los cuatro archivos nuevos, y produjo
  `diff_implementacion_documental_f1_revision2.txt`.
- **Revisión 3** corrigió una afirmación errónea de la revisión 2 sobre
  los códigos de salida de `git diff` sin `--exit-code`, incorporó
  `--exit-code` para `AGENTS.md`, y produjo
  `diff_implementacion_documental_f1_revision3.txt`.
- **Revisión 4** repitió el mismo procedimiento corregido, después de
  aplicar correcciones adicionales de contenido a los cinco artefactos,
  y produjo `diff_implementacion_documental_f1_revision4.txt`.
- **Revisión 5** repitió el mismo procedimiento, después de exigir
  concurrencia de `APROBAR` para `VIGENTE` y el ciclo completo de
  revalidación en `ADAPTER_REVIEW_POLICY.md`, y produjo
  `diff_implementacion_documental_f1_revision5.txt`.
- **Revisión 6** repitió el mismo procedimiento, después de introducir
  el registro append-only por tipos de entrada en
  `ADAPTER_REVIEW_POLICY.md`, y produjo
  `diff_implementacion_documental_f1_revision6.txt`.
- **Revisión 7** repitió el mismo procedimiento, después de la
  corrección estructural de cierre (esquema de 16 campos, encadenamiento
  global, secuencia de seis commits) en `ADAPTER_REVIEW_POLICY.md`, y
  produjo `diff_implementacion_documental_f1_revision7.txt`.
- **Revisión 8** repitió el mismo procedimiento, después de exigir la
  lectura del estado por el campo 11 independiente del tipo, límites
  estrictos de `SUPERSESIÓN`, el rol de registrador autorizado y los
  dos casos de corrección tras rechazo, en
  `ADAPTER_REVIEW_POLICY.md`, y produjo
  `diff_implementacion_documental_f1_revision8.txt`.
- **Revisión 9** repitió el mismo procedimiento, después de la
  corrección de separación funcional (auditor/informe/registro,
  Miguel/decisión/registro, propuesta raíz frente a propuesta exacta)
  en `ADAPTER_REVIEW_POLICY.md`, y produjo
  `diff_implementacion_documental_f1_revision9.txt`.
- **Revisión 10** repitió el mismo procedimiento, después de la
  corrección de integridad del registro (autor material, autorización
  de escritura, entrada válida, cabeza global única) en
  `ADAPTER_REVIEW_POLICY.md`, y produjo
  `diff_implementacion_documental_f1_revision10.txt`. **Esta revisión
  fue RECHAZADA PARA COMMIT** (§14) por siete defectos documentales
  precommit, todos corregidos en la presente corrección localizada.

- **Revisión 11** corrigió localizadamente los siete defectos que
  rechazaron la Revisión 10 (§14), produjo
  `diff_implementacion_documental_f1_revision11.txt`, y fue la revisión
  efectivamente versionada en el commit
  `309c6b23317da8b1906d4ebcdb6a8507079e2151` ("docs: implementa
  gobernanza multi-IA fase 1"). Ese commit fue auditado de forma
  independiente por Codex
  (`786db86cf04b855de6c8f46bba151873e212c9f5`), con veredicto
  `RECHAZAR` y los hallazgos H-01 a H-05 (§14).
- **Revisión 12** fue el primer intento de corrección de los hallazgos
  H-01 a H-05 sobre el commit rechazado
  `309c6b23317da8b1906d4ebcdb6a8507079e2151`, y produjo
  `diff_implementacion_documental_f1_revision12.txt`. **Fue rechazada
  antes del commit**, únicamente por tres correcciones documentales
  localizadas y una corrección del informe: H-01 y H-03 quedaron
  incompletos, H-02 quedó parcialmente implementado, y el informe
  contenía un conteo incorrecto de criterios conformes en la matriz de
  aceptación de la auditoría de Codex (§14). Se menciona aquí
  únicamente como historial.
- **Revisión 13** es la corrección localizada actual, que completa los
  pendientes de la Revisión 12 —rutas y artefactos propios del proyecto
  (H-01), precedencia completa (H-02) y estados y transiciones de tarea
  (H-03)— y conserva sin cambios, byte a byte, la corrección de H-04 y
  H-05 ya aplicada en `governance/core/ADAPTER_REVIEW_POLICY.md` desde
  la Revisión 12, además de corregir el conteo de criterios conformes
  en este informe (§14). Al igual que la Revisión 12, no se genera
  contra un árbol de trabajo sin commit previo del mismo contenido: se
  genera mediante `git diff` contra el commit exacto ya versionado y
  rechazado, conforme a §16.2.

Ninguno de esos once archivos anteriores (revisiones 2 a 12) es el
producido por esta corrección actual (Revisión 13). Se mencionan aquí
únicamente como historial.

### 16.2 Procedimiento actual (Revisión 13)

A diferencia de las revisiones 2 a 11, los cuatro artefactos de esta
corrección (`governance/core/INSTITUTIONAL_CORE.md`,
`governance/core/ADAPTER_REVIEW_POLICY.md`,
`governance/projects/CLAUDEBOT_PROFILE.md` y este propio informe) ya
existen, sin excepción, en el commit rechazado
`309c6b23317da8b1906d4ebcdb6a8507079e2151`: ninguno de los cuatro es un
archivo nuevo en esta corrección, por lo que no aplica el patrón
`git diff --no-index -- /dev/null <archivo>` usado en las revisiones
anteriores para archivos todavía no rastreados. En su lugar, el diff se
genera comparando el árbol de trabajo actual directamente contra ese
commit exacto, ya versionado:

```text
out="$(xdg-user-dir DOWNLOAD)/diff_implementacion_documental_f1_revision13.txt"
git diff --exit-code --binary \
  309c6b23317da8b1906d4ebcdb6a8507079e2151 \
  -- \
  governance/core/INSTITUTIONAL_CORE.md \
  governance/core/ADAPTER_REVIEW_POLICY.md \
  governance/projects/CLAUDEBOT_PROFILE.md \
  reports/AI-GOV-F1-CANONICAL/IMPLEMENTATION_REPORT.md \
  > "$out"
codigo_diff=$?
```

`git diff --exit-code <commit> -- <rutas>` compara el árbol de trabajo
actual contra el commit exacto indicado, sin tocar el índice y sin
ejecutar `git add`; con `--exit-code`, termina en `1` porque existen
diferencias (las cinco correcciones H-01 a H-05) y terminaría en `0`
si no existiera ninguna. El código obligatorio y esperado aquí es `1`.
Este comando no requiere el patrón `/dev/null` de las revisiones
anteriores porque ninguno de los cuatro archivos es nuevo respecto del
commit citado.

### 16.3 Limitación temporal y archivo actual

Existe la misma limitación temporal que en las revisiones anteriores:
el diff definitivo solo puede generarse contra el contenido
textualmente final de los cuatro artefactos autorizados, y este informe
es uno de ellos. Por eso este informe registra, en §16.2, el
procedimiento exacto, la ruta de salida y el código de salida esperado
(`1`) —no puede registrar, dentro de sí mismo, el código real que
resulte de ejecutar ese procedimiento sobre su propio contenido ya
cerrado, porque generarlo exige que el informe deje de editarse
primero. El código real de la generación definitiva se informa en la
entrega de Sonnet al final de esta corrección, fuera del texto de este
informe.

Ruta registrada para el diff de la Revisión 13:
`diff_implementacion_documental_f1_revision13.txt`, en
`$(xdg-user-dir DOWNLOAD)`.

**Nota sobre la entrega definitiva de esta operación.** Esta misma
corrección localizada, después de generado ese diff de la Revisión 13,
recibió dos ajustes adicionales estrictamente localizados: una regla
de evidencia durable para reanudar `BLOQUEADA` o `DETENIDA POR
INCIDENTE` en `governance/core/INSTITUTIONAL_CORE.md` §12.1, y la
corrección de las referencias de este propio informe que identificaban
incorrectamente como "Revisión 12" contenido que en realidad
corresponde a la Revisión 13 (§16.1). Por ello, el diff que acredita el
contenido textualmente final y completo de esta operación no es el de
la Revisión 13, sino el de la **Revisión 14**, generado con el mismo
procedimiento de §16.2 contra el mismo commit exacto
(`309c6b23317da8b1906d4ebcdb6a8507079e2151`), en
`diff_implementacion_documental_f1_revision14.txt`, dentro de
`$(xdg-user-dir DOWNLOAD)`. Después de generar ese diff definitivo de
la Revisión 14, no se vuelve a editar ningún artefacto de esta
operación.
