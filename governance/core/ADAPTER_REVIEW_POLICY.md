# ADAPTER_REVIEW_POLICY.md — Política de revisión de adaptadores (Capa A)

**Estado: BORRADOR — NO CONGELADO.**

## 1. Propósito y alcance

Define el mecanismo documental obligatorio para proponer, registrar,
auditar y decidir sobre cualquier adaptador específico de modelo
(Capa D) dentro de este marco de gobernanza. Esta política es
agnóstica de proveedor y de proyecto. Esta fase no crea ningún
adaptador, ninguna carpeta `adapters/` ni ningún registro operativo:
define exclusivamente el mecanismo que regirá su creación futura.

## 2. Ubicación exacta del registro

- `adapters/ADAPTER_REGISTRY.md` es la **única fuente documental
  durable** del historial de revisión de adaptadores y de los estados
  formalmente registrados, con ruta exacta fijada; no se crea en esta
  fase.
- El registro central, cuando exista, es un **registro append-only**
  (§3): contiene una entrada por cada evento documental de cada
  adaptador.
- Que el registro sea la única fuente **documental** durable no
  significa que su última entrada agregada sea, por sí sola y en todo
  momento, prueba suficiente del **estado operacional** real (§9).
- Mientras `adapters/` no exista, ningún agente crea el registro
  central por iniciativa propia; su creación exige el mandato que
  autorice el primer adaptador.

## 3. Naturaleza append-only, esquema común, entrada válida y cabeza global única

El registro central es **estrictamente append-only**. Ninguna entrada
ya versionada cambia, se completa, se actualiza, "pasa de `PENDIENTE`"
a otro valor, ni ve reemplazado uno de sus campos. Cada entrada es una
**fotografía inmutable**.

### 3.1 Esquema común de toda entrada

Toda entrada, sin excepción y sea cual sea su tipo, declara como
mínimo estos dieciocho campos:

1. identificador estable del adaptador;
2. modelo y versión o revisión objetivo;
3. identificador único del ciclo de revisión;
4. identificador único de esta entrada;
5. tipo de entrada: `PROPUESTA`, `AUDITORÍA`, `DECISIÓN`, `DISPARADOR`
   o `SUPERSESIÓN`;
6. fecha de la entrada;
7. evento u origen: `CREACIÓN INICIAL`; uno de los cinco disparadores
   exactos de §7; `CORRECCIÓN`; `REVALIDACIÓN`; `DECISIÓN`;
   `SUPERSESIÓN`;
8. **entrada causal anterior**, dentro del mismo ciclo: puntero
   durable completo al hito causal que motivó esta entrada (la
   `PROPUESTA` que audita una `AUDITORÍA`, la `AUDITORÍA` sobre la que
   decide una `DECISIÓN`, la `DECISIÓN` `VIGENTE` que activa un
   `DISPARADOR`), o `NO APLICA` cuando esta política lo autorice
   expresamente;
9. **entrada precedente global**: puntero durable completo a la
   **cabeza global única real** del adaptador (§3.3) en el commit base
   exacto de la operación, o `NO APLICA` únicamente para la primera
   entrada histórica de ese adaptador. El campo 8 y el campo 9 **pueden
   coincidir, pero no están obligados a coincidir**: si existe una
   `SUPERSESIÓN` administrativa intermedia (§4.5), el campo 8 conserva
   el hito causal y el campo 9 apunta a esa `SUPERSESIÓN`, que es la
   cabeza global real en ese momento;
10. entrada supersedida, cuando corresponda: puntero durable completo,
    o `NO APLICA`;
11. estado operativo o constancia declarada: `VIGENTE`,
    `REVISIÓN REQUERIDA`, `HIPÓTESIS NO VALIDADA` o
    `NO APLICA — PROPUESTA RECHAZADA` (§6);
12. fecha de última revisión concluida (§9);
13. evidencia Git: repositorio, commit completo y ruta literal del
    contenido que esta entrada certifica;
14. responsable de la propuesta;
15. auditoría: identidad del auditor, commit completo, ruta literal de
    su informe y veredicto exacto; o `PENDIENTE`;
16. decisión de Miguel: fecha, commit completo y ruta literal de la
    entrada durable en `decisions/OWNER_DECISIONS.md`; o `PENDIENTE`;
17. **autor material de la entrada**: identidad exacta de quien la
    agregó, y el rol bajo el cual actuó — exactamente uno de:
    `PROPONENTE AUTORIZADO` o `REGISTRADOR AUTORIZADO`;
18. **autorización de escritura**: **referencia durable de
    autorización de escritura** (estructura distinta del puntero
    durable completo, ver más abajo) a la fuente que autorizó
    materialmente esta escritura.

Además, toda entrada de `AUDITORÍA` y de `DECISIÓN` declara dos campos
adicionales obligatorios (§4.2, §4.3):

19. **propuesta raíz del ciclo**: puntero durable completo a la
    primera entrada de `PROPUESTA` del ciclo (campo 3); se conserva
    para reconstruir la historia, sin demostrar por sí sola qué
    versión fue auditada o decidida;
20. **propuesta exacta evaluada o decidida**: puntero durable completo
    a la entrada de `PROPUESTA` que contiene la versión exacta
    sometida a la auditoría o a la decisión que esta entrada
    documenta; coincide con la raíz cuando no hubo corrección, y debe
    ser distinta cuando sí la hubo.

**Reglas sobre los campos 17-18:**

- ninguna entrada es válida (§3.2) si carece de los campos 17 y 18;
- el acceso técnico al repositorio **no reemplaza** el campo 18: una
  autorización de escritura exige mandato expreso y permiso literal;
- la autorización citada en el campo 18 debe existir **antes** del
  commit que agrega la entrada; no se permite una referencia al mismo
  commit que crea la entrada;
- una autorización para un tipo de entrada **no se reutiliza** para un
  tipo de entrada no mencionado por ella;
