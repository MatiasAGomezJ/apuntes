# Tema 5: Herramientas para el control y documentación de software
# 5.1 Refactoring
El término **refactoring** hace referencia a los cambios efectuados en el código de programación desarrollado, sin implicar ningún cambio en los resultados de su ejecucción. Es decir, se transforma el código fuente manteniendo intacto su comportamiento, aplicando los cambios sólo en la forma de programar o en la estructura del código fuente, buscado su optimización.

¿Por qué los programadores dedican tiempo a la refactorización del código fuente? Aumento de la calidad del código fuente.

### 5.1.1 Ventajas y limitaciones de la refactorización

Ventajas:
- Prevención de la aparición de problemas habituales a partir de los cambios provocados por los mantenimientos de las aplicaciones.
- Ayuda a aumentar la simplicidad del diseño.
- Mayor entendimiento de las estructuras de programación.
- Detección más sencilla de errores.
- Permite agilizar la programación.
- Genera satisfacctión en los desarrolladores.

Limitaciones de la refactorización
- Personal poco preparado para utilizar las técnicas de refactorización.
- Exceso de obsesión por conseguir el mejor código fuente.
- Excesiva dedicación de tiempo a la refactorización, provocando efectos negativos.
- Repercusiones en el resto del software y del equipo de desarrolladores cuando uno aplica técnicas de refactorizacción.
- Posibles problemas de comunicación provocados por el punto anterior.
- Limitaciones debidas a las bases de datos, interfaces gráficas...
### 5.1.2 Patrones de ractorización más usuales
Los patrones más habituales son los siguientes:
- Renombrar
- Mover
- Extraer una variable local
- Extraer una constante
-  Convertir una variable local en un campo
-  Extraer una interfaz
-  Extraer el método

## 5.2 Control de versiones
Un **sistema de control de versiones** es una herramienta de ayuda al desarrollo de software que irá almacenando, según los parámetros indicados, la situación del código fuente en momentos determinados. Es como una herramienta que va haciendo fotos de forma regular, cada cierto tiempo, sobre el estado del código.

Algunas funcionalidades de los sistemas de control de versiones pueden ser:
- **Comparar cambios en los distintos archivos a lo largo del tiempo**, pudiendo ver quien ha modificado por última vez un determinado archivo o pedazo de código fuente.
- Reducción **de problemas de coordinación que puede haber entre los distintos programadores**. Con los sistemas de control de versiones podrán compartir su trabajo, ofreciendo las últimas versiones del código o de los documentos, y trabajar, incluso, de forma simultánea sin miedo a encontrarse con conflictos en el resultado de esta colaboracón.
- **Posibilidad de acceder a versiones anteriores de los documentos o código fuente**. De forma programada se podrá automatizar la generación de copias de seguridad o, incluso, almacenar todo cambio efectuado. En el caso de haberse equivocado de forma puntual, o durante un período largo de tiempo, el programador podrá tener acceso a versiones anteriores del código o deshacer, paso a paso, todo lo desarrollado durante los últimos días.
- **Ver qué programador ha sido el último en modificar un determinado pedazo de código** que puede estar causando un problema.
- **Acceso al historial de cambios sobre todos los archivos a medida que avanza el proyecto**. También puede servir para el jefe de proyectos o para cualquier otra parte interesada (stakeholder), con permisos para acceder a este historial, para ver la evolución del proyecto.
- **Devolver un archivo determinado o todo el proyecto entero a uno o varios estados anteriores**.

Los sistemas de control de versiones ofrecen, además, algunas funcionalidades para poder gestionar un proyecto informático y para poder realizar su seguimiento. Entre estas funcionalidades se pueden encontrar:
- **Control histórico detallado de cada archivo**. Permite almacenar toda la información de lo que ha sucedido en un archivo, tales como todos los cambios que se han efectuado, por quien, el motivo de los cambios, almacenar todas las veriones que ha habido desde su creación...
- **Control de usuarios con permisos para acceder a los archivos**. Cada usuario tendrá un tipo de acceso determinado a los archivos para poder consultarlos o modificarlos o, incluso borrarlos o crear otros nuevos. Este control debe ser gestionado por la herramienta de control de veriones, almacenando todos los usuarios posibles y los permisos que tienen asignados.
- **Creación de ramas de un mismo proyecto**: en el desarrollo de un proyecto hay momentos en los que es necesario ramificarlo, es decir, a partir de un determinado momento, de un determinado punto, es necesario crear dos ramas del proyecto que se podrán seguir desarrollando por separado. Este caso se puede dar en el momento de finalizar una primera versión de una aplicación que se entrega a los clientes, pero que es necesario seguir evolucionando.
- **Fusionar dos versiones de un mismo archivo**: permitiendo fusionarlas, cogiendo, de cada parte del archivo, el código que más interese a los desarrolladores. Esta funcionalidad deberá validarse manualmente por parte de una persona.

## 5.2.1 Componentes de un sistema de control de veriones
- Repositorio (**repository**): conjunto de datos almacenados también referido a versiones o copias de seguridad. Es el sitio donde estos datos quedan almacenados. Se podrá referir a muchas versiones de un único proyecto o de varios proyectos.
- Tronco (**master**): estado principal del proyecto. Es el estado del proyeto destinado, al terminar su desarrollo, a ser pasado a producción.
- Rama (**branch**): es una bifurcación del tronco o rama maestra de la aplicación que contiene una versión independiente de la aplicación a la que pueden aplicarse cambios sin que afecten ni al tronco ni a otras ramas. Estos cambios, en un futuro, pueden incorporarse al tronco.
- Versión (**version**): es el estado del proyecto o una de sus ramas en un momento determinado. Se crea una versión cada vez que se añaden cambios a un repositorio.
- Etiqueta (**tag**): Información que se añadirá a una versión.
- Clonar (**clone**): consiste en crear un nuevo repositorio, que es una copia idéntica de otro, puesto que contiene las mismas revisiones.
- Bifurcación (**fork**): creación de un nuevo repositorio a partir de otro. Éste nuevo repositorio, al contrario que en el caso de la clonación, no está ligado al repositorio original y se trata como un repositorio distinto.
- **Pull**: es la acción que copia los cambios de un repositorio (habitualmente remoto) en el repositorio local. Esta acción puede provocar conflicos.
- **Push**: son acciones utilizadas para añadir los cambios del repositorio local en otro repositorio (habitualmente remoto). Esta acción puede provocar conflictos.
- Fusionar (**merge**): es la acción que se produce cuando se quieren combinar los cambios de un repositorio local con uno remoto y detectar cambios en el mismo archivo en ambos repositorios y se produce un conflicto.