# Gateway

* Status: proposed
* Date: 2024-02-14

## Context and Problem Statement

Se necesita implementar un protocolo HTTP/REST mediante un componente Gateway que actúe de intermediario recibiendo peticiones de la capa cliente y las procese para enviárselas a la capa de servicios y viceversa.

## Decision Drivers

* RF03: Cambio a protocolo HTTP/REST

## Considered Options

* 0002-1-Desarrollar un gateway personalizado
* 0002-2-Usar un Gateway existente

## Decision Outcome

Chosen option: "0002-2-Usar un Gateway existente", because dado el requerimiento de implementar HTTP/REST y la disponibilidad de soluciones maduras como Kong y AWS API Gateway, creemos que es más beneficioso aprovechar estas herramientas existentes en lugar de desarrollar y mantener nuestro propio gateway personalizado. Sobre todo cuando estamos ante una aplicación compleja y extensa en la cual se preveen mejoras en el futuro.

### Positive Consequences

* Nos permitirá ahorrar tiempo y recursos, al tiempo que nos beneficiamos de la experiencia y la robustez de las soluciones establecidas.
* Se puede implementar en entornos locales y en la nube.

### Negative Consequences

* Las actualizaciones y cambios requieren especial atención para garantizar la compatibilidad con las versiones anteriores.

## Pros and Cons of the Options

### 0002-1-Desarrollar un gateway personalizado

Desarrollar un gateway personalizado que maneje las solicitudes HTTP/REST entrantes y salientes.

* Good, because permite un control total sobre la implementación y personalización del gateway según las necesidades específicas del proyecto.
* Bad, because requiere un esfuerzo de desarrollo considerable y mantenimiento continuo.

### 0002-2-Usar un Gateway existente

Utilizar un gateway existente, como Kong, API Gateway de AWS, o similar.

* Good, because Puede reducir el tiempo de desarrollo y la carga de mantenimiento al aprovechar soluciones probadas y preexistentes.
* Bad, because Podría requerir ajustes y configuraciones para adaptarse a los requisitos específicos del proyecto.
