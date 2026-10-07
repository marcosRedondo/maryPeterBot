# Design

## Context

Consulte `proposal.md` para la motivación y `specs/control-electronico/spec.md` para el contrato de comportamiento. El repositorio aún no contiene firmware ni configuración de plataforma. El inventario disponible es provisional: no confirma modelos de placa, LEDs ni valores de resistencias.

## Goals / Non-Goals

**Goals:**
- Mantener la lógica de estados independiente de la asignación física de GPIO.
- Permitir probar las transiciones localmente antes de incorporar comunicación móvil.
- Incorporar el circuito y los pines solo después de comprobar el inventario y el modelo exacto de placa.

**Non-Goals:**
- Elegir o comprar hardware definitivo.
- Añadir movimiento, cuchilla, sensores físicos o navegación.
- Implementar la comunicación de P2.

## Decisions

- Separar la gestión de estados y órdenes de la capa de salidas GPIO. Así se pueden comprobar transiciones sin depender del cableado y cambiar pines sin alterar el contrato de estados.
- Usar el monitor serie por USB como interfaz temporal de diagnóstico y estímulo de órdenes de prueba en P1. Se considera frente a botones físicos porque la disponibilidad de botones aún no está confirmada y permite probar sin añadir otra pieza al circuito. No forma parte de la interfaz de P2.
- Documentar el mapeo de GPIO y el cableado únicamente tras confirmar el modelo ESP32, LEDs, resistencias y alimentación. No se asumirán LEDs integrados ni valores de componentes.
- Mantener las salidas en estado seguro al iniciar y cada vez que se active parada, error o emergencia; las salidas simuladas representan señales únicamente y no se conectarán a motores ni cuchillas.

## Risks / Trade-offs

- [El inventario confirmado podría no incluir LEDs o componentes adecuados] → Completar el inventario antes de cablear; revisar la posibilidad de usar un LED integrado solo si el modelo lo confirma y documentar cualquier material adicional requerido.
- [El monitor serie no representa todavía el uso desde un móvil] → Limitarlo a pruebas locales de P1 y especificar la interfaz de comunicación en el cambio de P2.
- [La selección de pines depende de la placa exacta] → No asignar ni conectar pines hasta identificar el modelo y revisar su documentación.

## Migration Plan

No hay firmware existente que migrar. Crear la estructura de firmware para la placa confirmada, implementar primero la lógica aislada, y luego añadir el adaptador GPIO y el circuito de LEDs. Para revertir el prototipo basta con desconectar la alimentación USB y retirar el cableado de prueba.

## Open Questions

- ¿Qué placa ESP32 y qué LEDs/resistencias están realmente disponibles? Resolverlo con el inventario antes de fijar pines y cableado.
