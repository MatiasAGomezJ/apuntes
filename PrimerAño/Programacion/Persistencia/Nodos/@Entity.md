JPA solo gestiona la persistencia de entidades

Si intentamos hacer un persiste de un string no sabra que hacer con ello

Las entidades son las clases con `@Entity`

Tienen que tener un constructor sin parámetros

No pueden ser `final`

Toda entidad necesita una propiedad "identidad", un `id`

Si no se indica lo contrario todas las propiedades son persistentes. Para indicar que lo no sea usamos `@Transient`

`field acces`
- Anotamos las variables
- JPA lo utiliza para leer/escribir

`property acces`
- Anotamos las métodos getter
- JPA utiliza get/set para acceder a los atributos