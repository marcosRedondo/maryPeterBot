# P0.3 — Roadmap del robot cortacésped

**Proyecto:** Robot cortacésped autónomo  
**Documento:** P0.3 — Roadmap  
**Estado:** Borrador  
**Versión:** 0.1  
**Fecha:** 2026-10-07

---

## 1. Objetivo

Definir el roadmap de desarrollo del robot cortacésped desde el primer prototipo electrónico hasta una versión funcional capaz de trabajar de forma autónoma en el terreno.

El desarrollo se realizará de forma **incremental**, validando cada fase antes de avanzar a la siguiente.

El objetivo inicial no es construir directamente el robot definitivo, sino reducir riesgos y costes mediante pequeños prototipos que permitan comprobar individualmente:

- Electrónica.
- Software.
- Comunicación.
- Control.
- Movimiento.
- Corte.
- Seguridad.
- Sensores.
- Navegación.
- Autonomía.

---

# 2. Principios de desarrollo

El proyecto seguirá los siguientes principios:

### 2.1. Prototipado progresivo

No se incorporarán todos los componentes desde el principio.

Cada fase añadirá una nueva capacidad al sistema.

### 2.2. Aprovechar el hardware disponible

Durante las primeras fases se utilizarán principalmente los ESP32 y otros componentes disponibles.

No se comprarán motores, sensores u otros componentes hasta que sean necesarios para la siguiente fase.

### 2.3. Minimizar costes

Antes de comprar hardware se comprobará si puede simularse la funcionalidad mediante:

- LEDs.
- Pulsadores.
- Serial Monitor.
- Bluetooth.
- Software.
- Componentes ya disponibles.

### 2.4. Separar funcionalidades

Cada subsistema deberá poder probarse de forma independiente siempre que sea posible.

Por ejemplo:

- Control de motores.
- Control de cuchilla.
- Comunicación.
- Sensores.
- Seguridad.

### 2.5. Seguridad desde el principio

Aunque las primeras fases no utilicen motores ni cuchillas, la arquitectura del software deberá contemplar desde el principio estados de:

- Parada.
- Emergencia.
- Error.
- Pérdida de comunicación.

---

# 3. Roadmap general

| Fase | Nombre | Objetivo principal |
|---|---|---|
| P0 | Definición y preparación | Definir y preparar el proyecto |
| P1 | Prototipo electrónico | Validar ESP32 y lógica básica |
| P2 | Comunicación y control | Controlar el prototipo remotamente |
| P3 | Prototipo móvil | Incorporar motores y movimiento |
| P4 | Sistema de corte | Incorporar y controlar la cuchilla |
| P5 | Sensores y seguridad | Detectar situaciones peligrosas |
| P6 | Navegación autónoma | Conseguir movimiento autónomo |
| P7 | Pruebas en terreno | Validar el robot en condiciones reales |
| P8 | Optimización | Mejorar rendimiento y fiabilidad |
| P9 | Versión definitiva | Construir una versión estable |

---

# 4. P0 — Definición y preparación

## Objetivo

Preparar la base documental, técnica y organizativa del proyecto.

## Tareas

- Crear y organizar el repositorio.
- Definir estructura de documentación.
- Definir arquitectura inicial.
- Configurar OpenSpec.
- Identificar hardware disponible.
- Identificar hardware que será necesario comprar posteriormente.
- Definir objetivos del primer prototipo.
- Definir restricciones del proyecto.
- Definir criterios de seguridad iniciales.

## Resultado

Proyecto preparado para comenzar el desarrollo del primer prototipo.

## Criterio de finalización

La documentación inicial y la estructura del proyecto están definidas y el inventario de hardware disponible está documentado.

---

# 5. P1 — Prototipo electrónico básico

## Objetivo

Construir el primer prototipo **sin motores y sin cuchilla**.

El objetivo será comprobar que el ESP32, el software y la lógica básica del robot funcionan correctamente.

## Hardware

Inicialmente:

- ESP32.
- LEDs.
- Resistencias.
- Pulsadores, si están disponibles.
- Cableado.
- Alimentación USB.

No se utilizarán todavía:

- Motores.
- Drivers de motores.
- Motor de cuchilla.
- Batería principal del robot.

## Simulación

Los LEDs representarán diferentes elementos del robot.

Por ejemplo:

| LED | Representación |
|---|---|
| LED 1 | Motor izquierdo |
| LED 2 | Motor derecho |
| LED 3 | Cuchilla |
| LED 4 | Estado del robot |
| LED 5 | Error/emergencia |

No significa que estos sean necesariamente los LEDs definitivos; son únicamente una herramienta de simulación.

## Software

Crear una primera estructura de software que permita:

