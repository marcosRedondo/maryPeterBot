# Proposal

## Why

Antes de comprar componentes de tracción, batería o sensores, MaryPeterBot necesita validar virtualmente decisiones de geometría, movimiento y control. Preparar el entorno de simulación primero permite detectar supuestos erróneos y orientar las compras posteriores. El hardware ESP32 comunicado se conserva como recurso para una fase de validación física posterior.

## What Changes

- Reorientar P1 a preparar el entorno y validar el funcionamiento básico del robot en simulación.
- Instalar y verificar una herramienta de simulación compatible con el equipo disponible, después de comparar opciones.
- Modelar un robot diferencial configurable y un escenario de prueba, distinguiendo parámetros conocidos, estimados y pendientes.
- Probar órdenes de avance, retroceso, giro y parada de forma repetible.
- Dejar la validación electrónica con ESP32 y LEDs para P2, usando material existente cuando sea posible.
- Mantener fuera de P1 las compras, el movimiento físico, la cuchilla y la navegación autónoma completa.

## Capabilities

### New Capabilities
- `simulacion-robot`: preparación del entorno y pruebas virtuales de movimiento básico.

### Modified Capabilities
- Ninguna.

## Impact

- Roadmap y documentación de P1.
- Entorno y archivos del modelo de simulación, una vez seleccionada la herramienta.
- No se requiere firmware ESP32 ni compra de hardware para completar P1.