- el autor material **no puede autodesignarse ni autoautorizarse**;
- para `PROPUESTA`, el autor material es el **proponente autorizado**
  (§4.1, §5); para `AUDITORÍA`, `DECISIÓN`, `DISPARADOR` y
  `SUPERSESIÓN`, el autor material es el **registrador autorizado**
  (§4.2-§4.5, §5). El auditor sigue identificado en el campo 15, pero
  no es el autor material de la entrada de `AUDITORÍA`; Miguel sigue
  identificado en el campo 16, pero no es el autor material de la
  entrada de `DECISIÓN`.

Esta política define **dos estructuras de referencia distintas**, que
no se confunden entre sí:

**A. Puntero durable completo entre entradas** (aplicable
exclusivamente a los campos 8, 9, 10, 19 y 20): cinco datos juntos —
repositorio; commit completo preexistente; ruta literal
`adapters/ADAPTER_REGISTRY.md`; identificador estable del adaptador; e
identificador exacto de la entrada referenciada—, nunca un
identificador aislado, una rama, `HEAD`, `main`, un tag móvil ni un
hash abreviado.

**B. Referencia durable de autorización de escritura** (aplicable
exclusivamente al campo 18): seis datos juntos — repositorio; commit
completo preexistente; ruta literal del mandato o decisión que
autoriza; identificador de la tarea o mandato; la ruta literal
autorizada (`adapters/ADAPTER_REGISTRY.md`); y el tipo o los tipos de
entrada que esa autorización permite agregar. Esta referencia **no
exige** identificador estable del adaptador ni identificador de
entrada del registro: autoriza una escritura, no apunta a una entrada
ya existente del registro.

En ambas estructuras, el commit citado debe existir antes del commit
que agrega la entrada que lo cita (§10), y `NO APLICA` se permite
únicamente en los casos que esta política autoriza expresamente.

`PENDIENTE` (campos 15 y 16) no es un estado institucional.
`NO APLICA — PROPUESTA RECHAZADA` (campo 11) no es un cuarto estado
institucional (§6). Todo valor heredado debe **repetirse
expresamente**.

### 3.2 Definición de entrada válida

Una entrada es **válida** únicamente cuando concurren, todos a la vez:

1. contiene todos los campos comunes (§3.1) y los específicos
   aplicables a su tipo (§4);
2. su autor material (campo 17) está identificado;
3. su autorización de escritura (campo 18) existe, es previa al
   commit que agrega la entrada, y permite expresamente ese tipo de
   entrada;
4. todos sus punteros durables completos resuelven a commits y a
   entradas **preexistentes**;
5. no contiene ninguna autorreferencia Git (§10): ningún puntero cita
   el commit que simultáneamente crea la propia entrada;
6. **cuando su entrada precedente global (campo 9) no es `NO APLICA`**,
   esa referencia era la **cabeza global única** (§3.3) del adaptador
   en el commit base exacto fijado para la operación. Se exceptúa
   expresamente la primera entrada de `PROPUESTA` histórica de un
   adaptador, cuyo campo 9 es `NO APLICA` conforme a §3.3 y §4.1;
7. cumple las reglas particulares de su tipo (§4);
8. fue versionada sin tocar rutas no autorizadas.

Una entrada **incompleta, no autorizada, autorreferente o con
punteros incoherentes no puede determinar estado**: no cuenta para
efectos de §6, aunque permanezca en el historial como intento
documentado. Esta invalidez es una **condición operacional de
bloqueo**, no el veredicto institucional `BLOQUEAR`: ese veredicto
formal solo puede emitirlo el auditor independiente (§12). Ante una
entrada que no satisface este §3.2, el autor material se detiene, no
la agrega y reporta la condición para que se resuelva mediante la
corrección o la auditoría que corresponda (§5).

Una entrada de `DECISIÓN` o de `SUPERSESIÓN` posterior puede
reemplazar, rechazar o superseder los efectos **hacia adelante** de
una entrada anterior sin invalidar retroactivamente esa entrada
histórica: la entrada anterior permanece válida como lo que certificó
en su momento, conforme a `governance/core/INSTITUTIONAL_CORE.md` §8.

### 3.3 Cabeza global única y prevención de forks

**Definición determinista:** en un commit exacto del registro, la
**cabeza global** de un adaptador es la única entrada válida de ese
adaptador que no aparece referenciada en el campo 9 de ninguna otra
entrada válida del mismo adaptador presente en ese mismo commit.

- **Exactamente una cabeza:** cadena válida para lectura del estado
  (§3.2, §6).
- **Cero cabezas:** la cadena está cerrada circularmente o corrupta;
  condición operacional de bloqueo.
- **Más de una cabeza:** existe una bifurcación; condición operacional
  de bloqueo.
- El orden visual del documento y las fechas de las entradas **no
  resuelven** cuál es la cabeza: solo la definición determinista
  anterior la resuelve.

- **Lectura del estado documental actual:** se obtiene exclusivamente
  del **campo 11** de la **cabeza global única, válida y no
  supersedida** del adaptador — no simplemente "la última entrada que
  aparece en el archivo" — cualquiera sea el tipo de esa entrada.
- Antes de agregar cualquier entrada que no sea la primera histórica
  del adaptador, el autor material debe: (1) fijar el **commit base
  exacto** autorizado para la operación; (2) verificar, en ese commit,
  cuál es la cabeza global única, válida y no supersedida del
  adaptador; (3) usar exactamente esa entrada como campo 9, mediante
  puntero durable completo; (4) **inmediatamente antes** de crear el
  commit que agrega la nueva entrada, verificar de nuevo que esa cabeza
  no cambió y que no apareció una entrada competidora.
- Solo la primera entrada de `PROPUESTA` histórica de un adaptador
  puede usar `NO APLICA` como entrada precedente global.
- Quedan prohibidos: que dos entradas nuevas declaren simultáneamente
  el mismo precedente global como cabeza sin encadenarse entre ellas;
  escoger una rama documental por orden visual; resolver un fork
  usando "la última línea", una fecha, `HEAD`, `main`, el nombre de
  una rama o un hash abreviado; e integrar una entrada cuyo precedente
  dejó de ser la cabeza global única antes del commit que la agrega.
