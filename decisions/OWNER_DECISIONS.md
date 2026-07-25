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
