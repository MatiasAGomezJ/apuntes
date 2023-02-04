###### Columna H

# El Stack

El **stack** es una región de la memoria que guarda variables temporales de cada función.
- Es [[LIFO]].

Cada vez que una función declara una nueva variable es *pusheada* al stack. Cuando se sale de la función, **todas** las variables son liberadas de la memoria.

La ventaja, no tienes que alojar la memoria manualmente, tanto para alojarla como para liberarla. Ya que lo hace la CPU, es muy rápido.

Puesto que las variables se borran después de finalizar una función, esta las hace locales por naturaleza.

## Resumen

- El stack crece y decrece a medida que las funcionas hacen *push* y *pop* a las variables locales. 
- La memoria se maneja automáticamente.
- Tiene tamaño.
- stack variables only exist while the function that created them, is running.

# El Heap
El **heap** es una región de la memoria que **NO** se majena automáticamente.

En C, utilizas las funciones `malloc` y `calloc` para alojar memoria en el heap. Para liberar la memoria utilizas `free`. Si no lo haces sucederá una fuga de memoria. El heap ocupará memoria y no dejará espacio para otros procesos.

No tiene restricción de tamaño.

La velocidad de lectura dentro del heap es más lenta porque es necesario utilizar *pointers* para acceder a ella.

Las variables dentro del heap son accesibles en cualquier parte del programa, esencialmente son globales.

# VS
## Stack
- Acceso rápido
- No hay que desalojarlas explícitamente.
- Es manejado eficientemente por la CPU, la memoria no se fragmentará.
- Locales.
- Tamaño limitado.
- Las variables no pueden cambiar de tamaño
## Heap
- Globales
- No hay límite de tamaño.
- Acceso más lento.
- Un eficiente uso del espacio no es garantizado, la memoria puede bloquear a otra memoria si no es liberada.
- Tienes que manejarla.
- Pueden variar de tamaño.

# Punteros (\*)
Los punteros indican el espacio de memoria de la variable donde están.
```c
double *age = malloc(sizeof(int));
*age = 30;
```

# When to use the Heap?
When should you use the heap, and when should you use the stack? If you need to allocate a large block of memory (e.g. a large array, or a big struct), and you need to keep that variable around a long time (like a global), then you should allocate it on the heap. If you are dealing with realtively small variables that only need to persist as long as the function using them is alive, then you should use the stack, it's easier and faster. If you need variables like arrays and structs that can change size dynamically (e.g. arrays that can grow or shrink as needed) then you will likely need to allocate them on the heap, and use dynamic memory allocation functions like malloc(), calloc(), realloc() and free() to manage that memory "by hand". We will talk about dynamically allocated data structures after we talk about pointers.