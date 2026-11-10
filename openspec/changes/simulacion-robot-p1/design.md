# Design

## Context

Consulte `proposal.md` para la motivación y `specs/simulacion-robot/spec.md` para los requisitos de simulación. P1 se realizará primero en software; no hay firmware ni plataforma de simulación configurada en el repositorio. El equipo de desarrollo es Windows y los datos del robot y del terreno siguen incompletos, por lo que el modelo deberá declarar sus supuestos.

## Goals / Non-Goals

**Goals:**
- Preparar e instalar una herramienta de simulación adecuada y verificarla con un ejemplo.
- Representar un robot diferencial configurable en un entorno reproducible.
- Probar movimiento básico y registrar parámetros, resultados y límites.

**Non-Goals:**
- Comprar componentes o validar motores físicos.
- Implementar cuchilla, sensores físicos o navegación autónoma completa.
- Sustituir la validación física futura con resultados virtuales.

## Decisions

- Se compararán herramientas gratuitas según compatibilidad con Windows, soporte para robot diferencial y facilidad de uso.
- Se probará un ejemplo del candidato mejor valorado; solo si no cumple los criterios se evaluará el siguiente candidato.
- La herramienta elegida, versión, instalación y resultado del ejemplo quedarán documentados antes de crear el modelo propio.
- Los parámetros se clasificarán como conocidos, estimados o pendientes. El informe de resultados indicará qué conclusiones dependen de estimaciones.
- Se separarán geometría, parámetros cinemáticos, escenario y control para permitir cambiar supuestos sin rehacer el proyecto.
- El ESP32 y los LEDs del inventario podrán emplearse en P2 para contrastar lógica; la falta de identificación física no bloquea P1.

## Risks / Trade-offs

- [El equipo puede no cumplir los requisitos de la herramienta] → Revisar compatibilidad antes de adoptarla y documentar alternativas si no funciona.
- [Los resultados dependen de parámetros todavía estimados] → Etiquetar supuestos y evitar presentar resultados virtuales como mediciones reales.
- [El modelo simplificado puede omitir condiciones del césped real] → Limitar las conclusiones al comportamiento representado y reservar validación en terreno para fases posteriores.

## Migration Plan

No hay firmware ni modelo virtual previo que migrar. Crear la estructura del simulador después de verificar la instalación. La futura validación ESP32 se mantendrá separada y podrá reutilizar el contrato de comandos cuando se defina.

## Open Questions

- ¿Qué dimensiones y características del terreno están confirmadas para parametrizar el escenario? Lo desconocido se marcará como estimado o pendiente.
