# maryPeterBot

Proyecto de desarrollo incremental de un robot cortacésped autónomo. El trabajo se divide en fases pequeñas y verificables, priorizando la validación temprana, la seguridad y el gasto progresivo.

## Estado actual

El proyecto está en **P0 — Definición y preparación**. La propuesta OpenSpec, `prototipo-electronico-p1`, define el prototipo electrónico local con ESP32 y salidas simuladas mediante LEDs; la comunicación móvil se abordará después en P2. El inventario recoge el material comunicado, pero el modelo exacto de ESP32 y varios datos eléctricos siguen pendientes antes de fijar circuito y pines.

## Documentación

- [Documento inicial](docs/project/initial-document.md): visión, principios y alcance.
- [Roadmap](docs/project/roadmap.md): fases P0–P9 y próximos pasos.
- [Inventario de hardware](docs/project/hardware-inventory.md): material disponible y datos pendientes de confirmar.
- [Propuesta OpenSpec P1](openspec/changes/prototipo-electronico-p1/proposal.md): objetivo y alcance del primer prototipo.
- [Diseño OpenSpec P1](openspec/changes/prototipo-electronico-p1/design.md): enfoque técnico propuesto.
- [Especificación P1](openspec/changes/prototipo-electronico-p1/specs/control-electronico/spec.md): comportamiento esperado.
- [Tareas P1](openspec/changes/prototipo-electronico-p1/tasks.md): trabajo previsto para implementar y validar P1.

## Próximo paso

Comprobar físicamente el modelo de ESP32, los valores de resistencias, los LEDs y un cable USB de datos; completar esos datos antes de definir el circuito de prueba de P1.
