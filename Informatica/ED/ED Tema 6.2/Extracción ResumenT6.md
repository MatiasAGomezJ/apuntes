# 6 Diseño y realización de pruebas de software
## 6.1 Introducción
<ins>**30% y un 50% del coste de todo el proyecto en la fase de pruebas**</ins>.

El **objetivo** de las pruebas es la <ins>evaluación de la calidad del software desarrollado durante todo su ciclo de vida, validando que hace lo que debe hacer y que lo hace tal y como se diseñó, a partir de los requerimientos</ins>.

## 6.3 Procedimientos, tipos y casos de pruebas

![](https://i.imgur.com/rq92UBa.png)

El esquema se inicia con una planificación de las pruebas, que tiene como punto de partida el análisis funcional, diagramas de casos de uso... del producto a desarrollar. En la planificación se estimarán los recursos necesarios para la elaboración de las pruebas y la posterior validación del software, obteniéndose un plan de pruebas como salida.

Partiendo del plan de pruebas y del código fuente que se haya desarrollado, se llevará a cabo el diseño de las pruebas identificando qué tipo de pruebas se efectuará para cada una de las funcionalidades, obteniéndose, como salida, los casos de prueba y procedimientos.

A partir de ese momento, se crea un bucle donde se ejecutarán las pruebas, se evaluarán los resultados de las pruebas efectuadas detectando los errores, se depurará el código aplicando las correcciones pertinentes y se volverán a ejecutar las pruebas.

Al finalizar el bucle, se realizará el análisis de la estadística de errores. Este análisis permitirá hacer predicciones de la fiabilidad del software, así como detectar las causas más habituales de error, con lo que se podrán mejorar los procesos de desarrollo.

### 6.3.1 Planificación de las pruebas
El **coste** de la resolución de un problema **crece exponencialmente** a medida que avanzan las fases del proyecto en las que se detecte.

Algunos de los contenidos del plan de pruebas son:
- Identificador del plan de pruebas
- Descripción del plan de pruebas
- Elementos del software a probar
- Elementos del software que no deben probarse
- Estrategia del plan de pruebas
- Documentos a entregar.
- Responsables y Responsabilidades.
- Calendario del plan de pruebas.

### 6.3.2 Diseño de las pruebas. Tipo de pruebas
Tipos de pruebas:
- Estructurales o de caja blanca
- Funcionales o de caja negra
- De integración
- De carga y aceptación
- De sistema y de seguridad
- De regresión y de humo

#### Casos de prueba y procedimientos
Un **caso de prueba** define cómo se llevarán a cabo las pruebas, especificando, entre otros: el tipo de pruebas, las entradas de las pruebas, los resultados esperados o las condiciones bajo las que tendrán que desarrollarse

Los casos de pruebas tienen un objetivo muy marcado: **identificar los errores existentes al software para que éstos no lleguen al usuario final**.

A la hora de diseñar los casos de prueba, no sólo debe validarse que la aplicación hace lo que se espera ante entradas correctas, sino que también debe validarse que tenga un comportamiento estable ante entradas no esperadas, informando de el error

Dos enfoques:
- **Pruebas de caja negra**: Su objetivo es validar <ins>que el código cumple la funcionalidad definida</ins>.
- **Pruebas de caja blanca**: <ins>Se centran en la implementación de los programas para escoger los casos de prueba</ins>.

Los casos de prueba siguen un ciclo de vida clásico:
- Definición de los casos de prueba.
- Creación de los casos de prueba.
- Selección de los valores para los test.
- Ejecución de los casos de prueba.
- Comparación de resultados obtenidos con los resultados esperados.

#### Tipo de pruebas
##### Tipo de pruebas unitarias:
Tienen como objetivo la detección de errores en los datos, en los algoritmos y en la lógica de éstos.
El método utilizado en este tipo de pruebas es el de la caja blanca o el de caja negra.
##### Tipo de pruebas funcionales:
Son las encargadas de detectar los errores en la implementación de los requerimientos de usuario.
##### Tipo de pruebas de integración:
 Se encargan de detectar errores de las interfaces y en las relaciones entre los componentes.
##### Tipo de pruebas de carga:
Se comprueba el rendimiento y la integridad de la aplicación ya terminada con datos reales y en un entorno que también simula el entorno real.
##### Tipo de pruebas de aceptación:
Su objetivo es la validación o aceptación de la aplicación por parte de los usuarios.
<ins>**Pruebas alfa y las pruebas beta**</ins>
##### Tipo de pruebas de sistema:
Comprobar que la integración es correcta.
##### Tipo de pruebas de regresión:
Su finalidad es detectar posibles errores introducidos al haber realizado cambios en el sistema, bien para mejorarlo, bien para corregir otros errores.
##### Tipo de pruebas “de humo”. 
Son pruebas rápidas de las funciones básicas de un software que normalmente se realizan después de un cambio en el código antes de registrar este código modificado en la documentación del proyecto.

#### Pruebas unitarias
Las pruebas unitarias, también conocidas como pruebas de componentes, son las pruebas que se harán a más bajo nivel, sobre los módulos o componentes más pequeños del código fuente del proyecto informático. Existen dos enfoques:
- **Caja blanca**: se analizan todos los posibles caminos
- **Caja negra**: funcionamiento de las funcionalidades del software.

##### Enfoque estructural o de caja blanca
**Las pruebas de caja blanca** se centran en la implementación de los programas para escoger los casos de prueba <ins>analizando todos los caminos de ejecución</ins>.

Al menos se pasa una vez por cada camino del programa

##### Enfoque funcional o pruebas de caja negra
**Las pruebas de caja negra** prueban la funcionalidad del programa, para el que se diseñan casos de prueba que comprueben las especificaciones del programa.

Habrá que escoger cuidadosamente los casos de prueba, de modo que sean tan pocos como sea posible para que la prueba se pueda ejecutar en un tiempo razonable y, al tiempo, que cubran la variedad de entradas y salidas más amplia posible.
- **Clases de equivalencia**: se trata de determinar los distintos tipos de entrada y salida, agruparlos y escoger casos de prueba para cada tipo o conjunto de datos de entrada y salida.
- **Análisis de los valores límite**: estudian los valores iniciales y finales, puesto que estadísticamente se ha demostrado que tienen mayor tendencia a detectar errores

#### Pruebas de integración
Las pruebas de integración sirven para validar que las partes de código que ya han sido probadas de forma independiente sigan funcionando correctamente al ser integradas.

#### Pruebas de carga y aceptación
Las pruebas de **carga** son pruebas que tienen como objetivo comprobar el rendimiento y la integridad de la aplicación ya terminada con datos reales.

El objetivo de la prueba de *aceptación* es obtener la aprobación del cliente sobre la calidad de funcionamiento del sistema desarrollado y probado

##### Las pruebas alfa
Consisten en invitar al cliente que venga al entorno de desarrollo a probar el sistema. Se trabaja en un entorno controlado y el cliente siempre tiene un experto a mano para ayudarle a usar el sistema y para analizar los resultados.

##### Las pruebas beta
Vienen después de las pruebas alfa, y se desarrollan en el entorno del cliente, un entorno que está fuera de control para el desarrollador y el equipo de trabajo. Aquí el cliente se queda solo con el producto y trata de encontrar los errores, de los que informará el desarrollador.

#### Pruebas de sistema y seguridad
Las pruebas de **sistema** servirán para validar la aplicación una vez ésta haya estado integrada con el resto del sistema del usuario.
- **Pruebas de robustez**: valorarán la capacidad de la aplicación para soportar varias entradas no correctas.
- **Pruebas de seguridad**: ayudarán a determinar los niveles de permisos de los usuarios, las operaciones que podrán llevar a cabo y las de acceso al sistema y los datos.
- **Pruebas de usabilidad**: determinarán la calidad de la experiencia de un usuario en la forma de interactuar con el sistema.

#### Pruebas de regresión y pruebas de humo
**Las pruebas de regresión** buscan detectar posibles nuevos errores o problemas que puedan salir al haber introducido cambios o mejoras en el software.

#### Las pruebas “de humo”
Se utilizan para describir la validación de los cambios de código en el software, antes de que los cambios en el código se registren en la documentación del proyecto. Son pruebas de ejecución rápida y comprueban las funciones básicas del software.

### 6.3.4 Finalización: evaluación y análisis de errores
Efectuar una evaluación y un análisis de los errores localizados, tratados, corregidos y reevaluados.
En caso de tener que rehacer los **procedimientos de pruebas**, es muy importante la creación de nuevos casos de pruebas y no la readaptación de los ya existentes.