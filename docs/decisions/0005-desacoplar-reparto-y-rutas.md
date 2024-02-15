# Desacoplar Reparto y rutas

* Status: proposed
* Date: 2023-11-03

## Context and Problem Statement

Necesitamos desacoplar el módulo "Reparto y rutas" en dos: "Reparto", "Rutas". Se debe respetar la decisión 0003 (dividir microservicios por dominio).

## Decision Drivers

* RF07 Desacople del módulo reparto y rutas
* RF08: Relación Incidencias-Repartos

## Considered Options

* 0005-1-Separarlos en dos clases
* 0005-2-Mantenerlos juntos

## Decision Outcome

Chosen option: "0005-1-Separarlos en dos clases", because nos permite cumplir con la decisión previa de dividir los microservicios por dominio (Decisión 0003).

### Positive Consequences

* Separar la lógica de "Reparto" de la lógica de "Rutas" puede facilitar el mantenimiento, la escalabilidad y la evolución independiente de cada una de estas funcionalidades.
* Mejor manejo de errores y una mayor claridad en la responsabilidad de cada microservicio.
* Se pueden gestionar de manera más eficiente en el contexto de cada funcionalidad específica.

### Negative Consequences

* Mayor complejidad inicial.
* Posible fragmentación excesiva

## Pros and Cons of the Options

### 0005-1-Separarlos en dos clases

Una vez el modulo Reparto elige una flota de transporte para los pedidos de unos determinados clientes, llama al módulo Rutas para calcular la ruta óptima de los camiones

* Good, because tiene la misma función que antes del desacople pero con la ventaja de que está modularizado
* Good, because permite buscar soluciones arquitectónicas con más opciones
* Good, because facilita la comprensión del código para futuros desarrolladores
* Bad, because son componentes con un grado alto de cohesión y puede ser dificil desacoplarlos

### 0005-2-Mantenerlos juntos

Respetar el módulo original proporcionado por la empresa

* Good, because se emplean menos recursos en el diseño y desarrollo
* Good, because separar dos componentes tan acoplados y cohesionados puede ser muy complejo
* Bad, because no se respeta la decisión 0003
* Bad, because el alto acoplamiento tendrá efectos negativos en el mantenimiento futuro
