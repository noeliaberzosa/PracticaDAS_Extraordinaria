# Módulo Estadísticas

* Status: proposed
* Date: 2024-02-28

## Context and Problem Statement

Contamos con un módulo de estadísticas que se encarga de proporcionar información acerca del estado de los pedidos y la situación a tiempo real de los camiones con los pedidos.
Queremos decidir si el módulo estadísticas se encargará de toda la tarea, o si se usará un gestor de Datos como intermediario

## Decision Drivers

* RF-13:Módulo Estadísticas

## Considered Options

* 0012-1-Conexión del módulo Estadísticas con el Gestor de Datos
* 0012-2-Módulo Estadísticas trabaja por su cuenta

## Decision Outcome

Chosen option: "0011-1-Conexión del módulo Estadísticas con el Gestor de Datos", because implica la transferencia de todas las comunicaciones relacionadas con la lógica de negocio al Gestor de Datos. Además, al optar por esta integración, el módulo de estadísticas se vuelve más escalable, lo que nos permite estar preparados para cualquier eventualidad futura en la que puedan surgir nuevos requisitos que necesiten la comunicación de estadísticas dentro de alguna parte de la lógica de negocio. Además así conseguimos un sistema más robusto y eficiente en general.

### Positive Consequences

* Mejora la escalabilidad
* Centralización de datos
* Integración con otras funcionalidades
* Facilita el análisis

### Negative Consequences

* Dependencia del Gestor de Datos
* Mayor complejidad
* Riesgo de seguridad
* Riesgo de sobrecarga de datos

## Pros and Cons of the Options

### 0012-1-Conexión del módulo Estadísticas con el Gestor de Datos

El componente GestorDatos actúa de intermediario con el módulo Estadísticas, para facilitar la comunicación del estado de los pedidos a tiempo real

* Good, because mejora en la gestión de datos, integrando el Módulo de Estadísticas con el Gestor de Datos optimiza el manejo de datos, garantizando una mejor organización y accesibilidad de la información estadística.
* Good, because escalabilidad mejorada permitiendo una gestión más eficiente de grandes volúmenes de datos estadísticos a medida que el sistema crece.
* Good, because mejora en la capacidad analítica arovechando las capacidades del Gestor de Datos puede conducir a herramientas y técnicas analíticas mejoradas para procesar datos estadísticos, permitiendo un análisis más perspicaz y una toma de decisiones más informada.
* Good, because repositorio centralizado de datos, fomentando la consistencia y precisión en todo el sistema.
* Bad, because dependencia del Gestor de Datos lo cuál introduce un único punto de falla, lo que plantea riesgos en caso de mal funcionamiento o interrupciones del sistema.
* Bad, because mayor complejidad adicional, especialmente si no se gestionan adecuadamente los aspectos de diseño y mantenimiento, lo que podría dificultar su comprensión y mantenimiento en el futuro.
* Bad, because proceso de integración complejo, puede requerir un tiempo y esfuerzo sustanciales para garantizar una compatibilidad y funcionalidad perfectas, lo que podría ocasionar retrasos o complicaciones en la implementación.
* Bad, because riesgos potenciales de seguridad de datos, centralizar datos estadísticos dentro del Gestor de Datos plantea preocupaciones sobre la seguridad y privacidad de los datos, lo que requiere medidas sólidas para proteger la información sensible contra accesos no autorizados o brechas de seguridad.

### 0012-2-Módulo Estadísticas trabaja por su cuenta

Todo lo relatuvo a la información de los pedidos, de los clientes y del estado a tiempo real de los camiones de reparto será llevada única y exclusivamente por el módulo Estadísticas

* Good, because sencillez en la gestión de datos, al tener un solo módulo encargado de manejar todos los aspectos relacionados con las estadísticas, se simplifica la gestión y mantenimiento de los datos.
* Good, because reduce la dependencia de otros componentes, al operar por su cuenta, no depende de otros componentes del sistema para acceder a la información que necesita, lo que puede reducir la complejidad y los posibles puntos de falla.
* Good, because mayor autonomía, al trabajar de manera independiente, el módulo de Estadísticas tiene un mayor control sobre sus propios procesos y datos, lo que puede facilitar la implementación de cambios y actualizaciones específicas.
* Bad, because escalabilidad limitada, si hay un crecimiento significativo en la cantidad de datos o en la complejidad de las operaciones, el módulo de Estadísticas trabajando por su cuenta podría no ser capaz de escalar eficientemente para manejar las demandas adicionales.
* Bad, because dificultad en la integración futura, al ser independiente, se puede enfrentar dificultades en la integración con otras funcionalidades del sistema en el futuro, lo que podría limitar su capacidad para aprovechar nuevas oportunidades o tecnologías.
* Bad, because posible duplicación de funcionalidades cuando otros componentes del sistema también necesiten acceder a la misma información que maneja el módulo de Estadísticas, lo que podría llevar a inconsistencias y dificultades en la gestión de la información.