- **Si existen dos o más cabezas globales no supersedidas** para un
  mismo adaptador: el estado documental se considera **ambiguo**;
  ningún estado `VIGENTE` puede invocarse; corresponde una **condición
  operacional de bloqueo** y operar fail-closed; no se usa una
  `SUPERSESIÓN` ordinaria para resolver la bifurcación; la
  recuperación exige mandato específico, auditoría independiente y
  decisión durable de Miguel, todo ello fuera del flujo ordinario de
  esta política.

## 4. Flujo de entradas por tipo

### 4.1 Entrada de `PROPUESTA`

- Cualquier agente puede **identificar y reportar** una posible
  mejora, ajuste o hipótesis de adaptador. Reportarla **no concede
  permiso de escritura** sobre el registro.
- Solo un **proponente autorizado** mediante mandato expreso, con
  permiso literal para (a) versionar el artefacto propuesto y (b)
  agregar la entrada de `PROPUESTA` en `adapters/ADAPTER_REGISTRY.md`,
  puede materializar esa hipótesis en el registro. Ninguna capacidad
  técnica, observación o iniciativa propia sustituye ese mandato. Sin
  proponente autorizado, la hipótesis permanece reportada, pero **no
  registrada** como entrada institucional (§8).
- Se agrega después de que el adaptador propuesto exista en un commit
  identificable; cita el commit completo y la ruta literal de ese
  adaptador (campo 13). Autor material (campo 17) = proponente
  autorizado; autorización de escritura (campo 18) = el mandato que lo
  designó, con permiso literal para `PROPUESTA`.
- **Propuesta inicial** (primera del adaptador; propuesta raíz de su
  ciclo): evento/origen = `CREACIÓN INICIAL`; entrada anterior del
  mismo ciclo = `NO APLICA`; entrada precedente global = `NO APLICA`
  (única entrada que puede usarlo, §3.3); estado declarado =
  `HIPÓTESIS NO VALIDADA`; fecha de última revisión concluida =
  `NO APLICA — SIN REVISIÓN CONCLUIDA`.
- **Propuesta de revalidación** (tras `DISPARADOR`, §9-C; propuesta
  raíz de su ciclo nuevo): evento/origen = `REVALIDACIÓN`; entrada
  anterior del mismo ciclo = `NO APLICA`; entrada precedente global =
  puntero durable completo a la entrada de `DISPARADOR` que dejó
  `REVISIÓN REQUERIDA` (verificada como cabeza global única, §3.3);
  estado declarado = `REVISIÓN REQUERIDA`; fecha de última revisión
  concluida heredada sin recalcular.
- **Propuesta corregida dentro del mismo ciclo** (Caso A, §6.2): no
  abre ciclo nuevo; pasa a ser la propuesta exacta (campo 20) de ese
  ciclo, conservando la raíz (campo 19). Evento/origen = `CORRECCIÓN`;
  entrada causal anterior (campo 8) = puntero durable completo a la
  entrada de `AUDITORÍA` que emitió `RECHAZAR`/`BLOQUEAR`; entrada
  precedente global (campo 9) = la cabeza global única real (coincide
  con el campo 8 salvo `SUPERSESIÓN` administrativa intermedia).
  **Conserva el estado y la fecha de última revisión concluida del
  ciclo**: `HIPÓTESIS NO VALIDADA` y `NO APLICA — SIN REVISIÓN
  CONCLUIDA` si el ciclo es de activación inicial; `REVISIÓN
  REQUERIDA` y la fecha heredada sin recalcular si el ciclo es de
  revalidación. No remite a §9.
- **Propuesta posterior a una `DECISIÓN` de rechazo ya registrada**
  (Caso B, §6.2): abre ciclo nuevo, con su propio identificador de
  ciclo, del cual es la nueva propuesta raíz. Evento/origen =
  `CORRECCIÓN`; entrada causal anterior (campo 8) = `NO APLICA`;
  entrada precedente global (campo 9) = puntero durable completo a la
  cabeza global única real, que es la entrada de `DECISIÓN` de
  rechazo (salvo `SUPERSESIÓN` administrativa intermedia). Si el
  ciclo rechazado era una **activación inicial**: estado declarado =
  `HIPÓTESIS NO VALIDADA`; fecha de última revisión concluida =
  `NO APLICA — SIN REVISIÓN CONCLUIDA`. Si el ciclo rechazado era una
  **reactivación**: estado declarado = `REVISIÓN REQUERIDA`; fecha de
  última revisión concluida = la fecha histórica anterior, heredada y
  repetida expresamente.
- En los cuatro casos: auditor = `PENDIENTE`; decisión de Miguel =
  `PENDIENTE`.

### 4.2 Entrada de `AUDITORÍA`

- El **auditor independiente** revisa la propuesta exacta, produce su
  propio **informe independiente**, separado, y lo versiona
  exclusivamente en un commit propio. Antes de ser versionado, ese
  informe debe contener: repositorio del adaptador; commit completo
  del artefacto exacto auditado; ruta literal del artefacto; puntero
  durable completo a la propuesta raíz; puntero durable completo a la
  propuesta exacta evaluada; identificador del ciclo; veredicto exacto
  (`APROBAR`, `RECHAZAR` o `BLOQUEAR`); y hallazgos con severidades.
- El auditor **no modifica** `adapters/ADAPTER_REGISTRY.md`, **no
  agrega directamente** la entrada de `AUDITORÍA`, y no puede
  registrar el resultado de su propia auditoría dentro del mismo
  ciclo.
- Después de que ese informe exista en su commit completo, el
  **registrador autorizado** agrega la entrada de `AUDITORÍA`,
  **transcribiendo de forma exacta y no discrecional** los datos
  anteriores. **Si el informe no contiene esos datos, o presenta
  discordancias entre ellos, el registrador no puede inferirlos ni
  completarlos: se detiene, no agrega la entrada de `AUDITORÍA`,
  reporta la condición operacional de bloqueo, y solicita la
  corrección del informe o una nueva auditoría, según corresponda
  (§5). El registrador nunca convierte ese reporte en un veredicto
  propio: el único veredicto formal `BLOQUEAR` lo emite exclusivamente
  el auditor independiente (§12).**
- Autor material (campo 17) = registrador autorizado; autorización de
  escritura (campo 18) = el mandato del registrador, con permiso
  literal para `AUDITORÍA`.
