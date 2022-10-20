# Practica PostgreSQL
# 0. Introducción
Antes de empezar a tocar la base de datos de postgress primero vamos a ver como instalarla. Para ello lo utilizaremos docker-compose.

Primero crearemos un arhivo llamado `docker-compose.yml`, en un directorio cualquiera, con la siguiente información.
```yml
# Use postgres/example user/password credentials
version: '3.1'

services:

  db:
    image: postgres
    restart: always
    environment:
      POSTGRES_PASSWORD: example

  adminer:
    image: adminer
    restart: always
    ports:
      - 8080:8080
```

![](https://i.imgur.com/GoR4EZF.png)

Con el archivo guardado nos iremos a la terminal y accederemos a la carpeta donde esté el archivo. Una vez allí ejecutaremos el siguiente comando para descargar, instalar y levantar los contenedores.

```bash
$ docker-compose up -d
```
> El parametro `-d` se utiliza para que se ejecute en modo demonio, no muestra por consola el log de la maquina virtual.

![](https://i.imgur.com/ou8ZLeo.png)

Para acabar el comienzo, podemos entrar en la base de datos de 2 maneras:
1. Por la url `localhost:8080`
2. Por consola utilizando el siguiente comando

```bash
$ docker exec -it postgress_db_1 bash
```
> Este comando nos deja entrar en el contenedor de la base de datos con la shell `bash`.
> Para saber a que contenedor entrar haremos `docker ps` que lista todos los contenedores abiertos.

![](https://i.imgur.com/u9eCCMJ.png)

**PLOT TWIST!**

Todavía no hemos entrado en la base de datos (aunque para los primeros ejercicios no hace falta), hemos entrado en su sistema operativo, para entrar a la bbdd primero nos cambiaremos de usuario:

```bash
$ su - postgres
```

Y despues accederemos a la bbdd

```bash
$ psql
```

![](https://i.imgur.com/NBI2XSG.png)

# 1. Crea un usuari alumne amb clau passalu amb la comanda createuser
Para ello, en la consola del SO del contenedor, ejecutaremos el siguiene comando:
```bash
$ createuser alumne --pasword
```
> `alumne`: nombre del usuario que vamos a crear
> `password`: preguntará por una contraseña para el usuario

![](https://i.imgur.com/NGO6CUX.png)

# 2. Crea un usuari alumne0 amb clau passalu i permisos de superusuari amb la comanda createuser
Para crear un usuario con permisos de superusuario simplemente añadiremos el parametro -s al comando anterior:
```bash
$ createuser alumne0 --pasword -s
```
> `alumne0`: nombre del usuario que vamos a crear
> `password`: preguntará por una contraseña para el usuario
> `-s`: creará el usuario con poderes de administrador

![](https://i.imgur.com/2WUgpgv.png)

# 3. Crea una base de dades aludb amb la comanda createdb, assigna alumne0 com propietari
En bash ejecutaremos el siguiente comando.
```bash
$ createdb aludb -O alumne0
```
> `aludb`: nombre de la db que vamos a crear
> `-O`: sirve para indicar el nombre del propietario de la db
> `alumne0`: el propetario de la db
 
![](https://i.imgur.com/oPiU1Y0.png)

Para comprobar que ha funcionado correctamente el comando entraremos en la base de datos y listaremos las dbs.

Para entrar:
```bash
$ psql
```

Para listar las dbs:
```sql
\l
```
![](https://i.imgur.com/ch9W673.png)

Podemos ver que está creada la base de datos aludb con su *owner* alumne0.

# 4. Afegiu la següent taula a la base de dades aludb
```sql
CREATE TABLE R (  
	A int primary key,  
	B text  
);  
INSERT INTO R VALUES (1,'a'), (2,'b'), (3,'c'), (4,'d');
```

Primero entraremos a la base de datos como `alumne0`:
```sql
\c aludb alumne0
```
> `aludb`: db a la que nos conectaremos
> `alumne0`: usuario con la que se conectará

![](https://i.imgur.com/yS16eju.png)

Hecho esto realizaremos el siguiente comando para crear la tabla e instertar valores en ella:
```sql
CREATE TABLE R (
	A int primary key,  
	B text  
);  
INSERT INTO R VALUES (1,'a'), (2,'b'), (3,'c'), (4,'d');
```
![](https://i.imgur.com/JRLFp1o.png)

Para comprobrar que se ha creado podemos utilizar el siguiente comando para mostrar todas las tablas de la base de datos:
```sql
\d
```
![](https://i.imgur.com/Z5u4XWY.png)

# 5. Connectats amb l’usuari alumne a aludb, intentau executar:
```sql
SELECT * FROM R;
```
Para conectarnos a la base de datos como `alumne` utiliaremos el comando que hemos hecho en el ejercicio anterior:
```sql
\c aludb alumne
```
![](https://i.imgur.com/WBocTMW.png)

E intentaremos realizar el siguiente comando:
```sql
SELECT * FROM R;
```
![](https://i.imgur.com/SXwN8dR.png)

Pero no nos dejará ya que el usuario `alumne` no tienes permisos para realizar busquedas en la db `aludb`.
# 6. Donau permisos de “SELECT” a l’usuari alumne a la taula R.
Para poder dar diversos permisos a otros usuarios en una tabla deveremos entrar como el owner de ella, en este caso, como `alumne0`, para ello haremos el siguiente comando:
```sql
\c aludb alumne0
```

![](https://i.imgur.com/ltqQoeX.png)
 
 Dentro ejecutaremos el siguiente comado para dar permisos.
 ```sql
GRANT SELECT ON R TO alumne;
```
> `SELECT`: es el tipo de permisos que vamos a conceder. Que?
> `ON R`: en que tabla los vamos a conceder. Donde?
> `TO alumne`: a quien se lo vamos a conceder. Quien?

 ![](https://i.imgur.com/Uj2QEI6.png)
# 7. Connectats amb l’usuari alumne a aludb, intentau executar:  
```sql
SELECT * FROM R;
```

Ya con los permisos concedidos deberiamos ser capaces de acceder con `alumne`:
```sql
\c aludb alumne
```
![](https://i.imgur.com/ub7yoeY.png)

Y poder hacer el siguiente comando:
```sql
SELECT * FROM R;
```
![](https://i.imgur.com/a38bVjw.png)

# 8. Eliminau els usuaris i bases de dades creats.
Para borrar los usuarios y las db podemos hacerlos de dos maneras:
- Desde la shell bash del contenedor
- Desde la base de datos

### Desde el bash:
Para borrar una db
```bash
$ dropdb aludb
```
> `aludb`: nombre de la db a borrar

![](https://i.imgur.com/wA0i0Ot.png)

Parra borrar los usuarios
```bash
$ dropuser alumne
$ dropuser alumne0
```
>`alumne`/`alumne0`: usuario a borrar

![](https://i.imgur.com/36sKTP5.png)
 
 Ya que no da error significa que todo ha ido correctamente.
 
 ### Desde la db
 Dentro de la db sin entrar en ningún sitio.
 Para borrar una db
 ```sql
 DROP DATABASE aludb
 ```
![](https://i.imgur.com/nektViZ.png)

  Para borrar los usuarios
 ```sql
 DROP USER alumne
 DROP USER alumne0
 ```
 ![](https://i.imgur.com/XOOzyZh.png)
