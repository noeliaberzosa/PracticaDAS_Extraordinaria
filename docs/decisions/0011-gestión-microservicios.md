# Gestión Microservicios

* Status: proposed
* Date: 2024-02-28

## Context and Problem Statement

Para poder ejecutar los microservicios de manera eficiente es necesario tener componente que ayude al desarrollo de dicha acción.

## Decision Drivers

* RF-8: Gestión de Microservicios

## Considered Options

* 0011-1- Spring Cloud
* 0011-2- Kubernetes
* 0011-3- Consul

## Decision Outcome

Chosen option: "0011-2-Kubernetes", because si usásemos Spring Cloud dependeríamos completamente de la herramienta Spring Boot, lo que conllevaría un extra de dificultad. Por otro lado, si usásemos Consul, nos ocurre algo parecido, pero en este caso dependeríamos de una infraestructura adciional.

### Positive Consequences

* Alta tolerancia a fallos.
* Fácil de desplegar, actualizar y escalar los microservicios de manera eficiente y confiable.
* Gestión de recursos.

### Negative Consequences

* Configurar, mantener y solucionar problemas en un clúster de Kubernetes puede ser desafiante.

## Pros and Cons of the Options

### 0011-1- Spring Cloud

Spring Cloud es una herramienta de código abierto construida en Java que facilita el uso de marcos para crear microservicios y aplicaciones web proporcionando bibliotecas.

* Good, Permite que los microservicios se escalen fácilmente para manejar picos de carga o aumentos en la demanda.
* Good, Permite desplegar rápidamente microservicios autocontenidos y autónomos.
* Good, Permite gestionar típicos problemas relacionados con los microservicios: registro, enrutamiento, descubrimiento de servicios...
* Bad, La adopción de Spring Cloud puede requerir tiempo y esfuerzo para que los equipos se familiaricen con los conceptos y herramientas asociadas. 
* Bad, El uso de Spring Cloud implica una dependencia de la plataforma Spring.

### 0011-2- Kubernetes

Kubernetes es una plataforma de código abierto ampliamente utilizada para la orquestación de contenedores, y es especialmente valiosa en entornos de microservicios.

* Good, Puede escalar horizontalmente las réplicas de los contenedores según la demanda, lo que permite manejar picos de tráfico y garantizar un rendimiento óptimo.
* Good, Proporciona mecanismos de autorreparación y reprogramación automáticos para garantizar que los microservicios estén siempre disponibles.
* Good, Automatización y la reproducibilidad de los despliegues, debido a que utiliza una arquitectura basada en declaraciones.
* Bad, A gestión de un clúster de Kubernetes pueden generar costos adicionales.
* Bad, Puede llevar a una sobrecarga de complejidad.

### 0011-3- Consul

Consul es una herramienta popular utilizada en entornos de microservicios para el registro y descubrimiento de servicios, así como para la gestión de configuraciones. 

* Good, Proporciona un mecanismo robusto para registrar los servicios disponibles y descubrir dinámicamente sus ubicaciones y estados. Gracias a esto la comunicación se vuelve más simple entre microservicios en entornos distribuidos y escalables.
* Good, Integración con otras herramientas y plataformas utilizadas en el ecosistema de microservicios (Kubernetes, Docker...).
* Good, Ofrece una gestión centralizada de la configuración, permitiendo así la actualización dinámica de la configuración de la aplicación.
* Bad, El despliegue de Consul requiere infraestructura adicional.
* Bad, Su configuración puede requerir tiempo y esfuerzo, especialmente para entornos grandes o complejos.
