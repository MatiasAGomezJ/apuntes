# Diagramas
1. Diagramas de comportamiento
2. Diagramas en casos de uso
3. Diagramas de secuencia
## Diagramas de comportamiento
![](https://i.imgur.com/ltkc5mq.png)

**Los diagramas dinámicos o de comportamiento representan el comportamiento dinámico del sistema que se está moldeando. Es decir, indican las acciones y procesos que se llevarán a cabo entre los elementos del sistema**, fijándose en sus movimientos y en los efectos que tienen estas acciones y actividades sobre los elementos.

Los distintos diagramas de comportamiento describen el comportamiento de clasificadores o, más a menudo, de sus instancias, desde distintos puntos de vista:

- Por un lado, representan o bien componentes ejecutantes o bien comportamientos emergentes.
- Por otra, se destaca uno de estos aspectos u otro: interacciones con el exterior, o las situaciones – denominadas estados– por las que pasa una instancia durante su existencia, o la secuencia temporal de las distintas partes de un comportamiento...

![](https://i.imgur.com/O7QyY9Z.png)
### Diagrama de actividades
**Diagrama de actividades** es lo que descompone un comportamiento en actividades y representa los flujos de ejecución y de información entre estas actividades.
### Diagrama de casas de uso
**Diagrama de casos de uso**. Este diagrama identifica los distintos comportamientos de un sistema desde el punto de vista de sus interacciones con el mundo exterior y describe determinadas relaciones entre estos comportamientos.
### Diagrama de estados
**Diagrama de estados** (en inglés State Machine Diagram). Este diagrama muestra los posibles cambios de una situación a otra de las instancias del clasificador de contexto e indica las causas y comportamientos que ponen en marcha estos cambios.
### Diagramas de interacción
Los otros cuatro diagramas están agrupados en los **diagramas de interacción**. Esta agrupación contiene diagramas que representan un comportamiento emergente mediante mensajes entre las instancias de clasificadores de una estructura interna o colaboración y puede especificar restricciones temporales relativas a estos mensajes.
#### Diagrama de comunicaciones
**Diagrama de comunicaciones**, que representa los mensajes sobre los conectores de una estructura interna o colaboración.
#### Diagrama de secuencia
**Diagrama de secuencia**, que pone énfasis en el orden temporal de los mensajes.
#### Diagrama de tiempo
**Diagrama de tiempo**, que representa una posible secuencia temporal de cambios de estado de una instancia o de diversas instancias que interactúan de acuerdo con los diagramas de estados respectivos.
#### Diagrama global de interacción
**Diagrama global de interacción**, que es un diagrama resumido que combina notaciones de los diagramas de secuencias y de los de actividades.
## Diagramas de casos de uso
El punto de vista que se utiliza para elaborar los diagramas de casos de uso es el punto de vista del usuario final. Esto implica que se trata de un **diagrama muy conveniente y utilizado en los intercambios iniciales de opiniones con los usuarios finales del sistema a modelizar** y, posteriormente, a automatizar.

Los mismos usuarios lo pueden entender y participar en su corrección. Con este tipo de diagrama se podrá crear una documentación adecuada para las necesidades de la toma de requerimientos.

**Los diagramas de casos de uso representan los diferentes requerimientos que utilizan usuarios finales de un determinado sistema. A partir de la utilización de actores y de casos de uso, este tipo de diagramas moldean las diferentes funcionalidades que podrá ofrecer un sistema.**

**Un caso de uso es una funcionalidad o un servicio que ofrece el sistema a modelizar a sus usuarios finales**. Es un conjunto de interacciones secuenciadas que se desarrollan entre los actores y el sistema para dar respuesta a un evento que inicia un actor.

En la modelización de un sistema podrá haber muchos casos de uso. Esto se debe al hecho que cada caso de uso deberá dar respuesta sólo a una característica concreta del sistema. Así, con esta representación del sistema, el usuario final podrá validar fácilmente que el analista ha entendido correctamente el funcionamiento del sistema que de representar.

Los elementos fundamentales del diagrama de casos de uso son los siguientes:
- Actor
- Sujeto
- Caso de uso o comportamiento

![](https://i.imgur.com/n1tR1RA.png)
### Sujeto
El **sujeto** de un diagrama de casos de uso es el clasificador al que está asociado el diagrama, que representa sus comportamientos ejecutantes.
Puede ser cualquier cosa que tenga comportamientos: un software, un sistema informático o físico en general, un subsistema, un componente, una clase...
### Actor
Un **actor** es un conjunto de papeles que hace una entidad física o virtual externa al sujeto en relación con sus casos de uso; a partir de estos papeles el actor interactúa con el sujeto y cada papel tiene que ver con uno de los casos de uso del sujeto. Todo lo que inicia un caso de uso o responde a un caso de uso también se considera un actor

Un actor puede ser:
- Una persona
- Un sistema
- Un dispositivo físico que tenga un cierto comportamiento propio y autónomo en relación con el sujeto e interactúe directamente.
- Tiempo, Reloj... cuando un caso de uso se pone en marcha automáticamente en una hora determinada.

### Caso de uso
Un **caso de uso** es un comportamiento ejecutante del sujeto. Un caso de uso se representa mediante un verbo que indica una acción, operación o tarea concreta. Esta operación se activará a partir de una orden dada por un agente externo al caso de uso. Podrá ser un actor que haga una petición y genere el caso de uso, u otro caso de uso que le invoque.

Un caso de uso se podrá representar de dos formas distintas:
- Mediante un diagrama de casos de UML, siguiendo la notación del resto de diagramas UML.

![](https://i.imgur.com/FopqRg3.png)

- Mediante un documento detallado.

![](https://i.imgur.com/Yg0y9l7.png)
### Ventajas e inconvenientes
- Son muy adecuados para comunicarse con los usuarios finales y, en definitiva, con los clientes.
- Ayudan a documentar las funcionalidades de lo que se conoce como cajas negras, que es como se consideran algunos de los casos de uso de un sistema.
- Ayudan a dividir y gestionar los proyectos de un tamaño muy extenso.
- Complementan la documentación del proyecto informático, ofreciendo una explicación sencilla del funcionamiento a los usuarios.
- Permiten realizar un seguimiento objetivo del proyecto.
- Ayudan en la tarea de verificación y validación que realizan los verificadores del software desarrollado en el proyecto.
## Diagramas de secuencia
El **diagrama de secuencia** describe las interacciones entre un grupo de objetos mostrando de forma secuencial los envíos de mensajes entre objetos. Los objetos interactúan entre sí con el envío de mensajes. La recepción de un mensaje suele significar la ejecución de un método que se especifica en el mensaje, y el objeto se vuelve activo mientras dura la ejecución del método.

![](https://i.imgur.com/tD65QYj.png)

Los elementos son los siguientes: 
### Línea de vida
Una **línea de vida** representa un elemento conectable que participa en una interacción enviando y recibiendo mensajes. Una línea de vida representa el intervalo de tiempo en el que existe la instancia o instancias que forman parte del elemento conectable, desde su creación hasta su destrucción.
### Activacion
Aunque por lo general sólo durante una parte o varias partes de ese intervalo participan en la interacción que contiene la línea de vida; estas partes se llaman **activaciones** y representan los intervalos de tiempo durante los cuales se está ejecutando alguna operación que tiene por objeto de contexto alguna de sus instancias.

![](https://i.imgur.com/Oe0Uoz2.png)
### Mensaje
Un **mensaje** es la especificación de la comunicación entre objetos. Un mensaje se representa con una flecha del emisor hacia el receptor; diferentes tipos de mensaje se representan con diferentes tipos de flecha:
#### M. asíncrono
Un mensaje **asíncrono**: el objeto no espera la respuesta a este mensaje antes de continuar.

![](https://i.imgur.com/E2xsQFB.png)
#### M. síncrono
Un mensaje **síncrono**: cuando el objeto espera la respuesta a este mensaje antes de continuar con su trabajo.

![](https://i.imgur.com/emRCd0s.png)
#### M. de respuesta de un mensaje síncrono
Un **mensaje de respuesta de un mensaje síncrono** se indica con una flecha de línea discontinua y punta llena.
![](https://i.imgur.com/emRCd0s.png)
![](https://i.imgur.com/PrKvodb.png)
#### M. que provoca la creación de un objeto
Un **mensaje que provoca la creación de un objeto** se indica con una flecha de línea discontinua y punta abierta; además, el extremo del mensaje coincide con el inicio de la línea de vida del receptor.
![](https://i.imgur.com/WB5bbXO.png)

![](https://i.imgur.com/h2W0HCQ.png)
### ..
Los mensajes se pueden numerar en formato de lista multinivel. Si un mensaje se envía una vez finalizado su precedente se contabiliza secuencialmente: 1,2,3... Pero si el mensaje se envía antes de que haya finalizado el precedente, se incrementará el nivel: 3.1, 3.2,...

![](https://i.imgur.com/RLa7wv3.png)

#ED 