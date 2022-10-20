Se dice de un objecto **Managed** que se instancia a partir de la base de datos y pasa a formar parte de un [[Persistence Context]] **activo**. Este objecto tiene entidad, es decir, existe en la base de datos.


El hecho que esté en un **PE** activo afecta al comportamiento del entity manager

Hay dos reglas:
1. No puede haber dos objetos con la misma identidad en un mismo **PE**.
2. El **PE** gestiona la persistencia de los objetos que contiene.

## Primera regla.
No puede haber dos objetos con la misma identidad en un mismo **PE**.

Persistence identity: **TIPUS** + **propiedad id**

EJ: $Persona + DNI$

Si un pe ya tiene cargada esta entidad, y se intenta ejecutar la misma entidad, el código hace un select y devuelve el registro, pero, cuando el JPA intenta instanciar y guardarlo al PE encuatra una violacion de la regla. NO da un error, si no que la información que viene del select se descartan y el objeto tendra una referancia hacia la entidad que ya esta incluida en este entity manager 

Con esto -> ejercicio

### Ejercicio
Veis ara el motiu de la signatura del métode merge?
![](https://i.imgur.com/ILqoCez.png)
*Returns*: the managed instance that the state was merged to

#### Método merge
Sirve para pillar un objeto e indicar al **em** que los cambios que le hemos hecho al objeto, su estado, se propagen a la base de datos.

Le pasamos un por parametro con el objeto el cual queremos guardar los cambios y devolvia una referencia a un objeto del mismo tipo

Si tenemos que seguir trabajando con el objeto utilizar la referencia que nos devuelve el método y no el objeto que le pasamos por parametro

## Segunda regla.
El **PE** gestiona la persistencia de los objetos que contiene.

Se ha hecho un find de on objeto, entonces esta **managed**. Si ahora modificamos su estado, automaticamente, sin hacer un merge ni nada. se actualizará en la base de datos.

Las sentencia SQL no se traducen a los métodos del entity manager.  
![](https://i.imgur.com/ydHmOo3.png)