- Inicializar el ESP32.
- Gestionar entradas.
- Gestionar salidas.
- Gestionar estados.
- Ejecutar comandos.
- Detectar errores.
- Gestionar parada.

## Estados iniciales

Como mínimo:

```text
OFF
READY
RUNNING
STOPPED
ERROR
EMERGENCY
```

## Pruebas

Se comprobará:

- Encendido.
- Inicialización.
- Cambio de estados.
- Activación de salidas.
- Parada.
- Simulación de error.
- Simulación de emergencia.

## Resultado esperado

Tener sobre la mesa un **robot virtual** representado mediante LEDs.

Por ejemplo:

```text
          ESP32
            │
    ┌───────┼────────┐
    │       │        │
 Motor L  Motor R  Cuchilla
   LED      LED       LED
```

## Criterio de finalización

La lógica principal funciona correctamente y todas las transiciones de estado previstas han sido probadas.

---

# 6. P2 — Comunicación y control

## Objetivo

Añadir comunicación inalámbrica y controlar el prototipo desde otro dispositivo.

Inicialmente seguirá sin haber motores.

Los LEDs continuarán simulando el comportamiento del robot.

## Funcionalidades

- Comunicación Bluetooth.
- Conexión con dispositivo de control.
- Envío de comandos.
- Recepción de comandos.
- Respuesta del ESP32.
- Información del estado actual.

## Comandos iniciales

Por ejemplo:

```text
START
STOP
FORWARD
BACKWARD
LEFT
RIGHT
CUT_ON
CUT_OFF
EMERGENCY
STATUS
```

Estos comandos no controlarán todavía motores reales.

Controlarán los LEDs y estados del prototipo.

## Seguridad

Se deberá estudiar desde esta fase el comportamiento ante:

- Pérdida de conexión.
- Comando desconocido.
- Error del ESP32.
- Activación de emergencia.

## Resultado esperado

Poder controlar desde el dispositivo de prueba un "robot virtual" mediante Bluetooth.

## Criterio de finalización

Todos los comandos definidos funcionan correctamente y el robot entra en un estado seguro cuando se pierde la comunicación o se produce una condición de emergencia.

---

# 7. P3 — Prototipo móvil

## Objetivo

Sustituir las simulaciones por componentes físicos de movimiento.

Aquí comienza el primer prototipo físico del robot.

## Hardware

Se incorporarán:

- Motores de tracción.
- Driver/controlador de motores.
- Batería.
- Chasis provisional.
- Ruedas.
- Cableado de potencia.
- Protecciones necesarias.

## Funcionalidades

- Avance.
- Retroceso.
- Giro izquierda.
- Giro derecha.
- Parada.
- Control independiente de motores.
- Control de velocidad.

## Pruebas

Inicialmente el robot deberá moverse:

- Sin cuchilla.
- En una superficie controlada.
- A baja velocidad.
- Preferiblemente con control manual.

## Resultado esperado

Robot móvil controlado por el ESP32.

## Criterio de finalización

El robot puede desplazarse y detenerse de forma controlada y repetible.

---

# 8. P4 — Sistema de corte

## Objetivo

Incorporar el sistema de corte después de haber validado el movimiento.

## Funcionalidades

- Activar cuchilla.
- Desactivar cuchilla.
- Controlar estado de la cuchilla.
- Parada inmediata.
- Integración con el estado de emergencia.

## Principio de seguridad

La cuchilla no deberá poder activarse en determinadas situaciones inseguras.

Por ejemplo:

- Emergencia activa.
- Error crítico.
- Condición de seguridad no cumplida.

## Pruebas

Inicialmente:

- Robot parado.
- Sistema de corte controlado.
- Pruebas progresivas.
- Sin funcionamiento autónomo.

## Criterio de finalización

El sistema de corte puede activarse y detenerse de forma controlada y segura.

---

# 9. P5 — Sensores y seguridad

## Objetivo

Añadir sensores que permitan detectar situaciones que puedan provocar daños en el robot, en el terreno o a personas/animales.

## Posibles sensores

La selección se realizará posteriormente.

Podrán estudiarse:

- Obstáculos.
- Inclinación.
- Vuelco.
- Elevación del robot.
- Atasco.
- Velocidad.
- Corriente de motores.
- Estado de batería.
- Otros sensores necesarios.

## Seguridad

Definir claramente qué ocurre cuando se detecta:

- Obstáculo.
- Vuelco.
- Elevación.
- Atasco.
- Sobreconsumo.
- Batería baja.
- Error de comunicación.

## Resultado esperado

El robot es capaz de detectar situaciones peligrosas y pasar a un estado seguro.

---

# 10. P6 — Navegación autónoma básica

## Objetivo

Conseguir que el robot pueda desplazarse de forma autónoma.

