# Spec Delta

## Purpose

Define el alcance verificable de P1: preparar un entorno de simulación funcional y usarlo para probar el movimiento básico de un robot virtual sin compras de hardware.

## ADDED Requirements

### Requirement: Entorno de simulación reproducible
El proyecto SHALL documentar e instalar una herramienta de simulación compatible con el equipo de desarrollo y SHALL verificarla abriendo y ejecutando un ejemplo incluido o equivalente.

#### Scenario: Preparación inicial del entorno
- **WHEN** se selecciona la herramienta tras comprobar sus requisitos
- **THEN** se documentan el nombre, versión y pasos de instalación
- **AND** se ejecuta un ejemplo que confirma que el simulador funciona

#### Scenario: El equipo no cumple los requisitos
- **WHEN** la herramienta seleccionada no puede ejecutarse en el equipo
- **THEN** se registra la limitación y se evalúa otra opción antes de iniciar el modelo

### Requirement: Modelo virtual configurable
El proyecto SHALL representar un robot virtual con movimiento diferencial y un escenario de prueba, manteniendo configurables sus parámetros principales y etiquetando cada valor como conocido, estimado o pendiente.

#### Scenario: Parámetros del modelo
- **WHEN** se define o modifica un parámetro del robot o del escenario
- **THEN** queda registrado su valor, unidad, procedencia y nivel de certeza

#### Scenario: Parámetro pendiente
- **WHEN** no se dispone de un valor confirmado
- **THEN** el modelo usa un valor provisional explícito o deja la característica desactivada, y documenta el supuesto

### Requirement: Pruebas de movimiento básico
El modelo SHALL permitir ejecutar y observar avance, retroceso, giro y parada, y repetir una prueba con la misma configuración.

#### Scenario: Órdenes básicas
- **WHEN** se envía cada orden de movimiento al robot virtual
- **THEN** el robot responde en la dirección esperada y STOP detiene el movimiento simulado

#### Scenario: Repetición de escenario
- **WHEN** se ejecuta de nuevo una prueba con los mismos parámetros y órdenes
- **THEN** se puede comparar el resultado con la ejecución anterior

### Requirement: Límites de los resultados
Los resultados de P1 SHALL identificar supuestos y limitaciones, y SHALL distinguir resultados de simulación de mediciones físicas.

#### Scenario: Informe de una prueba
- **WHEN** se documenta el resultado de una simulación
- **THEN** se incluyen configuración, órdenes, resultado observado y limitaciones relevantes