- **Entrada causal anterior (campo 8)**: puntero durable completo a la
  entrada de `PROPUESTA` que contiene la propuesta exacta auditada.
  **Entrada precedente global (campo 9)**: puntero durable completo a
  la cabeza global única real del adaptador en el commit base exacto
  de la operación (§3.3); coincide con el campo 8 salvo que exista una
  `SUPERSESIÓN` administrativa intermedia (§4.5, §3.1).
- Evento/origen: el mismo que declaró la entrada de `PROPUESTA`
  referenciada por el campo 8 (`CREACIÓN INICIAL`, `REVALIDACIÓN` o
  `CORRECCIÓN`), repetido expresamente, no heredado por inferencia.
- Mantiene `PENDIENTE` la decisión de Miguel, y repite expresamente,
  sin cambiarlo, el estado y la fecha de última revisión concluida
  declarados por esa `PROPUESTA` (§6, §6.1): esta entrada no activa ni
  reactiva ningún adaptador.

### 4.3 Entrada de `DECISIÓN`

- **Miguel**, en su rol de propietario y autoridad final, emite la
  decisión final y la **registra de forma durable** en
  `decisions/OWNER_DECISIONS.md`. Antes de ser versionada, esa
  decisión durable debe identificar: puntero durable completo a la
  propuesta raíz; puntero durable completo a la propuesta exacta sobre
  la cual decide; puntero durable completo a la entrada de `AUDITORÍA`
  correspondiente; commit completo y ruta literal del informe
  independiente; el resultado exacto autorizado —`ACTIVAR`,
  `REACTIVAR` o `RECHAZAR`—; y la fecha de la decisión. Miguel **no
  modifica** `adapters/ADAPTER_REGISTRY.md` bajo ninguna forma: ni
  siquiera para registrar directamente un rechazo.
- **Si la decisión durable no identifica esos objetos exactos, el
  registrador no puede elegirlos, completarlos ni inferirlos: se
  detiene, no agrega la entrada de `DECISIÓN`, reporta la condición
  operacional de bloqueo, y solicita a Miguel la decisión durable
  completa que corresponda (§5). El registrador nunca convierte ese
  reporte en un veredicto propio.**
- Después de que la decisión durable exista en su commit completo, el
  **registrador autorizado** agrega la entrada de `DECISIÓN`,
  **transcribiéndola exactamente**. El registrador no decide por
  Miguel y no puede alterar alcance, resultado, estado autorizado,
  fecha, propuesta ni auditoría citada.
- Autor material (campo 17) = registrador autorizado; autorización de
  escritura (campo 18) = el mandato del registrador, con permiso
  literal para `DECISIÓN`.
- **Entrada causal anterior (campo 8)**: puntero durable completo a la
  entrada de `AUDITORÍA` exacta sobre la cual se decide. **Entrada
  precedente global (campo 9)**: puntero durable completo a la cabeza
  global única real del adaptador en el commit base exacto de la
  operación (§3.3); coincide con el campo 8 salvo `SUPERSESIÓN`
  administrativa intermedia (§4.5, §3.1).
- Evento/origen: `DECISIÓN`.
- **El campo 13 (evidencia Git) de esta entrada debe citar el mismo
  artefacto exacto que**: la `PROPUESTA` exacta; el informe del
  auditor; la entrada de `AUDITORÍA`; y la decisión durable de Miguel.
  **Cualquier diferencia entre esos cuatro objetos es una condición
  operacional de bloqueo** (el registrador se detiene y no agrega la
  entrada, conforme al procedimiento de §5), y no permite `VIGENTE`.
- Registra `VIGENTE` (campo 11) **únicamente** si concurren, sin
  discordancia: (1) la entrada de `AUDITORÍA` referenciada apunta a la
  misma propuesta exacta que esta `DECISIÓN`; (2) esa `AUDITORÍA`
  tiene veredicto exacto `APROBAR`; (3) el commit del artefacto citado
  coincide con el objeto efectivamente auditado; (4) no existe una
  propuesta corregida posterior de ese ciclo pendiente de nueva
  auditoría; (5) no existe ningún hallazgo crítico abierto; y (6) la
  decisión durable de Miguel identificada en el punto anterior
  autoriza exactamente `ACTIVAR` o `REACTIVAR` esa misma propuesta
  exacta. **Cualquier discordancia es una condición operacional de
  bloqueo y no permite `VIGENTE`.** Si el resultado autorizado es
  `ACTIVAR` o `REACTIVAR`, la fecha de última revisión concluida es la
  fecha de esta misma decisión durable de Miguel.
- Registra `NO APLICA — PROPUESTA RECHAZADA` (campo 11) cuando la
  decisión durable de Miguel identificada es `RECHAZAR`, con
  independencia de cuál haya sido el veredicto del auditor (§6.2). En
  ese caso, la fecha de última revisión concluida es
  `NO APLICA — SIN REVISIÓN CONCLUIDA` si el ciclo rechazado era una
  propuesta inicial, o la fecha heredada y repetida expresamente de la
  última entrada `VIGENTE` anterior, conservada exclusivamente como
  dato histórico, si el rechazo corresponde a una reactivación.

### 4.4 Entrada de `DISPARADOR`

- Se agrega, exclusivamente por el **registrador autorizado**, cuando
  alguno de los cuatro primeros eventos de §7 es conocido y
  verificable, o automáticamente al cumplirse el plazo de 90 días del
  quinto evento (§7, punto 5; §9-A), para un adaptador `VIGENTE`.
  Autor material = registrador autorizado; autorización de escritura =
  su mandato con permiso literal para `DISPARADOR`.
- **Entrada causal anterior (campo 8)**: puntero durable completo a la
  entrada de `DECISIÓN` que registró ese `VIGENTE`. **Entrada
  precedente global (campo 9)**: puntero durable completo a la cabeza
  global única real del adaptador en el commit base exacto de la
  operación (§3.3); coincide con el campo 8 salvo `SUPERSESIÓN`
  administrativa intermedia (§4.5, §3.1).
- Evento/origen: el disparador exacto de §7 que ocurrió, citado
  literalmente (incluido "cumplimiento de 90 días" cuando corresponda).
  Registra `REVISIÓN REQUERIDA`; no modifica ni borra la entrada
  `VIGENTE` histórica; conserva, repetida expresamente, la fecha de
  última revisión concluida.
