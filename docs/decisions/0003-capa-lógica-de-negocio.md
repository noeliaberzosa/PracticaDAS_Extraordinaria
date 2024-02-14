# Capa Lógica de Negocio

* Status: proposed
* Date: 2024-02-14

## Context and Problem Statement

Se quiere ofrecer una variedad de servicios que abarcan diferentes aspectos de su negocio, desde la gestión de clientes hasta el procesamiento de pagos. Estos servicios serán implementados como módulos independientes para garantizar la modularidad y la reutilización del código.

## Decision Drivers

* Respetar la estructura por capas
* Modularizar

## Considered Options

* Dividir los servicios en múltiples capas según su funcionalidad
* Agrupar los servicios en una única capa

## Decision Outcome

Chosen option: "Una única capa", because simplifica la estructura manteniendo la calidad del diseño.

## Pros and Cons of the Options

### Dividir los servicios en múltiples capas según su funcionalidad

Una con los módulos de la lógica de negocio de la empresa y otra que se encarga de gestionar las interacciones entre servicios

* Good, because Hay un intermediario en todas las interacciones
* Bad, because Es una estructura extra con una función que tal vez se podría realizar sin ella

### Agrupar los servicios en una única capa

Sería juntar los módulos de la lógica de negocio de la empresa y el gestor de servicios en una misma capa

* Good, because El grado cohesión es muy alto
* Good, because Es más fácil de desarrollar
* Bad, because Acopla un poco más los módulos de la empresa
