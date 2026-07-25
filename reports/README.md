# reports/

Cada tarea recibe sus informes en `reports/<ID-TAREA>/`, con el mismo
`<ID-TAREA>` que su carpeta correspondiente en `tasks/`:

```text
reports/<ID-TAREA>/
├── SONNET_REPORT.md
├── CODEX_AUDIT.md
└── GEMINI_REVIEW.md
```

Regla de existencia: **solo debe existir el archivo correspondiente al
agente que efectivamente haya participado** en esa tarea. No se crean
los tres archivos por defecto ni como plantilla vacía dentro de una
tarea real.

Todo informe debe declarar, como mínimo (ver
`templates/REPORT_TEMPLATE.md` y `templates/AUDIT_TEMPLATE.md`):

1. archivos abiertos;
2. archivos modificados;
3. comandos ejecutados;
4. estado Git final.

Un informe de auditoría (`CODEX_AUDIT.md`, `GEMINI_REVIEW.md` cuando
actúan como auditoría) no modifica el artefacto auditado ni el informe
que audita; registra su propio veredicto en su propio archivo.
