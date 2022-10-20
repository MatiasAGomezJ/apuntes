# Procedimiento y comandos básicos de Git
Se asume que estamos trabajando en una carpeta exclusiva para el repositorio, es decir la carpeta solo contiene archivos de repositorio.
## 0: Cosas que tener antes
1. El repositorio al que quieres subir los archivos. Al crear un repositorio te dan una URL que necesitaremos copiar para trabajar con el. En este caso la URL de mi repositorio es: https://github.com/MatiasAGomezJ/apuntes.git

2. La carpeta en la que vas a trabajar
	P.ej:
	```bash
	~/Documentos/Repositorios/Proyecto_PyDevops
	```
##  1: Proceso de creacion y subida de archivos a un repositorio
Sin el siguiente comando no se pueden hacer control de versiones, por lo tanto es lo primero que deberemos hacer a la hora de trabajar con git.
```bash
$ git init
```
 Esto creara una carpeta oculta con archivos de configuración.
 
Crearemos el primer documento, en este caso lo llamaré `documento1`.

El comando `$ git status` muestra el estado de los archivos con respecto al repositorio, como lo acabamos de crear nos dirá que esta **untracked**.
```bash
$ git status

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        documento1
```
Para añadirlo utilizaremos:
- Para añadir todos los archivos
```bash
$ git add . 
```
- Para añadir solo un archivo
```bash
$ git add nombre_del_archivo
```
Ahora el archivo esta en estado **Stage**.
```bash
$ git status

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   documento1
```
El siguiente paso es commitear
```bash
$ git commit -m "Esto es un comentario"
```
Al hacer un commit estamos poniendo en una cola de espera a los archivos en los que hayamos usado el `$ git add`. El siguiente paso es hacer el `$ git push` pero todavia no hemos especificado a que repositorio vamos a subir los archivos.
> Nota: el parametro `-m` sirve para añadir un comentario, si lo omitimos nos saldra el editor de texto **VIM** para añadir el comentario
> ***IMPORTANTE***. Al hacer un commit sera totalmente necesario hacer un comentario, si no, no dejará subirlo.

Para añadir nuestro repositorio vacio utilizaremos:
```bash
$ git remote add origin *URL*
```
Si hacemos  lo siguiente mostrará dos links, uno de `(fetch)` y otro de `(push)`, significa que todo esta bien.
```bash
$ git remote -v
origin https://github.com:MatiasAGomezJ/my-obsidian-vault.git (fetch)
origin https://github.com:MatiasAGomezJ/my-obsidian-vault.git (push)
```
Siguiendo con el proceso de antes, haremos un `$ git push` esto subira, por fin, los archivos de tu dispositivo al repositorio.
```bash
$ git push -u origin master
```
Sera necesario, *creo*, especificar la rama a la que subiremos los archivos, en este caso es la rama `master`, que se crea automaticamente cada vez que creemos un repositorio.
> Nota: Ni idea para que sirve el `-u origin`.
> Nota 2: Solo hace falta utilizar este comando 1 vez, despues se puede utilizar `$ git push` y ya asumirá la rama en la que subira los archivos. Si queremos cambiar de rama tendremos que volver a especificar.
> Fin de la nota.

Hecho esto ya se estarán subidos los archivos en GitHub.
##  2. Proceso de clonacion y descarga de un repositorio
**ESTAMOS EN OTRA MAQUINA** o otra carpeta.

El primer paso para clonar un repositorio es ir a la pagina de este y copiar su *URL*. Teniendo esto podemos utilizar el siguiente comandillo.
```bash
$ git clone https://github.com/MatiasAGomezJ/apuntes.git
```
Hecho esto estará descargada la ultima version del repositorio.
>***IMPORTANTE***. Al hacer una clonacion no estas descargando los archivos en una carpeta estas **descargando el repositorio como carpeta**

P.ej:
Mi repositorio de `apuntes`, tiene el archivo `"Procedimiento y comandos básicos de Git"`.
Si hago una clonacion en la carpeta `Proyecto_PyDevops`:
```bash
~/Documentos/Repositorios/Proyecto_PyDevops$ ls
archivo1
~/Documentos/Repositorios/Proyecto_PyDevops$ git clone https://github.com/MatiasAGomezJ/hello-world-dual.git
Cloning into 'hello-world-dual'...
.
.
```
Sucederá esto:
```bash
~/Documentos/Repositorios/Proyecto_PyDevops$ ls
archivo1 apuntes/
```
**No esto**:
```bash
~/Documentos/Repositorios/Proyecto_PyDevops$ ls
archivo1 .git documento1
```
En el segundo pone los archivos directamente en la carpeta en la que se ha clonado, esto **NO SUCEDE**.
> Hasta aquí la nota IMPORTANTE

