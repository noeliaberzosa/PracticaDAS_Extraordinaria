# Selección de la Pasarela de pago

* Status: proposed
* Date: 2024-02-21

## Context and Problem Statement

Se necesita comunicarse con una pasarela de pago externa para realizar los pedidos de manera online

## Decision Drivers

* RF09: Acceso a la pasarela de pago

## Considered Options

* 0007-1-Adyen
* 0007-2-PayPal

## Decision Outcome

Chosen option: "0007-1-Adyen", because es una plataforma muy adapatable y ofrece soluciones a nivel mundial

### Positive Consequences

* Ofrece gran variedad de métodos de pago.
Proporciona herramientas robustas de informes y análisis que permiten a los
* Es capaz de procesar pagos en diversas monedas.
* comerciantes realizar un seguimiento detallado de las transacciones y tomar decisiones informadas sobre su estrategia de pago.

### Negative Consequences

* Integrar dicha platarforma a nuestro sistema puede resultar más complejo en comparación con otras soluciones. 

## Pros and Cons of the Options

### 0007-1-Adyen

Adyen es una plataforma de procesamiento de pagos que se ha destacado por ofrecer soluciones de pago a nivel mundial.Su enfoque se centra en la simplicidad y escalabilidad, proporcionando una infraestructura robusta que puede manejar grandes volúmenes de transacciones. Adyen es conocida por su seguridad, utilizando prácticas avanzadas para proteger las transacciones y cumplir con los estándares de la industria. Aunque puede requerir una integración inicial más compleja, destaca por su capacidad para adaptarse a las preferencias locales y su presencia global.

* Good, because tiene capacidad para procesar pagos a nivel mundial.
* Good, because es altamente escalable, puede manejar volúmenes de transacciones masivos.
* Good, because ofrece seguridad, utiliza prácticas avanzadas de seguridad y cumple con los estándares de la industria para proteger las transacciones.
* Bad, because su integración puede resultar compleja.

### 0007-2-PayPal

PayPal es una de las pasarelas de pago más conocidas y utilizadas en el mundo. La plataforma permite a los usuarios realizar transacciones en línea de manera segura y fácil

* Good, because es compatible con una amplia variedad de plataformas de comercio electrónico y sistemas de pago en línea.
* Good, because payPal es ampliamente aceptado y utilizado en todo el mundo, lo que facilita la transacción entre clientes de diferentes países.
* Bad, because existen casos en los que las cuentas de PayPal pueden ser canceladas o restringidas, lo que puede causar inconvenientes a los usuarios.
