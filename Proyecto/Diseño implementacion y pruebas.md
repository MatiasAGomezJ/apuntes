# Diseño
- Mapa conceptual proyecto
- ***Esquema de BBDD***
# Implementación
- Herramientas utilizados
- BackEnd
	- BBDD: CRUD -> ejemplos
- Front end	
...
# Pruebas
En diseño hablamos de las pruebas se realizaran
- BackEnd
	- Codigo
	- Capturas pantallas
- FromEnd	
# Diseño
La estructura del programa empieza en un modulo principal nombrado "main" el cual contiende diversos submodulos en una agrupacion especifica a la tarea que realiza. 
## Estructura
![](https://i.imgur.com/DJrBliV.png)

El modulo principal se encarga de llamar a las otras funciones, en este modulo hay dos grupos de modulos que utiliza.

Los primeros se encargan de acceder a la base de datos de Mongo y devolver lo que le pedimos:
1. La funcion `obtener_cluster(uri)` se encarga de devolver el cluster en base a la URI que le pasamos
2. El modulo de `obtener_bd(cluster, bd)` devuelve a partir de un cluster la base de datos con el nombre que tambien le pasamos.
3. Por ultimo, la funcion `obtener_coleccion(bd, coleccion)` devuelve, de la base de datos pasada, la coleccion que ha sido pasada como parametro.

Lo otros modulos se encargan de la lógica del programa, estos estan siendo llamados desde la funcion `crear_markdown(coleccion, filtro)` :
1. La primera funcion es `obtener_documentos(coleccion, filtro)` la cual a partir de una coleccion y un diccionario, devuelve todos los documentos que haya dentro de la coleccion en los cuales esté filtro.
2. La siguiente es `obtener_texto_para_markdown(lista_documentos)` que crea el texto a partir de una lista de diccionarios
3. El modulo de `crear_nombre_archivo(filtro)` crea a partir de un diccionario un string
4. Para finalizar está la funcion `crear_archivos_markdown(texto, nombre)` crea archivos markdown de nombre el nombre pasado, y de contenido el texto pasado.

Luego está la funcion `mover_markdowns(ruta_destino)` la cual simplemente copia los archivos en la carpeta creada dentro del programa, y la mueve a la carpeta que se especifique como parametro 

Despues estan separadas del resto las demás funciones CRUD.
1. a
2. b
3. c
## Esquema
```json
{
	'_id': ObjectID(90823649081326749082136492304),
	'PricePack': String,
	'NamePack': String,
	'ContenPack': String,
	'HasCupon': Boolean,
	'HasParking': Boolean
}

$jsonSchema: {
            bsonType: "object",
            required: ["PricePack","NamePack","ContentPack","HasCupon","HasParking"],
            properties: {
                "_id":{},
                "PricePack":{
                    bsonType: "string",
                    description: "The price of the Pack"
                    //debe ser 0 (Free) o x (buy)
                },
                "NamePack":{
                    bsonType: "string",
                    description: "The name of the Pack"
                },
                "ContentPack":{
                    bsonType: "array",
                    items: {
                        bsonType:"object",
                        required: ["name"],
                        properties:{
                            name:{
                                bsonType:"string",
                                description: "este es el nombre del elemento del pack"
                            },
                            description:{
                                bsonType:"string",
                                description: "esta es la descrición del elemento"
                            }
                        }
                    }
                },
                "HasCupon":{
                    type:"boolean",
                    description:"Para saber si tiene o no descuento el pack"
                },
                "HasParking":{
                    bsonType:"bool",
                    description:"Para saber si el pack es solo para los que tienen parking"
                }
            }
        }
```
# Implementacion
Aqui explicaremos las diferentes herramientas que se han utilizado para la creación del software, separa en BackEnd, FrontEnd y General:
- BackEnd:
	- MongoAtlas: Servicio que nos permite tener bases de datos en la nube
	- Python: Lenguaje de programacion con el que se ha programado todo el programa
	- Modulo de python: Hemos usado diversos modulos que nos facilitaban ciertas tareas:
		- pymongo: Nos permite realizar la conexion a la base de datos y trabajar con los datos que haya dentro
		- certifi: Necesario para conectarse con la base de datos de manera correcta
		- os: Nos permite trabajar con directorios
		- shutil: Necesario para copiar archivos de una carpeta a otra 
- FrontEnd
	- Hugo: Es un generador de sitios estaticos en cual utilizamos para poder visualizar los documentos makrdown
- General
	- VSCode: Editor de texto en el cual hemos programado todo el codigo
	- Git: Control de versiones
# Pruebas
## Accesso a datos
Con las funciones de acceso a datos no hemos realizado muchas pruebas.

- `obtener_cluster(uri)`. Hemos comprobado que una vez dentro de un cluster nuestro esté una BBDD especifica.
```python
ruta = "mongodb+srv://m001-student:12345@sandbox.glkvp.mongodb.net/myFirstDatabase?retryWrites=true&w=majority"
cluster = obtener_cluster(ruta)
assert "amenities" in cluster.list_database_names()
```

- `obtener_bd(cluster, bd)`. Hemos comprobado que dentro de una BBDD nuestra esté una coleccion especifica.
```python
ruta = "mongodb+srv://m001-student:12345@sandbox.glkvp.mongodb.net/myFirstDatabase?retryWrites=true&w=majority"
cluster = MongoClient(ruta)
db = cluster["amenities"]
assert "packs2" in db.list_collection_names()
```
## Logica
`obtener_documentos(coleccion, filtro)`. 
La funcion a partir de una coleccion llena de documentos busca solo los documentos que concuerdan con el filtro.
1. Creamos una coleccion usando las funciones que hemos creado.
2. Creamos un filtro, un diccionario, en base a dos valores llamados `clave_filtro`, `valor_filtro`.
3. Despues utilizando la funcion que está siendo testeada obtenemos una lista de diccionarios
4. Por ultio comprobamos que cada diccionario dentro de esta lista tenga de clave-valor los que le hemos pasado.
```python
cluster = obtener_cluster(
	"mongodb+srv://matias:12345@proyecto.bjagm.mongodb.net/myFirstDatabase?retryWrites=true&w=majority"
)
db = obtener_bd(cluster, "prueba")
coleccion = obtener_coleccion(db, "prueba")

clave_filtro = "r"
valor_filtro = 125

filtro = {clave_filtro: valor_filtro}

lista_docs = obtener_documentos(coleccion, filtro)

for doc in lista_docs:
	assert doc[clave_filtro] == valor_filtro
```
Otro test es comprobar que sucede cuando el filtro esta vacio.
1. Lo unico diferente es cuando utilizamos la funcion de obtener documentos, a está le pasamos un diccionario vacio, por lo que debería volver todos los documentos dentro de una coleccion.
2. Despues comprobamos que la cantidad de documentos dentro de la lista sea la misma que los que hay en la coleccion.
```python
cluster = obtener_cluster(
	"mongodb+srv://matias:12345@proyecto.bjagm.mongodb.net/myFirstDatabase?retryWrites=true&w=majority"
)
db = obtener_bd(cluster, "prueba")
coleccion = obtener_coleccion(db, "prueba")

numero_documentos = coleccion.count_documents({})

filtro = {}

lista_docs = obtener_documentos(coleccion, filtro)

assert numero_documentos == len(lista_docs)
```
`obtener_texto_para_markdown(lista_documentos)`.
La funcion crea a partir de una lista de diccionarios un string. En este test solo hay una prueba.
1. Primero creamos una lista de diccionarios
2. Despues el texto que deberia dar una vez llamada a la funcion
3.  Por ultimo comprobamos que utilizando la funcion pasando la lista de diccionarios devuelva exactamente el texto que hemos creado

```python
lista_documentos = [
	{
		"_id": {"$oid": "619a9b91a2b4bbbb8e69bc60"},
		"PricePack": "Free",
		"NamePack": "Free Pack",
		"ContentPack": "This pack includes a bag full of sweets",
		"HasCupon": False,
		"HasParking": False,
	},
	{
		"_id": {"$oid": "619a9b92a2b4bbbb8e69bc61"},
		"PricePack": "5€",
		"NamePack": "Tier 1 Pack",
		"ContentPack": "this low-priced pack includes a bag of sweets plus an organized hotel welcome ",
		"HasCupon": False,
		"HasParking": False,
	},
]

texto_resultante = "# Free Pack\n\nThis pack includes a bag full of sweets\n\nEl precio de este pack es: Free\n\n_Cupon_ ❌\n\n_Parking_ ❌\n\n# Tier 1 Pack\n\nthis low-priced pack includes a bag of sweets plus an organized hotel welcome \n\nEl precio de este pack es: 5€\n\n_Cupon_ ❌\n\n_Parking_ ❌\n\n"

assert obtener_texto_para_markdown(lista_documentos) == texto_resultante
```
`crear_nombre_archivo(filtro)`.
Esta función a partir de un diccionario devuelve un string. En el primer test hay 3 subtest que comprueban lo mismo.
1. Creamos un filtro para pasarle a la funcion
2. Y llamamos a la funcion con este filtro comrobando sea igual a una string que creamos en el test
```python
filtro = {"a": 1}
assert crear_nombre_archivo(filtro) == "a1"

filtro = {"a": 1, "b": "alohomora"}
assert crear_nombre_archivo(filtro) == "a1balohomora"

filtro = {"a": 1, "b": "alohomora", "c": [1, 2, 3]}
assert crear_nombre_archivo(filtro) == "a1balohomorac[1, 2, 3]"
```
`crear_archivos_markdown(texto, nombre)`.
Esta crea archivos markdown a partir de dos strings, la primera el texto que será escrito dentro del archivo y la segunda el nombre del archivo. En esta funcion hay varios test. El primero comprobamos si funciona pasando parametros normales.
1. Primero creamos dos strings para pasarle a la funcion
2. Depues llamamos a la funcion pasado estos strings
3. Luego creamos una ruta en la cual está el archivo recien creado y comprobamos si ese arhivo existe
4. A continuacion abrimos el arhivo en python
5. Creamos un acumulado y guardamos dentro cada linea del archivo
6. Para finalizar comprobamos que el acumulador sea exactamente igual al texto que le pasamos al inicio
```python
texto = "texto1"
nombre = "nombre1"

crear_archivos_markdown(texto, nombre)

ruta_archivo = "./markdowns/" + nombre + ".md"

assert path.isfile(ruta_archivo)

archivo = open(ruta_archivo, "r")

acu = ""
for linea in archivo.readlines():
	acu += linea
	
assert texto == acu
```
El segundo test comprueba que sucede cuando el filtro texto esta vacio. En este test se reutiliza el mismo codigo que en test anterior, ademas de una linea la cual utiliza la funcion `getsize`. En esta linea comprobamos que el tamaño del archivo que hemos creado sea 0.
```python
texto = ""
nombre = "nombre2"

crear_archivos_markdown(texto, nombre)

ruta_archivo = "./markdowns/" + nombre + ".md"

assert path.isfile(ruta_archivo)

archivo = open(ruta_archivo, "r")

acu = ""
for linea in archivo.readlines():
	acu += linea

assert texto == acu
assert path.getsize(ruta_archivo) == 0
 ```
El ultimo test comprueba que sucede cuando el nombre esta vacio. Al igual que el anterior el codigo es practicamente el mismo que el primero, con la unica diferencia de que al crear la variable `ruta_archivo`, en vez de poner la variable nombre, pone `default`, que es el nombre que le hemos puesto por defecto a la funcion.
```python
texto = "texto2"
nombre = ""

crear_archivos_markdown(texto, nombre)

ruta_archivo = "./markdowns/" + "default" + ".md"

assert path.isfile(ruta_archivo)

archivo = open(ruta_archivo, "r")

acu = ""
for linea in archivo.readlines():
	acu += linea
	
assert texto == acu
```
`mover_markdowns(ruta_destino)`.
Este modulo copia todos los archivos dentro de la carpeta `markdown`, carpeta que hemos creado en el otro modulo, dentro de la carpeta en `ruta_destino`. Solo hay un test que comprueba que funcione.
1. Especicamos la carpeta donde estan los archivos markdown.
2. Despues guardamos la ruta de donde copiaremos los archivos.
3. Llamaremos a la funcion pasandole la `ruta_destino`.
4. Para finalizar, comprobamos que en la `ruta_destino` hayan la misma cantidad de archivos que en la `ruta_origen`
```python
ruta_origen = "./markdowns"
ruta_destino = "./logica/test/carpeta_de_prueba/"

mover_markdowns(ruta_destino)

assert len(listdir(ruta_origen)) == len(listdir(ruta_destino))
```

s|fssgsadfsadf|afdasdfdasf|dsfgsdhhgbkdm|gijsdogikjoi0|oañisjgoiejvoidgpokpo|oañisjgoiejvoidgpokpo|oañisjgoiejvoidgpokpoaoañisjgoiejvoidgpokpo|oañisjgoiejvoidgpokpoqoañisjgoiejvoidgpokpo|oañisjgoiejvoidgpokpoa|q|a|q|a|q|a|q
:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:
j|r|k