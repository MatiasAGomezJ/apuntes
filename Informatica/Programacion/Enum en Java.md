Leer Cap. 18 Libro Beginning Java 8 fundamentals

Enums
Para el compilador es una clase
Crea una clase con un constructor **privado**
En el constructor da valores a los atributos que luego podremos acceder
Va crear el numero de objetos como variables tenga

Podermos crear un objeto como valor null

```java
public enum Severity {
	LOW, MEDIUM, HIGH, URGENT;
}

Severity severity = null;

Severity badAttempt = new Severity(); // A compile time error

for(Severity s : Severity.values()){
	...
}
```


`.compareTo()` No puede comprobar diferentes tipos de enumerados. Pero si puedes hacer `.equals()`.

Si un método es `final` significa que no puede ser sobreescrito.

Singleton:
Sirven para crear objetos para una sola vez, 