- Debe agregarse lo antes posible una vez ocurrido el disparador
  (§9-B); su ausencia o demora no preserva el uso del adaptador
  (§9-A).

### 4.5 Entrada de `SUPERSESIÓN`

- Se usa **exclusivamente**, por el **registrador autorizado**, para
  corregir defectos documentales **no sustantivos** de una entrada
  histórica, dejándola sin efecto hacia adelante sin reescribirla
  nunca. Es una **operación administrativa separada**, distinta del
  ciclo sustantivo de propuesta/auditoría/decisión: no es un hito
  obligatorio de ese ciclo (§9-C).
- **Abre su propio ciclo administrativo**, con un **identificador de
  ciclo nuevo**, distinto del ciclo de la entrada que corrige. Autor
  material = registrador autorizado; autorización de escritura = su
  mandato con permiso literal para `SUPERSESIÓN`.
- Evento/origen (campo 7): `SUPERSESIÓN`.
- **Entrada causal anterior (campo 8)**: `NO APLICA` (una
  `SUPERSESIÓN` no tiene hito causal dentro de un ciclo sustantivo).
- **Entrada precedente global (campo 9)**: puntero durable completo a
  la cabeza global única real del adaptador en el commit base exacto
  de la operación (§3.3).
- **Entrada supersedida (campo 10)**: puntero durable completo a la
  entrada histórica concreta que se deja sin efecto hacia adelante.
  Esta entrada **no necesita ser la cabeza global**: puede ser
  cualquier entrada anterior del historial del adaptador.
- **Debe repetir expresamente**, sin alterarlos, el campo 11 (estado o
  constancia) y la fecha de última revisión concluida de la entrada
  precedente global (campo 9) — no necesariamente los de la entrada
  supersedida (campo 10), si esta última no es la cabeza global. No
  origina ninguno de los cuatro resultados de §6.1.
- Puede corregir **únicamente** datos descriptivos no sustantivos
  (por ejemplo, un error ortográfico o de formato). **No puede, por sí
  sola, cambiar**: la propuesta; el artefacto; la auditoría; el
  veredicto; la decisión; el estado (campo 11); el modelo o la versión
  objetivo; ni la fecha de última revisión concluida; tampoco puede
  reiniciar ni extender el plazo de 90 días, reemplazar evidencia
  sustantiva, ni activar, reactivar, rechazar o revocar un adaptador.
- Cuando el defecto es sustantivo, no se usa `SUPERSESIÓN`: se trata
  fail-closed mediante el flujo ordinario de §4.1–§4.3 (o §9).

## 5. Responsables y separación de funciones

- **Proponente autorizado:** único rol habilitado para agregar la
  entrada de `PROPUESTA` (§4.1), mediante mandato expreso con permiso
  literal para versionar el artefacto y para escribir esa entrada. No
  audita su propia propuesta. Reportar una hipótesis no concede este
  rol (§8).
- **Auditor independiente:** distinto del proponente; revisa la
  propuesta exacta, produce su informe independiente con los punteros
  exigidos por §4.2, lo versiona en un commit propio y emite
  `APROBAR`, `RECHAZAR` o `BLOQUEAR`. **No modifica**
  `adapters/ADAPTER_REGISTRY.md`, no agrega la entrada de `AUDITORÍA`,
  y no puede registrar el resultado de su propia auditoría dentro del
  mismo ciclo.
- **Miguel, en su rol de propietario y autoridad final:** única
  autoridad para emitir la decisión de `ACTIVAR`, `REACTIVAR` o
  `RECHAZAR`, registrada de forma durable con los punteros exigidos
  por §4.3 en `decisions/OWNER_DECISIONS.md`. **No modifica**
  `adapters/ADAPTER_REGISTRY.md` bajo ninguna forma, incluido un
  rechazo.
- **Registrador autorizado:** único rol habilitado para agregar
  entradas de `AUDITORÍA`, `DECISIÓN`, `DISPARADOR` y `SUPERSESIÓN`.
  Reglas:
  - solo una persona o agente **expresamente designado mediante
    mandato**, con permiso literal de escritura sobre
    `adapters/ADAPTER_REGISTRY.md` para el tipo de entrada concreto,
    puede ejercerlo; el acceso técnico no concede el rol; nadie se
    autodesigna ni se autoautoriza;
  - **materializa hechos ya existentes, durables y citables**: no
    dictamina veredictos, no decide activaciones/reactivaciones/
    rechazos, y transcribe sin reinterpretar, sin corregir y sin
    agregar reservas inexistentes;
  - **el registrador nunca emite el veredicto formal `BLOQUEAR`: ese
    veredicto es exclusivo del auditor independiente (§12).** Ante
    datos faltantes, discordantes o ambiguos en el informe del auditor
    o en la decisión durable de Miguel (§4.2, §4.3), o ante una
    bifurcación de cabeza global (§3.3), el registrador: (1) se
    detiene; (2) no agrega la entrada; (3) reporta una **condición
    operacional de bloqueo**; y (4) solicita la corrección, la nueva
    auditoría o la decisión durable que corresponda. El registrador no
    completa, no infiere y no elige por cuenta propia ningún dato
    faltante, y nunca convierte ese reporte en un veredicto propio;
  - antes de agregar cualquier entrada que no sea la primera histórica,
    verifica la cabeza global única del adaptador conforme a §3.3;
  - una `SUPERSESIÓN` agregada por el registrador está sujeta, sin
    excepción, a los límites de §4.5.

Los únicos veredictos institucionales siguen siendo `APROBAR`,
`RECHAZAR` y `BLOQUEAR` (§12), y solo el auditor independiente puede
emitirlos. En síntesis: solo el auditor emite el veredicto; solo
Miguel decide; el registrador únicamente materializa, verifica y, ante
cualquier dato faltante, discordante o ambiguo (incluida una
bifurcación de cabeza global), se detiene y reporta la condición
operacional de bloqueo en vez de completar por iniciativa propia.

## 6. Estados institucionales

