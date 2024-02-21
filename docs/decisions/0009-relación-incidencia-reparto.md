# Relación Incidencia-Reparto

* Status: proposed
* Date: 2024-02-21

## Context and Problem Statement

Se quiere relacionar los módulos Incidencia y Reparto de modo que se comunique cualquier tipo de incidencia a los gestores de las rutas, manteniéndolos al tanto de la situación.
Se tendrán en cuenta 3 tipos de incidencias: camión averiado00, demora y no entrega de pedidos

## Decision Drivers

* RF-5: Módulo Pedido

## Considered Options

* 0009-1-Conexión del módulo Incidencias con Reparto a través del Gestor de Pedidos
* 0009-2-Conexión directa del módulo Incidencias con el Reparto

## Decision Outcome

Chosen option: "0009-1-Conexión del módulo Incidencias con Reparto a través del Gestor de Pedidos", because conlleva la transferencia de todas las comunicaciones relacionadas con la lógica de negocio al Gestor de Pedidos. Además, al optar por esta integración, la funcionalidad de notificación de incidencias se vuelve más escalable, lo que nos permite estar preparados para cualquier eventualidad futura en la que puedan surgir nuevos requisitos que necesiten la comunicación de incidencias dentro de alguna parte de la lógica de negocio.

### Positive Consequences

* Mejora la escalabilidad
* Centralización de la comunicación
* Facilita la coordinación

### Negative Consequences

* Mayor complejidad
* Dependencia excesiva de GestorPedidos
* Posible sobrecarga de GestorPedidos

## Pros and Cons of the Options

### 0009-1-Conexión del módulo Incidencias con Reparto a través del Gestor de Pedidos

El componente GestorPedidos hace de intermediario entre los  clientes, pedidos, el reparto y rutas y las incidencias, comunicando dichas funcionalidades entre sí.

* Good, because mejora la escalabilidad, lo que permite una estructura más flexible y escalable para manejar futuros requisitos de comunicación de incidencias dentro de la lógica de negocio.
* Good, because centralización de la comunicación facilitando el seguimiento y la resolución de incidencias al centralizar la gestión de comunicaciones en GestorPedidos.
* Good, because coordinación mejorada lo cual puede promover una mejor coordinación entre los componentes del sistema al canalizar todas las comunicaciones relacionadas con incidencias a través de una única entidad.
* Bad, because mayor complejidad ya que agrega una capa adicional de complejidad al sistema, lo que puede dificultar su mantenimiento y comprensión en futuras modificaciones.
* Bad, because crea una fuerte dependencia del GestorPedidos, lo que podría ser problemático si hay fallas o problemas en GestorPedidos.
* Bad, because posible sobrecarga del GestorPedidos si el volumen de incidencias aumenta significativamente con el tiempo, lo que podría afectar el rendimiento del sistema.

### 0009-2-Conexión directa del módulo Incidencias con el Reparto

Las incidencias ocurren con los repartos y las notificaciones de las incidencias se deben  realizar al módulo de repartos y rutas, por tanto sería una opción bastante lógica.

* Good, because simplicidad al evitar la integración con GestorPedidos, se mantiene una estructura más simple y directa en el sistema.
* Good, because reduce la dependencia de una única clase para la gestión de incidencias, lo que puede disminuir el riesgo de problemas si ocurren fallas en un componente específico.
* Good, because permite un mayor grado de control sobre la gestión de incidencias al evitar la centralización en una única entidad.
* Bad, because menor escalabilidad ya qye puede dificultar la adaptación a futuros requisitos si surgen necesidades adicionales de comunicación de incidencias dentro de la lógica de negocio.
* Bad, because dificultad en la coordinación, la falta de centralización puede dificultar la coordinación entre los diferentes componentes del sistema en relación con las incidencias.
* Bad, because podría resultar en la duplicación de esfuerzos si la gestión de incidencias se aborda de manera independiente en diferentes partes del sistema, lo que podría llevar a inconsistencias y complicaciones adicionales.
