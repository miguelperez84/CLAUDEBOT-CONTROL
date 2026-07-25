# CLAUDEBOT-CONTROL

Repositorio de coordinación documental para los agentes de IA que
colaboran en el proyecto científico `CLAUDEBOT`.

## Propósito

Este repositorio almacena exclusivamente:

- mandatos dirigidos a agentes (Sonnet, Codex, Gemini u otros);
- informes de ejecución y auditorías entregados por esos agentes;
- decisiones del propietario del proyecto (Miguel);
- plantillas para estandarizar mandatos, informes y auditorías.

## Qué NO almacena este repositorio

- Código científico del proyecto (laboratorios, señales, backtests).
- Datasets, CSV, resultados de discovery u OOS.
- Artefactos de producción (`v4/`, conectores, base de datos, alertas).
- Secretos, credenciales o archivos privados.

Todo lo anterior permanece exclusivamente en
`/home/miguel/proyectos/CLAUDEBOT`, que este repositorio no modifica
bajo ninguna circunstancia.

## Relación con CLAUDEBOT

`CLAUDEBOT-CONTROL` es un repositorio **separado e independiente**. No
es un submódulo, no comparte historia git y no se sincroniza
automáticamente con `CLAUDEBOT`. La coordinación entre ambos ocurre
únicamente porque un humano (Miguel) o un agente autorizado lee un
mandato aquí y actúa sobre `CLAUDEBOT` en una tarea separada, o
documenta aquí el resultado de una tarea ya ejecutada allí.

## Estructura

```text
CLAUDEBOT-CONTROL/
├── README.md
├── AGENTS.md
├── tasks/
│   └── <ID-TAREA>/
│       ├── MANDATE.md
│       ├── CONTEXT.md
│       ├── ACCEPTANCE.md
│       └── STATUS.md
├── reports/
│   └── <ID-TAREA>/
│       ├── SONNET_REPORT.md
│       ├── CODEX_AUDIT.md
│       └── GEMINI_REVIEW.md
├── decisions/
│   └── OWNER_DECISIONS.md
└── templates/
    ├── TASK_TEMPLATE.md
    ├── REPORT_TEMPLATE.md
    └── AUDIT_TEMPLATE.md
```

Ver `AGENTS.md` para las reglas de operación vinculantes de todo agente
que participe en este repositorio.