Los únicos tres estados institucionales válidos de un adaptador son
disjuntos entre sí. El estado documental actual se determina
exclusivamente por el **campo 11** de la **cabeza global única,
válida y no supersedida** del adaptador (§3.2, §3.3), cualquiera sea
su tipo.

- **`VIGENTE`** se declara **únicamente** cuando concurren, todos a la
  vez: el campo 11 de la cabeza global única declara `VIGENTE`; existe
  una propuesta exacta identificada; existe una entrada de
  `AUDITORÍA` independiente sobre esa misma propuesta exacta; el
  veredicto exacto de esa auditoría es `APROBAR`; no existen
  hallazgos críticos abiertos; no existe una propuesta posterior de
  ese ciclo pendiente; existe una **decisión previa, expresa y
  durable de Miguel** que autoriza exactamente `ACTIVAR` o
  `REACTIVAR` esa misma propuesta exacta; y la entrada de `DECISIÓN`
  fue agregada posteriormente por un registrador autorizado y
  transcribe, sin discordancia, esa decisión (§4.3). **Las seis
  comprobaciones técnicas de §4.3 no sustituyen la decisión durable de
  Miguel**: ambas son necesarias conjuntamente.
- **`REVISIÓN REQUERIDA`** — el campo 11 de la cabeza global única
  declara `REVISIÓN REQUERIDA`, **o** existe un disparador de §7
  todavía pendiente de registro: alguno de los cuatro primeros
  eventos, conocido y verificable, o el cumplimiento automático de 90
  días del quinto evento, que no depende de que un agente lo advierta
  (§7 punto 5, §9-A).
- **`HIPÓTESIS NO VALIDADA`** — el campo 11 de la cabeza global única
  declara `HIPÓTESIS NO VALIDADA`.
- **`NO APLICA — PROPUESTA RECHAZADA`** — no es un estado
  institucional, sino una constancia: el campo 11 de la cabeza global
  única declara ese valor (§6.2).

No existe ningún cuarto estado institucional. Si existen dos o más
cabezas globales no supersedidas (§3.3), el estado documental es
ambiguo y ningún `VIGENTE` puede invocarse.

### 6.1 Origen exacto de cada estado o constancia

- **`HIPÓTESIS NO VALIDADA`** surge exclusivamente de: una entrada de
  `PROPUESTA` inicial; una entrada de `PROPUESTA` de corrección de una
  activación inicial (Caso A, §6.2, dentro del mismo ciclo); una
  entrada de `PROPUESTA` que abre un ciclo nuevo tras el rechazo de
  una activación inicial (Caso B, §6.2); o la entrada de `AUDITORÍA`
  subsiguiente a cualquiera de las anteriores — en todos los casos,
  mientras no exista una entrada de `DECISIÓN` de activación. Una
  entrada de `PROPUESTA` de **revalidación**, y su `AUDITORÍA`
  subsiguiente, **no** originan `HIPÓTESIS NO VALIDADA`: permanecen en
  `REVISIÓN REQUERIDA` (véase el punto siguiente).
- **`REVISIÓN REQUERIDA`** surge **inmediatamente** de un disparador
  de §7 (conocido y verificable, o automático al cumplirse 90 días,
  §7 punto 5, §9-A) y queda **formalizado** por una entrada de
  `DISPARADOR` (§4.4, §9-B); se conserva, repetido expresamente, a lo
  largo de toda la entrada de `PROPUESTA` de revalidación y de su
  entrada de `AUDITORÍA` subsiguiente (§9-C).
- **`VIGENTE`** solo puede surgir de una entrada de `DECISIÓN` que
  satisfaga íntegramente la definición completa de §6: ninguna otra
  entrada puede producirlo.
- **`NO APLICA — PROPUESTA RECHAZADA`** solo puede surgir de una
  entrada de `DECISIÓN` que transcriba el rechazo durable de Miguel
  (§4.3, §6.2): ninguna otra entrada puede producirla.
- Una entrada de `SUPERSESIÓN` **no origina** ninguno de los cuatro
  resultados anteriores: repite, sin alterarlo, el campo 11 de la
  entrada precedente global (§4.5).

En consecuencia: el veredicto del auditor, por sí solo, no activa
ningún adaptador; el registrador no produce ningún estado por decisión
propia; y ninguna entrada de `DECISIÓN` puede producir `VIGENTE` sobre
un veredicto `RECHAZAR` o `BLOQUEAR`, ni sobre hallazgos críticos
abiertos, con independencia de la voluntad de Miguel
(`governance/core/INSTITUTIONAL_CORE.md` §2.1, §13).

### 6.2 Tratamiento de una propuesta o reactivación rechazada

Miguel puede rechazar una propuesta o una reactivación con
independencia de cuál haya sido el veredicto del auditor, incluido
`APROBAR` (§4.3). Además, un veredicto `RECHAZAR` o `BLOQUEAR` bloquea
técnicamente la activación sin que Miguel deba pronunciarse todavía.

Cuando Miguel decide rechazar definitivamente una propuesta o
reactivación, el flujo documental del rechazo es el siguiente:

1. Miguel emite una decisión durable de rechazo (`RECHAZAR`) sobre el
   ciclo, identificando los objetos exigidos por §4.3.
2. Esa decisión queda versionada, previamente, en
   `decisions/OWNER_DECISIONS.md`.
3. Solo después, el **registrador autorizado** agrega al registro la
   entrada de `DECISIÓN` que transcribe exactamente ese rechazo. Miguel
   **nunca** agrega directamente esa entrada.

**Caso A — existe una entrada de `AUDITORÍA` con `RECHAZAR` o
`BLOQUEAR`, pero todavía no existe una entrada de `DECISIÓN`:** este
caso admite dos alternativas distintas, a elección de Miguel:

- **corregir dentro del mismo ciclo, sin decisión de rechazo
  todavía**: una propuesta corregida se agrega como nueva entrada de
  `PROPUESTA`, dentro del mismo ciclo, pasando a ser la propuesta
  exacta (§4.1); exige revisión documental y una nueva entrada de
  `AUDITORÍA` independiente. La secuencia completa de esta alternativa
  es:

  ```text
  PROPUESTA (raíz)
  → AUDITORÍA (RECHAZAR o BLOQUEAR)
  → PROPUESTA (corregida, exacta)
  → AUDITORÍA (de la propuesta corregida)
  → DECISIÓN (sobre la propuesta corregida)
  ```

