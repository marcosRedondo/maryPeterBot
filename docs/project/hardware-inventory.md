# Inventario de hardware

**Proyecto:** Robot cortacésped autónomo
**Estado:** Inventario recopilado; faltan identificaciones y comprobaciones físicas puntuales
**Última actualización:** 2026-10-13

Este inventario recoge el material comunicado en el chat del proyecto **«Inventario Arduino rescatado»**. Las cantidades se transcriben de ese inventario; los modelos, valores eléctricos y compatibilidad que no constan quedan pendientes de comprobación. No se debe inferir un modelo de placa, valor de resistencia ni capacidad de alimentación.

## Control y computación

| Elemento | Cantidad comunicada | Modelo / características | Estado y observaciones |
|---|---:|---|---|
| Placas ESP32 | 5 | Modelo exacto pendiente | Disponibles según el inventario del chat; identificar la placa elegida antes de asignar GPIO. |
| Arduino | 1 | Arduino Uno | Disponible según el inventario; no necesario para P1. |
| Raspberry Pi | 1 | Model B; revisión exacta pendiente | Disponible según el inventario; no necesaria para P1. |

## Electrónica y montaje

| Elemento | Cantidad comunicada | Modelo / características | Estado y observaciones |
|---|---:|---|---|
| Protoboard | 1 | Tamaño/modelo pendiente | Disponible según el inventario. |
| Cables Dupont | 1 lote | Tipos y cantidades por comprobar | Disponibles según el inventario. |
| Resistencias | 1 lote | Valores y cantidades pendientes | Disponibles según el inventario; identificar valores antes de conectar LEDs. |
| Módulo de relé | 1 | Un canal; modelo y tensión de bobina pendientes | Disponible; queda fuera del alcance P1. |
| Pulsadores | 5 | Tipo pendiente | Disponibles; P1 puede comenzar sin ellos si se usa el monitor serie. |
| Trimmers/potenciómetros | 3 | Valores pendientes | Disponibles; no necesarios para el alcance actual de P1. |
| LEDs | 1 lote | Varios colores, aproximadamente 5 mm según inspección previa | Disponibles; cantidad exacta y características eléctricas pendientes. |
| Componentes pequeños sin identificar | 2 | Sin identificar | No asignarles uso hasta identificarlos. |

## Alimentación y conexión al ordenador

| Elemento | Cantidad comunicada | Modelo / características | Estado y observaciones |
|---|---:|---|---|
| Portapilas | 1 | Para 3 pilas AA; 4,5 V nominales sin carga | Disponible; no asumir que sea adecuado para alimentar directamente la placa ESP32. |
| Cable USB para programar ESP32 | Pendiente | Conector, cantidad y capacidad de datos desconocidos | Confirmar un cable de datos compatible. El chat del inventario no confirma cables USB. |
| Fuente/cargador USB | Pendiente | Características desconocidas | No consta en el inventario recuperado. |

## Resumen para P1

El inventario comunicado incluye placas ESP32, LEDs, resistencias, protoboard y cables Dupont, por lo que hay material potencial para preparar el prototipo local de P1 sin motores. Antes de cerrar el circuito hay que inspeccionar la placa ESP32 seleccionada, identificar los valores de las resistencias y confirmar la cantidad/características de los LEDs. También falta confirmar un cable USB de datos para programar y usar el monitor serie.

No se ha confirmado en el chat un circuito concreto, los GPIO, los valores de resistencias, el modelo exacto de ESP32 ni que el portapilas sea una alimentación apropiada para la placa. Esos datos deben verificarse antes de cablear. El móvil y la comunicación inalámbrica corresponden a P2, no a P1.
