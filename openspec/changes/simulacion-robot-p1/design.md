# Design

## Context

Consulte `proposal.md` para la motivación y `specs/control-electronico/spec.md` para los requisitos de simulación. P1 se realizará primero en software; no hay firmware ni plataforma de simulación configurada en el repositorio. El equipo de desarrollo es Windows y los datos del robot y del terreno siguen incompletos, por lo que el modelo deberá declarar sus supuestos.

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

- La selección del simulador se hará después de revisar compatibilidad con Windows, requisitos del modelo y facilidad de automatizar pruebas; la propuesta no fija todavía una herramienta.
- La primera tarea técnica es instalar el simulador elegido y abrir un mundo de ejemplo antes de desarrollar el modelo propio.
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

- ¿Qué simulador ofrece el mejor equilibrio entre compatibilidad con el ordenador, facilidad de uso y capacidad para representar un robot diferencial?
- ¿Qué dimensiones y características del terreno están ya confirmadas para parametrizar el primer escenario?
