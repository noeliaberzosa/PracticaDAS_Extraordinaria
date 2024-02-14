# ACCESO BASE DE DATOS

* Status: proposed
* Date: 2024-02-14

## Context and Problem Statement

Necesitamos gestionar el acceso a la base de datos. Tenemos dos bases de datos SQL, una para pedidos y otra para clientes.

## Decision Drivers

* RF2 Acceso a las bases de datos
* Mantener la seguridad en el acceso

## Considered Options

* SQL Server Native Client
* Open Database Connectivity

## Decision Outcome

Chosen option: "SQL Server Native Client", because En primer lugar y fundalmente porque al trabajar sobre BBDD SQL neceistamos un gestor de datos SQL.

### Positive Consequences

* Rendimiento: SQL Server Native Client está optimizado para trabajar con SQL Server, lo que significa que puede ofrecer un mejor rendimiento en comparación con otros controladores genéricos o universales.
* Características avanzadas: SQL Server Native Client proporciona acceso a todas las características avanzadas de SQL Server, como procedimientos almacenados, transacciones distribuidas y notificaciones de cambio.
* Seguridad: Al ser específico de SQL Server, SQL Server Native Client puede ofrecer opciones de seguridad avanzadas, como la autenticación integrada de Windows y el cifrado de datos.
* Mantenimiento y compatibilidad: Microsoft proporciona soporte y actualizaciones continuas para SQL Server Native Client, lo que garantiza su compatibilidad con las versiones más recientes de SQL Server y ayuda a mantener el sistema actualizado y seguro.

### Negative Consequences

* Dependencia de una tecnología específica
* Limitaciones de plataforma
* Costo de licenciamiento
* Posible complejidad de configuración

## Pros and Cons of the Options

### SQL Server Native Client

Es un controlador de datos desarrollado por Microsoft que permite a las aplicaciones comunicarse con una base de datos SQL Server.Es una opción popular para desarrolladores que trabajan con aplicaciones y sistemas que requieren una conexión directa y eficiente con una base de datos SQL Server.

* Good, because está diseñado específicamente para trabajar con SQL Server, lo que puede resultar en un rendimiento más rápido y eficiente en comparación con otros controladores genéricos.
* Good, because se tiene acceso completo a todas las características avanzadas de SQL Server, como procedimientos almacenados, transacciones distribuidas y notificaciones de cambio.
* Good, because ofrece opciones de seguridad avanzadas, incluida la autenticación integrada de Windows y el cifrado de datos, lo que ayuda a garantizar la seguridad de los datos almacenados en la base de datos.
* Good, because al ser desarrollado y mantenido por Microsoft, garantiza una buena compatibilidad con las versiones más recientes de SQL Server y proporciona soporte continuo y actualizaciones de seguridad.
* Bad, because se está vinculando el sistema a una tecnología específica de Microsoft, lo que puede dificultar la migración a otras plataformas de bases de datos en el futuro.
* Bad, because está diseñado para funcionar en sistemas operativos compatibles con Windows, lo que puede ser una limitación si se desea implementar en entornos que utilicen sistemas operativos diferentes.
* Bad, because aunque en sí mismo puede ser gratuito, SQL Server como producto comercial puede implicar costos de licenciamiento que pueden ser significativos, especialmente en entornos empresariales con grandes volúmenes de datos y usuarios.

### Open Database Connectivity

Es un estándar de conectividad de datos que permite a las aplicaciones acceder y manipular datos en una variedad de bases de datos a través de un único conjunto de interfaces.

* Good, because es compatible con una amplia gama de sistemas operativos y plataformas, incluyendo Windows,LInux,macOS y otros.
* Good, because facilita la interoperabilidad entre diferentes sistemas de gestión de bases de datos
* Good, because la configuración de conexión es sencilla y se puede realizar en pocos pasos
* Good, because es eficiente en cuanto a rendimiento
* Bad, because introduce un cierto nivel de overhead(costo adicional o  uso de recursos que no están directamente relacionados con la tarea principal), en términos de rendimiento
* Bad, because el overhead puede implicar el uso de recursos adicionales como memoria, ancho de banda de red, capacidad de almacenamiento o potencia de procesamiento
* Bad, because el overhead puede implicar complejidad adicional
* Bad, because el overhead puede ser el resultado de ineficiencias en la implementación de un sistema
