# Documento inicial del proyecto

## 1. Propósito

Desarrollar progresivamente un robot cortacésped eléctrico autónomo, con una primera versión equipada con cuchillas. El proyecto avanzará por fases pequeñas y verificables, validando las decisiones técnicas antes de invertir en hardware definitivo.

Este documento establece la visión, los principios de diseño y el alcance inicial. No es todavía una especificación detallada de implementación.

## 2. Visión del proyecto

El objetivo a largo plazo es construir una máquina capaz de desplazarse y cortar césped de forma autónoma, con un diseño modular que permita incorporar y validar sus capacidades de manera gradual.

El desarrollo será incremental y seguirá las fases del roadmap: preparar el proyecto (P0), validar el prototipo electrónico (P1), añadir comunicación y control (P2), incorporar movimiento (P3), integrar el sistema de corte (P4), completar sensores y seguridad (P5), desarrollar navegación autónoma (P6), probar en terreno (P7), optimizar (P8) y consolidar la versión definitiva (P9).

El orden y el alcance de cada fase podrán ajustarse a partir de los resultados de las pruebas.

## 3. Principios de desarrollo

- **Validar antes de escalar:** cada fase debe demostrar su funcionamiento antes de añadir complejidad.
- **Desarrollo incremental:** dividir el trabajo en objetivos pequeños, observables y comprobables.
- **Diseño modular:** separar las funciones para poder cambiarlas o probarlas de forma independiente.
- **Seguridad desde el diseño:** considerar los riesgos de movimiento y, especialmente, del sistema de corte antes de probarlos.
- **Gasto progresivo:** no invertir en componentes definitivos o costosos hasta validar las hipótesis con prototipos.
- **Decisiones documentadas:** registrar requisitos, cambios y decisiones relevantes junto al proyecto.

## 4. Fases iniciales del proyecto

La planificación detallada de las fases se mantiene en [roadmap.md](roadmap.md). Para evitar duplicar esa planificación, este documento fija la visión general y resume el alcance de las primeras fases:

- **P0 — Definición y preparación:** organizar la documentación y el repositorio, preparar OpenSpec e inventariar el hardware disponible.
- **P1 — Prototipo electrónico básico:** validar el ESP32, la lógica y los estados mediante LEDs, sin motores ni cuchilla.
- **P2 — Comunicación y control:** añadir comunicación inalámbrica entre el móvil y el ESP32 y controlar el prototipo de LEDs.

La antigua descripción de una única «Fase 0 — Prototipo de control» queda sustituida por P1 y P2: primero se valida la electrónica y la lógica local; después se añade el control remoto.

### Alcance de P1 — Prototipo electrónico básico

El prototipo inicial estará basado en:

- Una placa ESP32 como controlador.
- LEDs y, si están disponibles, pulsadores para representar y probar salidas, estados y entradas.

P1 valida el arranque, la lógica y las transiciones de estado sin comunicación inalámbrica, tracción ni cuchillas. La comunicación con el móvil se incorpora en P2.

### Criterios de éxito

P1 se considerará completada cuando:

- El ESP32 inicialice y gestione las entradas, salidas y estados definidos para el prototipo.
- Los LEDs representen claramente los estados y las salidas simuladas.
- Se puedan probar la parada, el error y la emergencia.
- Las transiciones previstas puedan repetirse y verificarse sin componentes definitivos.

### Alcance de P2 — Comunicación y control

P2 añadirá comunicación inalámbrica entre el móvil y el ESP32, comandos y respuestas de estado. Los comandos seguirán controlando la lógica y los LEDs; todavía no habrá motores ni cuchilla. El método de comunicación, el protocolo y los criterios de pérdida de conexión se concretarán en la especificación de P2.

## 5. Arquitectura conceptual

La arquitectura inicial se organizará en tres partes:

1. **Interfaz móvil:** presenta controles y muestra el estado conocido del robot.
2. **Comunicación:** transporta órdenes y respuestas entre el móvil y el controlador.
3. **Controlador ESP32:** valida las órdenes, gestiona los estados y coordina las salidas del prototipo, comenzando por los LEDs en P1 y recibiendo órdenes del móvil en P2.

En fases posteriores, las salidas de prueba podrán sustituirse o complementarse con controladores de motores, sensores y otros subsistemas. La interfaz y la lógica de control deberán evolucionar sin quedar ligadas innecesariamente a un componente concreto.

## 6. Movimiento y estados

El movimiento se añadirá después de validar el control básico. La interfaz y el controlador deberán contemplar, como mínimo, órdenes diferenciadas para avanzar, retroceder, girar y detenerse cuando se incorpore la tracción.

El robot deberá tener estados comprensibles y observables. Como base conceptual se consideran:

- **Detenido:** no ejecuta órdenes de movimiento.
- **Manual:** responde a las órdenes válidas de la interfaz.
- **Seguimiento:** estado futuro para desplazarse siguiendo una referencia.
- **Error o comunicación perdida:** interrumpe o inhibe las órdenes que puedan producir movimiento hasta recuperar una condición válida.

Los nombres y las transiciones concretas se definirán en las especificaciones de cada fase.

## 7. Comunicación

La comunicación móvil–ESP32 se validará en P2, después de comprobar en P1 la lógica local y las salidas simuladas. El protocolo deberá permitir enviar órdenes y recibir estados, con mensajes suficientemente claros para detectar órdenes inválidas y situaciones de pérdida de conexión.

La tecnología concreta de comunicación y el formato de los mensajes se decidirán durante la preparación técnica del primer sprint, atendiendo al alcance del prototipo y a los medios disponibles.

## 8. Seguimiento y navegación futura

El seguimiento es una capacidad futura, fuera de P1 y P2. Antes de implementarlo habrá que definir qué referencia seguirá el robot, qué sensores o infraestructura requiere y cómo se comportará ante la pérdida de esa referencia.

La navegación autónoma se abordará después de validar por separado el control, la tracción, los sensores y las medidas de seguridad necesarias.

## 9. Seguridad

La seguridad deberá evolucionar junto con las capacidades del robot. Antes de habilitar movimiento real habrá que definir cómo se detiene el sistema, qué ocurre al perder comunicación y cómo se previenen órdenes inesperadas.

El sistema de corte con cuchillas se tratará como un subsistema independiente y de riesgo elevado. No se integrará ni probará hasta que existan requisitos y medidas de seguridad adecuados para el diseño y el entorno de prueba. P1 y P2 no incluyen cuchillas ni movimiento real.

## 10. Evolución del hardware

El hardware se incorporará de forma gradual:

- **P1:** ESP32, LEDs, resistencias, cableado y alimentación USB; pulsadores si están disponibles.
- **P2:** añade el móvil y el medio de comunicación seleccionado; los LEDs siguen simulando el robot.
- **Fases posteriores:** componentes de tracción, sensores, elementos de seguridad y alimentación, según se validen sus requisitos.
- **Fase de corte:** integración del sistema de cuchillas una vez definidos y comprobados los requisitos del subsistema.
- **Evolución energética:** dimensionamiento de la batería y evaluación de una posible contribución solar cuando se conozcan las necesidades reales de consumo.

No se seleccionará el hardware definitivo de todo el robot por adelantado. Las decisiones de compra se tomarán cuando una fase requiera componentes concretos y sus criterios puedan justificarse.

## 11. Software modular

El software se organizará por responsabilidades, manteniendo separadas, en la medida de lo razonable, la interfaz, la comunicación, la gestión de estados y el control de los subsistemas.

Cada nueva capacidad deberá poder desarrollarse y verificarse sin acoplar innecesariamente el resto del sistema. La estructura concreta del código se decidirá al iniciar la implementación, de acuerdo con las necesidades reales del proyecto.

## 12. Metodología y documentación

El trabajo se organizará mediante fases y sprints. Cada sprint tendrá un objetivo acotado y criterios de aceptación que permitan decidir si está completo.

OpenSpec se utilizará para describir y revisar los cambios funcionales antes de implementarlos. Se inicializará en el repositorio siguiendo la estructura que establezca la herramienta en la versión elegida. Las especificaciones y decisiones se mantendrán versionadas junto al código.

La preparación del repositorio y de sus herramientas pertenece a **P0 — Definición y preparación**. Después se realizarán **P1 — Prototipo electrónico básico** y **P2 — Comunicación y control**, según el orden del roadmap.

## 13. Fuera del alcance inicial

Quedan fuera del alcance de P1 y P2:

- Construir un robot listo para cortar césped.
- Diseñar o poner en funcionamiento las cuchillas.
- Implementar tracción o movimiento físico.
- Implementar seguimiento o navegación autónoma.
- Dimensionar y comprar el hardware definitivo.
- Definir un sistema solar completo.
- Cerrar una arquitectura de producción antes de validar el prototipo.

Estos elementos se tratarán en fases posteriores mediante requisitos y criterios propios.

## 14. Regla de inversión

No se comprará hardware definitivo ni se realizarán inversiones relevantes hasta que la fase correspondiente haya validado la necesidad, los requisitos y la viabilidad de los componentes. Se priorizarán prototipos económicos y pruebas pequeñas para reducir el riesgo de comprar material que luego no encaje con el diseño.

## 15. Criterio general de éxito

El proyecto avanzará correctamente si cada fase entrega una capacidad demostrable, documenta sus decisiones y deja una base útil para la siguiente fase, manteniendo la seguridad, la modularidad y el gasto bajo control.

