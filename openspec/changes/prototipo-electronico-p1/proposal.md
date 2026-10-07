# Proposal

## Why

El proyecto necesita validar la lógica básica del robot con el ESP32 antes de añadir comunicación inalámbrica o hardware de movimiento. P1 permitirá comprobar estados, parada y salidas simuladas con un prototipo de bajo coste, manteniendo sin confirmar los modelos y conexiones hasta revisar el inventario físico.

## What Changes

- Definir el comportamiento del control electrónico local del prototipo P1.
- Representar salidas del robot mediante LEDs y mantenerlas desactivadas en los estados de parada, error y emergencia.
- Definir cómo se inicializa el prototipo y cómo se verifican sus estados y transiciones.
- Documentar el circuito y la asignación de pines después de confirmar el hardware realmente disponible.
- Mantener P1 sin motores, cuchilla ni comunicación móvil; esta última pertenece a P2.

## Capabilities

### New Capabilities
- `control-electronico`: gestión local de estados y salidas simuladas del prototipo electrónico.

### Modified Capabilities
- Ninguna.

## Impact

- Documentación de diseño y pruebas del prototipo P1.
- Firmware del ESP32, cuando se implemente la propuesta.
- Circuito de LEDs; modelo de placa, pines y componentes concretos quedan pendientes de confirmar mediante el inventario físico antes de cablear.
- Sin cambios a APIs externas ni a dependencias existentes identificadas; el repositorio todavía no contiene firmware.
