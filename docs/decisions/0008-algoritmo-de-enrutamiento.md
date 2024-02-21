# Algoritmo de enrutamiento

* Status: proposed
* Date: 2024-21-02

## Context and Problem Statement

Se cuenta con 2 algoritmos de optimización de modo que se gestionen las rutas en función de la demora de los camiones, teniendo en cuenta que se toma como límite 30 minutos de demora.

## Decision Drivers

* RF-6: Algoritmos de optimización
* Estructura mantenible y escalable que permita elegir de manera eficiente

## Considered Options

* 0008-1-Patrón strategy
* 0008-2-Motor de Reglas
* 0008-3-Tabla de Enrutamiento

## Decision Outcome

Chosen option: "0008-1-Patrón strategy", because este enfoque proporciona la modularidad necesaria para agregar, modificar y seleccionar algoritmos de manera dinámica, al tiempo que mantiene un buen rendimiento y facilita el mantenimiento del sistema a largo plazo.

## Pros and Cons of the Options

### 0008-1-Patrón strategy

Cada algoritmo de enrutamiento se encapsula en su propia clase y se puede intercambiar fácilmente según sea necesario.

* Good, because cada algoritmo está encapsulado en su propia clase, lo que facilita la adición y modificación de algoritmos.
* Good, because los cambios en un algoritmo no afectan a otros componentes del sistema.
* Good, because permite intercambiar algoritmos dinámicamente en tiempo de ejecución.
* Bad, because requiere una estructura adicional para manejar la selección dinámica de algoritmos.

### 0008-2-Motor de Reglas

Evalúa las condiciones actuales, como la demora del camión, y selecciona dinámicamente el algoritmo adecuado según un conjunto predefinido de reglas.

* Good, because permite definir reglas flexibles para seleccionar algoritmos en función de múltiples variables.
* Good, because no requiere cambios en la estructura principal del sistema para agregar nuevos algoritmos o criterios de selección.
* Bad, because implementar y mantener un motor de reglas puede ser más complejo que otras soluciones.

### 0008-3-Tabla de Enrutamiento

Configurada externamente para asociar diferentes condiciones (como la demora del camión) con algoritmos específicos, permitiendo una rápida selección basada en la consulta de esta tabla.

* Good, because es una solución directa y fácil de entender para asociar condiciones con algoritmos.
* Good, because la selección de algoritmos se realiza consultando una tabla, lo que puede ser rápido y eficiente.
* Bad, because menos flexible que otras soluciones, ya que la lógica de selección está predefinida en la tabla.
* Bad, because requiere mantenimiento manual de la tabla de enrutamiento.
