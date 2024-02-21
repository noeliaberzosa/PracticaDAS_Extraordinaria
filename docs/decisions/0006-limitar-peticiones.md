# Limitar peticiones

* Status: proposed
* Date: 2024-02-21

## Context and Problem Statement

Se debe establecer un mecanisnmo que permita limitar las peticiones realizadas por los clientes (en este caso a 3). Se debe evitar que haya un exceso de peticiones irrelevantes (por duplicidad, fallos o ataques) que saturen el servidor.

## Decision Drivers

* RF5.1: Restricción módulo pedido

## Considered Options

* 0006-1 Patron "Retry"
* 0006-2 Patrón "Decorator"

## Decision Outcome

Chosen option: "0006-1 Patron "Retry"", because permite tratar fallos no críticos de manera sencilla

### Positive Consequences

* Mejora de la experiencia del usuario: Al reintentar automáticamente las operaciones fallidas, los usuarios pueden experimentar menos interrupciones y obtener respuestas más rápidas, lo que puede mejorar su experiencia general.
* Tolerancia a fallos: Al incorporar mecanismos de reintento, el sistema es más tolerante a fallos,.
* Reducción de la carga del servidor: En algunos casos, reintentar operaciones puede evitar que los servidores se vean abrumados por un gran número de solicitudes simultáneas, ya que algunos errores pueden resolverse con reintentos en lugar de generar nuevas solicitudes.
* Implementarlo tiene costes reducidos en tiempo y recursos.

### Negative Consequences

* No se limitan las peticiones en todos los contextos
* Retrasos innecesarios: Los reintentos automáticos pueden introducir retrasos innecesarios

## Pros and Cons of the Options

### 0006-1 Patron "Retry"

Un patrón que captura errores de envíos y permite reintentarlos. Se puede limitar el número de reintentos a 3.

* Good, because Permite más flexibilidad para establecer y cambiar facilmente el número de intentos.
* Good, because Ofrece una protección excelente a errores en el envío.
* Bad, because No permite limitar peticiones exitosas.
* Bad, because Posible aumento de latencia

### 0006-2 Patrón "Decorator"

Envolvemos la componente original con un decorator. Al envolverlo implementamos la lódiga que permita limitar las peticiones. El servidor utiliza el componente decorator mediante la inyección de dependencias.

* Good, because Flexibilidad: Diferentes decoradores permiten limitar diferentes tipos de soluciones en diferentes contextos.
* Good, because Separación de preocupaciones: El patrón Decorator te permite separar la lógica de limitación de las peticiones del resto de la funcionalidad del componente. Esto facilita la gestión y el mantenimiento del código, ya que cada decorador se ocupa de una responsabilidad específica.
* Bad, because Posible sobrecarga: Agregar múltiples decoradores puede resultar en una sobrecarga de objetos
* Bad, because Eliminar funcionalidades puede ser complejo.
