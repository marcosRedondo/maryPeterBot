# Spec Delta

## Purpose

Define el comportamiento local del prototipo electrónico P1 para validar en un ESP32 la gestión de estados y las salidas simuladas antes de añadir comunicación inalámbrica, tracción o cuchilla.

## ADDED Requirements

### Requirement: Gestión de estados del prototipo
El sistema SHALL exponer los estados OFF, READY, RUNNING, STOPPED, ERROR y EMERGENCY, e informar del estado actual después de cada transición aceptada.

#### Scenario: Inicialización correcta
- **WHEN** el controlador termina de inicializarse sin errores
- **THEN** el estado pasa a READY y el estado actual puede consultarse

#### Scenario: Inicio desde READY
- **WHEN** se acepta una orden START estando en READY
- **THEN** el estado pasa a RUNNING

#### Scenario: Parada solicitada
- **WHEN** se acepta una orden STOP estando en RUNNING
- **THEN** el estado pasa a STOPPED

#### Scenario: Orden no válida para el estado actual
- **WHEN** se recibe una orden que no está permitida en el estado actual
- **THEN** el sistema conserva el estado actual e informa que la orden no fue aceptada

### Requirement: Salidas simuladas seguras
El sistema SHALL representar mediante LEDs las salidas simuladas del prototipo y mantenerlas desactivadas en OFF, STOPPED, ERROR y EMERGENCY.

#### Scenario: Entrada en estado seguro
- **WHEN** el sistema entra en OFF, STOPPED, ERROR o EMERGENCY
- **THEN** todas las salidas simuladas representadas por LEDs quedan desactivadas

#### Scenario: Activación de salida simulada
- **WHEN** el sistema está en RUNNING y acepta una orden de salida simulada
- **THEN** el LED asociado refleja la salida activada

### Requirement: Parada de emergencia
El sistema SHALL priorizar la emergencia sobre las órdenes normales y desactivar inmediatamente todas las salidas simuladas.

#### Scenario: Emergencia durante RUNNING
- **WHEN** se activa la condición de emergencia mientras el estado es RUNNING
- **THEN** el estado pasa a EMERGENCY y todas las salidas simuladas quedan desactivadas

#### Scenario: Orden normal durante emergencia
- **WHEN** se recibe una orden de inicio o activación mientras el estado es EMERGENCY
- **THEN** la orden no se ejecuta, el estado permanece en EMERGENCY y las salidas siguen desactivadas
