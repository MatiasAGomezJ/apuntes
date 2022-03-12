Un diagrama de clases repressenta las clases que seran utilizadas en el sistema y las relaciones que ecisten entre ellas.

Se utilizan durante las fases de análisis y diseño

Se identifican los componentes (con sus atributos y funcionalidades)

Concepto => Clase, atribut y método (operaciones.)

Una clase describe un conjunto de objetos que comparte los mismos atributos, que representa caractarísticas estables de las clases, y las operaciones que representan las acciones de las clases.

Los atributos (también llamados propiedades o características) son los datos detallados que contienen los objetos. Estos valores corresponden al objeto que instancia la clase y hace que todos lo objetos sean distintos entre sí.

Las operaciones (también llamadas métodos o funcionalidades) implementan las acciones que podrán llevarse a cabo sobre los atributos.

## Visibilidad
La visibilidad de un atributo o de una operación definirá el ámbito desde el que podrán ser utilizados estos elementos. Esta característica está directamente relacionada con el concepto de orientación a objetos llamado emcapsulación, mediante el cual se permite a los objetos decidir cuál de la su información será más o menos pública para el resto de objetos.

Símbolo | Tipo
:--: | :--:
`+` | public
`-` | private
`#` | protected
`~` | package (no se escribe nada)

Modificador | Clase | Package | Subclase | Todos
:--: | :--: | :--: | :--: | :--:
public | Sí | Sí | Sí | Sí
protected | Sí | Sí | Sí | No
No especificado | Sí | Sí | No | No
private | Sí | No | No | No

## Objetos. Instanciación
Un objeto es uan instanciación de una clase. El concepto insanciación indica la accinón de crear una instancia de uan clase.

La creación de una instancia de una clase se refiere a llamar almétodo constructor de una clase en tiempo de ejecución de un software