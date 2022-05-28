El self se utiliza para poner una variable en el entorno

Si ponemos un metodo como estatico se da a entender que no utilizará variables de la clase(self)

Static y self nunca juntos

no se puede modificar la visibilidad de un metodo

Datos con relacion metidos en una structura

Si no se le puede cambiar el nombre de la funcion

#### DAT DAtos abstractos
Tienen sus propios metodos y atributos
#### Programacion funcional se utilizan los metodos built-in del lenguaje de programacion [Pag 574]

#### En la mayoria de lenguajes de programacion existen: map, filter, reduce

Filter devuelve un objeto filter.

Reduce se utiliza para reducir una lista a un unico valor

Map: Le pasas una coleccion de valors y por cada ejecuta una funcion
Aplica una funcion a cada elemento de una lista

#### Lambda
le decimos al compilador que lo que se escribe posterior a `lambda` es una funcion sin nombre
```python
	def isPositive(x):
		return x > 0	
	# -- O --
	lambda x : x > 0

	def isBigger(x, y):
		return x > y	
	# -- O --
	lambda x, y : x > y

```
#### Operador ternario
```python
	if (cond):
		return 1
	else:
		return 2
	# -- 0 --
	return cond ? 1 : 2
```

>***Consejazo***
>TDD a muerte


Las clases tienen funciones built-in y se suelen sobreescribir

Para el bowling usar coverage

# DDD
Los diagramas y modelos sirven para explicar de manera sencilla , logico de modelo destilada, solo lo que aporta valor al comprador del software.

L: Principio de sustitucion de Liskov
Programo entidades que exiben un 

Si hay varios objetos que tienen la misma ogica lo meteremos en el mismo objeto

Entidades:

CilderRose |
:--: |
stock |
update_quality <br> add_item |

### Ni idea donde va esto brother
El codigo de las distinas capas no tiene que estar conectado

