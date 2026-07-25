# <AGENTE>_AUDIT.md — <ID-TAREA>

Plantilla para auditorías (`CODEX_AUDIT.md`, `GEMINI_REVIEW.md` cuando
actúan como auditoría). El auditor **no modifica** el artefacto
auditado ni el informe que audita; este archivo es su único producto.

## 1. Identificación

- **Tarea auditada:**
- **Agente auditor:**
- **Artefacto(s) auditado(s) (rutas literales):**
- **Commit auditado:**

## 2. Alcance de la auditoría

<Qué se revisó exactamente y qué quedó fuera del alcance de esta
auditoría.>

## 3. Archivos abiertos por el auditor

Lista literal. La lectura de auditoría no autoriza modificar el
artefacto auditado.

1.

## 4. Comandos ejecutados

```text
```

## 5. Hallazgos

| # | Severidad (crítico/mayor/menor) | Descripción | Ubicación (archivo:línea) |
|---|---|---|---|
|   |   |   |   |

**Un hallazgo crítico bloquea el avance** de la tarea auditada hasta
resolución explícita, con independencia de otros veredictos.

## 6. Estado Git final (del auditor)

```text
git status --short
```

<Pegar la salida real. Debe permanecer limpio si el auditor no
modificó nada, como corresponde a su rol.>

## 7. Veredicto de auditoría

El veredicto debe ser exactamente uno:

- APROBAR
- RECHAZAR
- BLOQUEAR

- Cualquier hallazgo crítico obliga a `BLOQUEAR`.
- `APROBAR` significa que no existen incumplimientos que impidan
  aceptar el artefacto.
- `RECHAZAR` significa que el artefacto fue completamente auditable,
  pero requiere corrección y una nueva entrega.
- `BLOQUEAR` significa que la auditoría no puede continuar o existe un
  hallazgo crítico.
- Ningún veredicto reemplaza la autorización expresa de Miguel.

Este veredicto es un insumo para la decisión de Miguel; **no reemplaza
su autorización** para ninguna acción irreversible ni para avanzar a la
siguiente fase.
