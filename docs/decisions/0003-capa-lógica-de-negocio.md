# Capa Lógica de Negocio

* Status: proposed
* Date: 2024-02-14

## Context and Problem Statement

Se necesita estructurar la capa lógica de negocios para incorporar los módulos de los servicios provenientes de una arquitectura monolítica. Esta capa necesita seguir una arquitectura basada en microservicios.

## Decision Drivers

* RF01: Migración a una arquitectura basada en microservicios
* RF07: Desacople del módulo reparto y rutas
* RF010: Relación Incidencias-Repartos

## Considered Options

* 0003-1-Separar los microservicios según los módulos
* 0003-2-Separar los microservicios por dominio

## Decision Outcome

Chosen option: "0003-2-Separar los microservicios por dominio", because simplifica la estructura manteniendo la calidad del diseño.

### Positive Consequences

* Se va a trabajar con una estructura más sólida, duradera y mantenible
* Disminuye futuros costes de desarrollo
* Mayor flexibilidad para diseñar internamente la capa

### Negative Consequences

* Se deben dedicar más recursos a corto plazo (en diseño, planificación y desarrollo).

## Pros and Cons of the Options

### 0003-1-Separar los microservicios según los módulos

Una con los módulos de la lógica de negocio de la empresa y otra que se encarga de gestionar las interacciones entre servicios

* Good, because Hay un intermediario en todas las interacciones
* Bad, because Es una estructura extra con una función que tal vez se podría realizar sin ella

### 0003-2-Separar los microservicios por dominio

Construir los microserviciós acorde al dominio. Juntando o separándo los módulos proporcionados según sea necesario.

* Good, because permite diseñar una estructura nueva adaptada a las necesidades de la arquitectura de microservicios.
* Good, because el mantenimiento sera menos costoso
* Bad, because se pueden incrementar los costes de desarrollo más que en la otra opción