Esta fase se realizará solamente después de disponer de un sistema móvil estable y seguro.

## Posibles funcionalidades

- Movimiento autónomo.
- Cambio de dirección.
- Evitar obstáculos.
- Control de velocidad.
- Estrategia de cobertura.
- Detección de límites.
- Recuperación después de atasco.

## Tecnología

La tecnología de navegación todavía no queda fijada.

Se estudiarán posteriormente diferentes alternativas, según coste y complejidad.

Podrían considerarse:

- Sensores simples.
- Encoders.
- Bluetooth.
- GPS.
- RTK.
- IMU.
- Visión.
- Combinación de tecnologías.

No se considera obligatorio implementar todas ellas.

---

# 11. P7 — Pruebas en terreno real

## Objetivo

Validar el robot en las condiciones reales donde deberá trabajar.

## Pruebas

- Césped.
- Terreno irregular.
- Pendientes.
- Diferentes alturas de hierba.
- Obstáculos.
- Diferentes condiciones de batería.
- Autonomía.
- Calidad del corte.
- Fiabilidad de navegación.

## Registro

Las pruebas deberán registrar, cuando sea posible:

- Tiempo de funcionamiento.
- Nivel de batería.
- Errores.
- Atascos.
- Pérdida de comunicación.
- Distancia recorrida.
- Problemas de navegación.
- Calidad del corte.

## Criterio de finalización

El robot puede realizar sesiones de trabajo reales de forma controlada y segura.

---

# 12. P8 — Optimización

Una vez validado el concepto se podrán realizar mejoras.

## Posibles mejoras

- Optimización energética.
- Motores.
- Batería.
- Sistema de carga.
- Diseño mecánico.
- Protección contra agua y polvo.
- Cableado.
- Electrónica.
- Comunicación.
- Navegación.
- Software.
- Mantenimiento.

También se estudiará en esta fase si tiene sentido incorporar:

- Carga solar.
- Estación de carga.
- Mejor sistema de comunicaciones.
- Componentes electrónicos definitivos.

---

# 13. P9 — Versión definitiva

## Objetivo

Construir una versión estable y mantenible del robot.

## Incluye

- Diseño mecánico definitivo.
- Electrónica definitiva.
- Software estable.
- Sistema de seguridad.
- Sistema de navegación.
- Sistema de corte.
- Alimentación.
- Carga.
- Protección ambiental.
- Documentación.

## Resultado

Robot cortacésped autónomo preparado para uso habitual.

---

# 14. Regla para avanzar entre fases

Una fase no se considera terminada simplemente porque el hardware o software "funcione".

Debe existir:

1. Implementación.
2. Pruebas.
3. Registro de resultados.
4. Corrección de problemas importantes.
5. Documentación.
6. Validación de la fase.

Después se podrá comenzar la siguiente.

---

# 15. Estrategia de compras

La compra de componentes se realizará de forma progresiva.

### Primera etapa

No comprar componentes específicos del robot si pueden evitarse.

Utilizar:

- ESP32 disponible.
- LEDs.
- Resistencias.
- Pulsadores.
- Cableado.
- Alimentación existente.

### Segunda etapa

Cuando P1 y P2 estén validadas, estudiar las compras necesarias para P3.

### Tercera etapa

Comprar únicamente los componentes necesarios para las siguientes fases.

De esta forma se evita realizar una compra grande antes de saber exactamente qué arquitectura y componentes necesita el robot.

---

# 16. Estado del roadmap

Este documento es un **roadmap inicial**.

No fija todavía:

- Modelo de motores.
- Driver definitivo.
- Batería definitiva.
- Motor de cuchilla.
- Sensores concretos.
- Tecnología definitiva de navegación.
- Sistema de carga.
- Sistema solar.
- Diseño mecánico definitivo.

Estas decisiones se documentarán mediante especificaciones concretas cuando llegue el momento de cada fase.

---

# 17. Próximo paso

El siguiente paso es completar **P0 — Definición y preparación**. El inventario se mantendrá en [hardware-inventory.md](hardware-inventory.md). Al terminar P0, se iniciará **P1 — Prototipo electrónico básico**; la comunicación móvil se añadirá después en P2.

Para cerrar P0 y preparar P1 se deberá:

1. Inventariar el ESP32 y los componentes disponibles, y documentar el inventario.
2. Identificar qué hardware puede utilizarse en el prototipo inicial.
3. Completar la configuración de OpenSpec en el repositorio.
4. Definir el circuito de prueba y los estados iniciales de P1.
5. Crear y validar la especificación OpenSpec de P1.
6. Implementar y probar P1, y documentar los resultados antes de avanzar a P2.

**Principio:** primero demostrar la lógica con LEDs; después controlar dispositivos reales.
