# Tasks

## 1. Confirmación del hardware y banco de prueba

- [ ] 1.1 Confirmar físicamente el modelo y cantidad de ESP32, la presencia de LEDs y resistencias (incluidos sus valores), y qué cables USB permiten datos; actualizar `docs/project/hardware-inventory.md` y verificar que cada elemento esté marcado como confirmado o pendiente.
- [ ] 1.2 Seleccionar una placa ESP32 y los componentes de prueba disponibles; documentar diagrama de conexión y GPIO en `docs/project/` y verificar que el esquema corresponde al modelo exacto de la placa y a los valores confirmados.

## 2. Lógica local de estados

- [ ] 2.1 Elegir y documentar el entorno de compilación compatible con la placa confirmada; verificarlo compilando un programa mínimo para ese modelo.
- [ ] 2.2 Crear el firmware base y la lógica de estados independiente de GPIO; verificar inicialización en READY, transición START a RUNNING, STOP a STOPPED y rechazo de órdenes no permitidas.
- [ ] 2.3 Implementar prioridad de EMERGENCY y salidas lógicas seguras para OFF, STOPPED, ERROR y EMERGENCY; verificar que una orden normal no reactiva las salidas durante emergencia.
- [ ] 2.4 Añadir entrada y consulta de estado por monitor serie para las pruebas locales de P1; verificar comandos aceptados, rechazados y respuestas de estado.

## 3. Integración de salidas LED

- [ ] 3.1 Implementar el adaptador GPIO según el circuito documentado y verificar cada salida LED con el prototipo desconectado de cualquier motor o cuchilla.
- [ ] 3.2 Verificar en el banco todos los escenarios de `specs/control-electronico/spec.md`, registrar resultados y documentar cualquier desviación o limitación en `docs/project/`.

## 4. Cierre de P1

- [ ] 4.1 Revisar que inventario, circuito, firmware y resultados de prueba estén documentados; verificar los criterios de finalización P1 del roadmap antes de proponer el avance a P2.