Una vez clonado, si hacemos algun cambio no modificaremos ni el que esta en el otro ordenador, ni el de github. Solo el de este ordenador.

Si hacemos un `$ git status` nos dirá que el archivo modificado hace falta subirlo. Asi que utilizaremos los comandos de antes para *pushearlo*.
```bash
$ git add .
$ git commit -m "He modificado el archivo documento1"
$ git push -u origin master
```
Como estan intentando modificar los archivos de un repositorio necesitaremos nombre y contraseña
```bash
Username for "https://github.com": nombre_del_github
Password for "https://nombre@github.com": *access token*
```
> ***access token***: En GitHub > Settings > Developer settings > Personal access tokens, ahí crearemos una password y lo guardaremos.

Y se habrán subido los cambios al repositorio.

Para finalizar haremos un `$ git log` y veremos todo los cambios que hicimos tanto en la primera maquina como en esta.
## 3. Actualizar datos viejos
Vamos a empezar haciendo un `$ git log` y veremos solo los cambios hechos en esta maquina. Para actualizar los datos necesitamos hacer un pull.
```bash
$ git pull
```
## 4. Mas cosas/datos importantes
1. Con el comando git checkout se puede volver a una version anterior con el incide del commit.
	```bash
	$ git checkout *indice_del_commit*
	```
 2. Cada repositorio tiene una rama master, y ya si eso se crean secundarias
  
 3. Usar `$ git clone URL` crea automaticamente un archivo de configuracion `.git`, que normalmente se crea con el `$ git init`.
 4. Usar `$ git log` para ver los ultimos cambios del repositorio.
 5. Por cada archivo modificado o creado tienes que hacer un add, commit, push, y en el otro dispositivo se tiene que hacer un pull
 6. La unica manera de que no pida la contraseña se necesita el git console gh. Ya lo enseñará. Spoiler: Hay otra manera
 7. Cada vez que hacemos un commit se crea un indice unico en base a los archivos que existen para verlo usaremos `$ git log --oneline`.
## 5. Resumen de los pasos
#### Queremos crear un repositorio
1. **Creamos el repositorio en GitHub y pillamos su *URL***

2. **Creamos una carpeta en la que queremos que esten los archivos y escribimos `$ git init` para crear la configuracion**. Se podria decir que ya esta configurado el control de versiones, que es lo que nos permite usar los comando git.
3. **Lo siguiente es crear archivos nuevos moviendolos a esta carpeta o creandolos**.
4. **Los añadiremos con `$ git add .`**.
5. **Despues haremos un commit con `$ git commit -m "Comentario"`**.
6. **Añadiremos el repositorio al que subiremos los archivos con `$ git remote add origin URL`**.
7. **Por ultimo lo pushearemos con `$ git push -u origin master`**.
8. Y ya estará subido al GitHub.
9. **Si hay nuevos cambios, usamos `$ git pull`**.
#### Queremos clonar un repositorio
1. **Primero pillaremos la *URL* del repositorio que queremos clonar**.

2. **Iremos a la carpeta en la que queramos que este la carpeta del repositorio con sus archivos**. Como he dicho antes, no soltara los archivos en la carpeta, los pondrá en una carpeta con el nombre del repositorio y dentro sus archivos.
3. **Utilizaremos `$ git clone URL`**.
4. Y ya estará descargado.
5. **Si hay nuevos cambios, usamos `$ git pull`**.
## 6. Resumen resumido
1. `$ git init`. La configuración

2. `$ git add`. Añadir archivos nuevos o modificados.
3. `$ git commit -m "Coment"`. Poner los archivo a la cola de espera, el ultimo paso antes se subirse.
4. `$ git remote add origin URL`. Este paso puede ser 2º, 3º o 4º. Añade el repositorio a la carpeta.
5. `$ git push -u origin master`. Sube los archivos.

Si queremos clonar

6.  `$ git clone URL`. Clona el repositorio.

Si quereremos actualizar

6. `$ git pull`. Actualiza el repositorio.
