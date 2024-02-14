# Inclusión Componente Gateway

* Status: proposed
* Date: 2024-02-14

## Context and Problem Statement

Se necesita implementar un protocolo HTTP/REST mediante un componente Gateway que actúe de intermediario recibiendo peticiones de la capa cliente y las procese para enviárselas a la capa de servicios y viceversa.

## Decision Drivers

* RF03: Cambio a protocolo HTTP/REST

## Considered Options

* 0002-1-Kong
* 0002-2-Express.js

## Decision Outcome

Chosen option: "0002-1-Kong", because estamos ante una aplicación compleja y extensa (se preveen mejoras en el futuro):

### Positive Consequences

* Complatible con contenedores.
* Se puede implementar en entornos locales y en la nube.
* En comparación con Express.js es un marco completo por lo que no se necesitan dependencias.
* El código fuente es modificable.
* Al ser código abierto, cuanta con una gran comunidad de usuarios y desarrolladores.

### Negative Consequences

* Las actualizaciones y cambios requieren especial atención para garantizar la compatibilidad con las versiones anteriores.

## Pros and Cons of the Options

### 0002-1-Kong

Kong Gateway, comúnmente conocido como Kong, es una puerta de enlace (gateway) de API de código abierto y una capa de gestión de microservicios. Está diseñado para facilitar la comunicación entre varios microservicios y gestionar el tráfico que fluye entre ellos. Kong ayuda a simplificar la implementación, escalabilidad y gestión de APIs y microservicios al proporcionar un punto centralizado para manejar tareas como autenticación, autorización, límites de velocidad, registro, entre otras.

* Good, because Es un marco completo. Incluye gestión de tráfico, seguridad, monitoreo; lo que facilita la administración de APIs y mocroservicios.
* Good, because Tiene escalabilidad. Implica que puede manejar un aumento en el tráfico y el número de peticiones mediante la adición de más instancias según sea necesario.
* Good, because Tiene flexibilildad. Kong es altamente configurable y se puede adaptar a una variedad de necesidades y entornos.
* Bad, because Tiene documentación compleja.Esto supone que a la hora de implementar funcionalidades usando Kong los desarrolladores encuentren un mayor número de dificultades.
* Bad, because Se necesitan un gran número de recursos. Al ser un sistema completo, puede requerir un mayor número de recursos en términos de hardware y memoria.

### 0002-2-Express.js

Express es una API gateway de microservicios, la cual no tiene servidor que se encuentra en el corazón de cualquier arquitectura de microservicios o arquitecturas que no tengan servidor.

* Good, because No importa el lenguaje o la plataforma que se esté utilizando Express asegura los microservicios y estos funcionan sin servidor.
* Good, because Es portátil. Puede ejecutarse en cualquier lugar con Docker en la nube pública o privada.
* Good, because Es simple. Usa una única configuración para controlarlo todo, detección automática y recarga en caliente de cambios de configuración.
* Bad, because Complejidad en aplicaciones grandes. A medida que las aplicaciones crecen en tamaño y complejidad, Express puede volverse más difícil de mantener.Lo que desemboca en problemas de organización y escalabilidad.
* Bad, because Falta de características integradas. Express no es un marco completo, por lo que no proporciona muchas características integradas, como autenticación, autorización, validación de formularios, etc. Esto implica que se necesiten bibliotecas de terceros o desarrollar una propia para ciertas funcionalidades.