- **Miguel decide rechazar definitivamente**, mediante el flujo de tres
  pasos descrito arriba, sobre este mismo ciclo, en vez de esperar la
  corrección; en ningún caso Miguel agrega la entrada de `DECISIÓN`
  directamente.

**Caso B — ya existe una entrada de `DECISIÓN` con
`NO APLICA — PROPUESTA RECHAZADA`:**

- cualquier propuesta posterior abre un ciclo nuevo, con su propio
  identificador de ciclo y su propia propuesta raíz; no hereda el
  veredicto ni la decisión del ciclo rechazado.

## 7. Eventos de revisión obligatoria

Un adaptador `VIGENTE` exige nueva revisión ante el primero que ocurra
de los siguientes cinco eventos:

1. cambio mayor o relevante del modelo, incluida su versión o revisión
   identificada, al que el adaptador aplica;
2. un incidente de gobernanza asociado a ese modelo o a ese adaptador;
3. una desviación conductual comprobada del modelo respecto de lo
   declarado por el adaptador;
4. un cambio material en las herramientas disponibles para el modelo;
5. el cumplimiento de 90 días desde la fecha de última revisión
   concluida (§3, §9) de la entrada que dejó al adaptador `VIGENTE`.
   Este evento **ocurre automáticamente** al cumplirse el plazo: no
   depende de que una persona o agente lo haya advertido ni de una
   condición de "conocido y verificable" (esa condición rige
   exclusivamente los cuatro eventos anteriores, §9-A). Este plazo
   nunca se calcula desde una `PROPUESTA`, una `AUDITORÍA` pendiente de
   `DECISIÓN`, una `DECISIÓN` de rechazo, ni una `SUPERSESIÓN`.

El evento que ocurra primero dispara la revisión obligatoria, conforme
al tratamiento de §9. Esta sección no rige la corrección de una
propuesta inicial rechazada o bloqueada (§4.1, §6.2).

## 8. Reporte de hipótesis frente a registro autorizado

- Cualquier agente puede identificar y **reportar** una posible mejora
  o ajuste de comportamiento como hipótesis. **Reportarla no concede
  permiso de escritura** sobre el registro ni la convierte en entrada
  institucional.
- Solo un **proponente autorizado** mediante mandato expreso, con
  permiso literal para versionar el artefacto y para agregar la
  entrada de `PROPUESTA` (§4.1, §5), puede materializar esa hipótesis
  en el registro. Sin ese mandato, la hipótesis permanece reportada
  pero no registrada.
- Una vez materializada como entrada de `PROPUESTA`, ninguna entrada en
  estado `HIPÓTESIS NO VALIDADA` habilita, por sí sola, ningún permiso
  adicional, ninguna ampliación de autonomía ni ninguna excepción a
  `governance/core/INSTITUTIONAL_CORE.md` o a un perfil de proyecto
  (Capa B). Ningún agente ejecuta ni trata como regla una hipótesis
  mientras no exista una entrada de `DECISIÓN` expresa de Miguel.

## 9. Fuente documental, estado operacional y revalidación mediante ciclo completo

Rige exclusivamente las revalidaciones originadas por uno de los cinco
disparadores de §7 sobre un adaptador **anteriormente `VIGENTE`**.

### 9-A. Efecto operacional inmediato de un disparador

- Cuando **no existe ningún evento pendiente de registro**, el estado
  documental de la cabeza global única (campo 11) puede utilizarse
  como evidencia del estado operacional.
- Cuando cualquiera de los cuatro primeros eventos de §7 es conocido y
  verificable para un adaptador `VIGENTE`, ese adaptador deja
  **inmediatamente** de poder utilizarse, con independencia de que la
  entrada de `DISPARADOR` correspondiente ya se haya agregado o no. La
  condición "conocido y verificable" rige exclusivamente estos cuatro
  eventos.
- El **quinto evento (cumplimiento de 90 días, §7 punto 5) ocurre
  automáticamente al cumplirse el plazo**: no depende de que una
  persona o agente lo haya advertido. Antes de cada uso del adaptador
  debe compararse la fecha actual con la fecha durable de última
  revisión concluida (campo 12); al cumplirse 90 días desde esa
  fecha, el adaptador pasa **operacionalmente y de inmediato** a
  `REVISIÓN REQUERIDA`, y queda prohibido utilizarlo aunque todavía no
  exista la entrada de `DISPARADOR` correspondiente.
- En ambos casos, desde ese momento el adaptador se trata
  **fail-closed** como `REVISIÓN REQUERIDA`. El evento debe disponer
  de evidencia citable (para los cuatro primeros) o de la propia
  fecha durable comparada con la fecha actual (para el quinto); esa
  evidencia temporal no crea un segundo registro ni sustituye la
  obligación de agregar la entrada de `DISPARADOR` (§9-B). Ninguna
  entrada `VIGENTE` anterior puede invocarse mientras tanto.

### 9-B. Registro documental del disparador y resincronización

- Debe agregarse y versionarse una entrada de `DISPARADOR` (§4.4),
  exclusivamente por el registrador autorizado, lo antes posible —
  incluido el vencimiento automático de 90 días, que el registrador
  debe formalizar posteriormente mediante esa misma entrada. Mientras
  no exista, el registro queda desactualizado y no acredita vigencia.
- El registro **vuelve a quedar sincronizado** exactamente cuando el
  registrador agrega y versiona esa entrada.
- Antes de revalidar, reactivar o volver a utilizar el adaptador deben
  **coincidir**: el estado operacional real; el estado documental del
  campo 11; y la entrada de `DISPARADOR` durable y citable. La omisión
  o demora documental nunca preserva `VIGENTE`.

### 9-C. Revalidación mediante ciclo completo

