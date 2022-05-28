Son transacciones
```JAVA
@GET @POST @PUT @DELETE
```
Finalizan cuando acaban el método en el que están

```JAVA
@PersistentContext
EntityManager em;
```

Un **PersistentContext** es un espai de objectes, com una cache, que guarda todos los objectos que el **EntityManager** ha trabajado.

Un **PersistentContext** se crea cuando comienza una transacción y se destruye cuando acaba.

Un **PE** comienza vacio. Una funcion como **find** guarda el objecto qu encuentra en el **PE**.

Un objecto que se instancia a partir de la base de datos y pasa a formar parte del **PE**. Este objecto que tiene entidad y forma parte del **PE** se le llama **managed** (gestionado).

Cuando la transacción finaliza tambien lo hace el **PE**, por lo tanto, sin el **PE** el objecto ya no es **managed** sino **detached**.

Un objeto **detached** es un objeto, entidad, con identidad pero que no forma parte de ningun **PE**. Ya sea porque el pe se ha eliminado, o porque, no ha formado parte nunca, como es caso de un objecto mediante el constructor java.

 Un objecto es **new** si lo hemos creado para guardar pero todavia no esta en el **PE**. 
 
Un objeto **removed** es un objeto que esta marcado para borrar de la base de datos. El objecto sigue en memoria ya que java no puede borrar objetos en memoria, pero no se puede utilizar para hacer operaciones de persistencia.