# Implementación Notificaciones

* Status: proposed
* Date: 2024-02-28

## Context and Problem Statement

Se requiere que el elemento reparto y rutas pueda notificar a los clientes el estado de su pedido vía mensajes al teléfono móvil y otros posibles canales de comunicación como Instagram. Hay que tener en cuenta futuras ampliaciones. El problema es coordinar el uso de las distintas APIs y componentes que se vayan a emplear.

## Decision Drivers

* RF-11: Seguimiento pedidos
* RF-12: Notificaciones de estado
* Escalabilidad

## Considered Options

* 0010-1 Patrón Bridge
* 0010-2 Decorator

## Decision Outcome

Chosen option: "0010-2 Decorator", because el patrón decoratos para implementar notificaciones es una práctica común.

### Positive Consequences

* Los desarrolladorse tendrán expeiencia en la implementaciín de esta solución de diseño.
* El sistema facilita añadir nuevas tecnologías.
* Modificar una tecnología no afecta a la implementación de las demás.

### Negative Consequences

* Se debe trabajar en que la implementación de los decoradores no se vuelva demasiado compleja. (No podrémos controlar si el uso de la API va a ser demasiado complejo).

## Pros and Cons of the Options

### 0010-1 Patrón Bridge

Por un lado tendremos una interfaz "Adapter". Habrá distintas implementaciones de adaptadores que adapten la información que debe ser notificada al formato correspondiente de cada api. Habrá otra interfaz, "Sender". Por cada componente se realizará una implementación que hara uso de una de las implementaciones adapter. La implementación recibe la información a transmitir, la adapta al formato usando el adaptador correspondiente y se comunica con la api para enviar el mensaje. 

Una clase general tendrá una lista  de "senders" y la recorrerá llamando a cada sender para enviar el mensaje.

* Good, because Permite desarrollar de manera independiente los adaptadores y la comunicación con la api. Es facil adaptarse a cambios de formato y a cambios en la comunicación.
* Good, because Añadir nuevos componenetes es tan sencillo como implementar un adaptador que genere la información en el formato adecuado e implementar la comunicación en el sender.
* Good, because Respeta el principio open-closed de solid
* Good, because Es fácil modificar y eliminar implementaciones y vías de mensaje.
* Bad, because Tantas interfaces dificulta la legibilidad. Entender el código sin documentación puede ser complicado.
* Bad, because No tenemos interes en que email sender (por ejemplo) pueda usar un adaptador distinto al dataToEmail.

### 0010-2 Decorator

Hay una Interfaz "Base decorator". Se implementa un decorator por cada tipo de mensaje que tengamos que enviar. Luego para enviar un mensaje a través de las APIs usamos las implementaciones del decorator para envolver el mensaje segun la API necesite.

* Good, because Es una estructura muy simple y más fácil de entender que la anterior.
* Good, because Añadir nuevos tipos de mensaje es fácill. Solo hay que añadir decoradores.
* Bad, because Es posible que aumente la complejidad de decorator en exceso y podría haber clases demasiado grandes (si el uso de la API es excesivamente complejo).
* Bad, because Cambiar de API (aunque sean muy parecidas) exige cambiar la clase.
