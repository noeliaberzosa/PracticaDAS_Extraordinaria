# Estilo arquitectónico

* Status: proposed
* Date: 2024-07-02

## Context and Problem Statement

Se requiere migrar un sistema de arquitectura monolítica a uno basado en microservicios.

## Decision Drivers

* RF01: Migración a una arquitectura basada en microservicios

## Considered Options

* 0001-1-Por capas
* 0001-2-Cliente-servidor

## Decision Outcome

Chosen option: "0001-2-Cliente-servidor", because Elegir la arquitectura cliente-servidor para el sistema descrito tiene sentido por varias razones:

Centralización de la lógica empresarial: La arquitectura cliente-servidor permite centralizar la lógica empresarial en el servidor, lo que facilita la gestión y la actualización de la lógica de negocio. Dado que el sistema actual se basa en dos bases de datos SQL y varios módulos críticos y no críticos, tener un servidor centralizado para gestionar estos datos y funcionalidades simplificaría su administración y mantenimiento.

Seguridad: Al tener un servidor centralizado, es más fácil implementar medidas de seguridad robustas y consistentes en un solo lugar. Esto es particularmente importante para componentes críticos como Pagos, donde la seguridad es un requisito importante.

Separación de responsabilidades: La arquitectura cliente-servidor permite una clara separación de responsabilidades entre el cliente y el servidor. Esto es beneficioso para un sistema con múltiples módulos y funcionalidades como el descrito, ya que cada parte puede enfocarse en su tarea específica sin interferir con otras áreas del sistema.

### Positive Consequences

* Respeta la independencia de los módulos.
* Muchos programadores están muy familiarizados.
* Sistema mantenible.
* Es posible llevar a cabo un desarrollo paralelo en cada capa.

### Negative Consequences

* Dependencia del servidor. En caso de fallo en este, el proyecto caería. Aunque se podría solucionar con copias de seguridad y varias servidores corriendo en paralelo para que cuando falle uno transportar todo el tráfico a uno funcional.
* Saturación del servidor tras muchas interacciones.

## Pros and Cons of the Options

### 0001-1-Por capas

Esta arquitectura organiza el sistema en capas lógicas, donde cada capa representa una parte del sistema con un propósito específico. Las capas se comunican entre sí de manera jerárquica, con cada capa ofreciendo servicios a la capa anterior y consumiendo servicios de la capa posterior.

* Good, because Modularidad y separación de preocupaciones, lo que facilita el mantenimiento y la evolución del sistema.
* Good, because Escalabilidad, ya que cada capa puede escalarse de forma independiente según sea necesario.
* Good, because Mejora de la reutilización del código y la interoperabilidad, ya que las capas pueden ser intercambiables o sustituibles.
* Bad, because Posible sobrecarga de comunicación entre capas, especialmente en sistemas con muchas capas.
* Bad, because Mayor complejidad debido a la gestión de la comunicación y la sincronización entre capas.
* Bad, because Dificultad para adaptarse a cambios en los requisitos si las capas están demasiado acopladas.

### 0001-2-Cliente-servidor

El sistema se divide en dos partes principales: el cliente, que solicita servicios o recursos, y el servidor, que proporciona esos servicios o recursos.

* Good, because Desacoplamiento entre la interfaz de usuario y la lógica del negocio, lo que facilita la escalabilidad y la evolución del sistema.
* Good, because Mejora de la seguridad, ya que los servicios pueden ser centralizados y gestionados en un servidor seguro.
* Bad, because Dependencia de la disponibilidad y rendimiento del servidor centralizado.
* Bad, because Puede haber cuellos de botella en el servidor si hay un gran número de clientes simultáneos.
* Bad, because Requiere una infraestructura de red robusta y confiable para la comunicación entre cliente y servidor.