- Abre un ciclo nuevo y completo desde una entrada de `PROPUESTA`
  (§4.1), nunca desde `AUDITORÍA`: (1) `PROPUESTA` de revalidación;
  (2) revisión documental; (3) `AUDITORÍA`, agregada por el
  registrador; (4) `DECISIÓN`, agregada por el registrador tras la
  decisión durable de Miguel. Una eventual `SUPERSESIÓN` que corrija
  un defecto no sustantivo de alguna entrada de este ciclo (§4.5) es
  una **operación administrativa separada**, en su propio ciclo, y no
  es un hito numerado de esta secuencia sustantiva.
- La `PROPUESTA` de revalidación declara expresamente mantener sin
  cambios (justificado) o modificar (identificando la nueva versión).
- Durante ese ciclo, el adaptador permanece `REVISIÓN REQUERIDA`: no
  vuelve a `HIPÓTESIS NO VALIDADA`, y no puede utilizarse.
- Solo una entrada de `DECISIÓN` que satisfaga íntegramente la
  definición completa de `VIGENTE` (§6) puede devolver el adaptador a
  `VIGENTE`, fijando una nueva fecha de última revisión concluida.

## 10. Secuencia durable de commits y prohibición de autorreferencias Git

- Una entrada del registro **no puede citar como evidencia el commit
  que simultáneamente crea esa misma entrada** (§3.2): toda evidencia
  Git citada por una entrada, incluido cualquier puntero durable
  completo, debe existir antes del commit que versiona esa entrada.
- Si todavía no existe el commit requerido, corresponde `PENDIENTE`
  (§3, §4.1, §4.2), o una condición operacional de bloqueo reportada
  por el registrador (§4.2, §4.3, §5), o el veredicto formal
  `BLOQUEAR` del auditor independiente (§12), según la etapa; nunca se
  inventa, se anticipa ni se reserva un SHA futuro.
- Una rama, `main`, un tag móvil, `HEAD` o un hash abreviado no
  sustituyen un commit completo.
- **Ruta limpia, sin correcciones** — la secuencia durable
  **obligatoria**, de principio a fin, es de **seis commits**:

  ```text
  1. commit del artefacto propuesto
  2. commit de la entrada de PROPUESTA del registro,
     agregada por el proponente autorizado
  3. commit del informe independiente del auditor
  4. commit de la entrada de AUDITORÍA del registro,
     agregada por el registrador autorizado
  5. commit de la decisión durable de Miguel
  6. commit de la entrada de DECISIÓN del registro,
     agregada por el registrador autorizado
  ```

- **Ruta con corrección** — por cada corrección posterior a una
  entrada de `AUDITORÍA` con `RECHAZAR` o `BLOQUEAR` (§4.1 Caso A,
  §6.2), se insertan **cuatro commits adicionales** antes de los
  commits 5 y 6 de la ruta limpia:

  ```text
  3a. nuevo commit del artefacto corregido
  3b. nuevo commit de la entrada de PROPUESTA corregida
  3c. nuevo commit del informe independiente (sobre la propuesta corregida)
  3d. nuevo commit de la entrada de AUDITORÍA (de la propuesta corregida)
  ```

  Por tanto: la ruta limpia tiene seis commits; una corrección eleva
  la secuencia a diez commits; cada corrección adicional agrega otros
  cuatro commits. **Ningún hito puede omitirse, agruparse ni
  colapsarse**, en ninguna de las dos rutas.
- **Ninguno de los hitos anteriores puede colapsarse** con el que lo
  precede o lo sucede, porque cada entrada posterior debe citar,
  mediante puntero durable completo, el SHA completo del commit
  anterior. El informe de auditoría y la entrada de `AUDITORÍA` nunca
  son el mismo commit ni el mismo agente; ni la decisión durable de
  Miguel y la entrada de `DECISIÓN`.
- Una implementación futura solo podrá agrupar en un mismo commit
  operaciones auxiliares que no sean ninguno de estos hitos y que no
  eliminen evidencia intermedia obligatoria.

## 11. Incompatibilidad con la Capa A

- Ningún adaptador puede introducir una regla, un permiso o una
  excepción incompatible con `governance/core/INSTITUTIONAL_CORE.md`.
- Un adaptador solo puede añadir precisión operativa sobre cómo un
  modelo concreto cumple la Capa A; nunca puede conceder un permiso
  que la Capa A no conceda, ni relajar una de sus prohibiciones.
- Un adaptador jamás puede relajar `governance/core/INSTITUTIONAL_CORE.md`,
  conforme a la regla de imposibilidad de esa Capa A §19.
- Toda incompatibilidad detectada obliga a `RECHAZAR` o `BLOQUEAR`
  según corresponda conforme a
  `governance/core/INSTITUTIONAL_CORE.md` §12-§13, y se registra como
  hallazgo en el informe del auditor.

## 12. Veredictos y autoridad final

- Los únicos veredictos válidos del auditor independiente son
  `APROBAR`, `RECHAZAR` y `BLOQUEAR`, en los términos de
  `governance/core/INSTITUTIONAL_CORE.md` §12. Solo el auditor emite
  el veredicto; el registrador únicamente lo transcribe (§5).
- La autoridad final para que una entrada de `DECISIÓN` conceda,
  mantenga o revoque el estado `VIGENTE` de cualquier adaptador es
  exclusivamente Miguel, en su rol de propietario y autoridad final
  (`governance/core/INSTITUTIONAL_CORE.md` §2.1). Solo Miguel decide;
  el registrador únicamente transcribe esa decisión (§5).
- Esta autoridad final no elimina las barreras institucionales de
  auditoría independiente y de hallazgos críticos abiertos de
  `governance/core/INSTITUTIONAL_CORE.md` §13: un veredicto `RECHAZAR`
  o `BLOQUEAR`, un hallazgo crítico abierto, cualquier discordancia
  entre los punteros exigidos por §4.2-§4.3, o una bifurcación de
  cabeza global (§3.3), impiden `VIGENTE` con independencia de la
  voluntad de Miguel.

---

*Esta política es un borrador de la Capa A del marco de gobernanza
multi-IA. Permanece en estado BORRADOR — NO CONGELADO. No crea
`adapters/`, ningún adaptador ni ningún registro operativo. Su
congelación exige auditoría independiente con veredicto `APROBAR`
vigente y decisión final y expresa del propietario del proyecto,
posterior y separada de esta implementación.*
