# tasks/

Cada tarea vive en su propia carpeta `tasks/<ID-TAREA>/` con exactamente
estos cuatro archivos:

```text
tasks/<ID-TAREA>/
├── MANDATE.md      # el mandato: alcance, prohibiciones, criterios de aceptación
├── CONTEXT.md       # contexto necesario para ejecutar sin releer todo el historial
├── ACCEPTANCE.md    # criterios de aceptación verificables, en detalle
└── STATUS.md        # estado vivo de la tarea (abierta, bloqueada, cerrada)
```

`<ID-TAREA>` sigue una convención corta y estable (por ejemplo
`F10-H2`, `F10-H3`, `INV-2026-07-25-01`), fijada por Miguel o acordada
con él antes de crear la carpeta.

Reglas:

- No crear una carpeta de tarea sin mandato explícito de Miguel.
- `MANDATE.md` no se modifica una vez que un agente comienza a
  ejecutar sobre él; un cambio de alcance exige un mandato nuevo o una
  adenda explícita aprobada por Miguel.
- `STATUS.md` se actualiza a medida que avanza la tarea; es el único
  archivo de la carpeta que se espera que cambie con frecuencia.

Ver `templates/TASK_TEMPLATE.md` para la plantilla de `MANDATE.md`.
