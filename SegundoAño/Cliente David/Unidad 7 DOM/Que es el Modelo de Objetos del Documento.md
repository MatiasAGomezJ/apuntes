# Introducción
El **Modelo de Objetos del Documento** (DOM) es una **interfaz de programación de aplicaciones** (API) para documentos validos HTML y bien construidos XML. Define la estructura lógica de los documentos y el modo en que se accede y manipula. XML presenta estos datos como documentos, y se puede utilizar DOM para manejar estos datos.

Con el Modelo de Objetos del Documento, los programadores pueden construir documentos, navegar por su estructura, y añadir, modificar, o eliminiar elementos y contenido.

Especificación de W3C, un objetivo importante para el Modelo de Objetos del
Documento es proporcionar un interfaz estándar de programación que puede ser
utilizado en una amplia variedad de entornos y aplicaciones. El DOM se diseña para ser
utilizado en cualquier lenguaje de programación.

# Lo que el Modelo de Objetos es
DOM es un API

![[DOM_Table.png]]
>Representación gráfica DOM de la tabla

DOM no especifica que los documentos deban ser implementados como un árbol o un bosque, ni tampoco especifica como deben implementarse las relaciones entre los objetos. DOM es un modelo lógico que puede implementarse de cualquier manera que sea conveniente. En esta especificación, usamos el término modelo de estructura para describir la representación en forma de árbol de un documento.

isomorfismo estructural

Los documentos se modelizan utilizando objetos, y el modelo comprende no solamente la estructura de un documento, sino también el comportamiento de un documento y los objetos de los cuales se compone. En otras palabras, **los nodos del diagrama anterior no representan una estructura de datos, representan objetos, los cuales pueden tener funciones e indentidad**. Como modelo de objeto, DOM identifica:
- Las aplicaciones y objetos utilizados para representar y manipular el documento.
- La semantica de estas aplicaciones y objetos - incluyendo comportamientos y atributos.
- Las relaciones y colaboraciones entre estas aplicaciones y objetos.

Tradicionalmente, la estructura de documentos SGML se ha representado mediante un modelo de datos abstractos, no por un modelo de objeto. En un modelo de datos abstracto, el modelo se centra en los datos. **En los lenguajes de programación orientados a objetos, los datos se encapsulan en objetos que ocultan los datos, protegiéndolos de su manipulación directa desde el exterior**. Las funciones asociadas con estos objetos determinan como pueden manipularse los objetos, y son parte del modelo de objeto.

# Lo que el Modelo de Objetos del Documento no es
- No es una manera de ofrecer objetos persistentes para XML o HTML
- No es un conjunto de estructuras de datos, es un modelo de objeto que especifica aplicaciones.
- No define que información en un documento es relevante o que información en un documento es estructurado.

# De donde viene el Modelo de Objetos del Documento
El DOM se originó como una especificación para permitir que los scrips de JavaScript y los programas Java fueran portables entre los navegadores Web. El "HTML Dinámico" fue el antesesor inmediato del Modelo de Objetos del Documento, y originalmente se pensaba en él principalmente en términos de navegadores.

# Arquitectura del DOM
La especificación del DOM proporciona un conjunto de APIs que forman la API del DOM. Cada especificación del DOM define uno o mas módulos y cada módulo esta asociado con un nombre de funcionalidad.

La siguiente representación contiene todos los módulos de DOM, representado
utilizando sus nombres de funcionalidades, definidos a lo largo de las especificaciones
DOM:
![[DOM_Modules.png]]

Una aplicación de usuario para Web es muy probable que implemente el módulo "MouseEvents" (eventos del ratón), mientras que una aplicación del lado del servidor no tendría que utilizar este módulo y probablemente no lo implementaría

