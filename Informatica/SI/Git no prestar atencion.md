# Git no prestar atencion
```
$ git init
```
Aparece un fichero git con configuraciones
```
$ vim .git/
```
Opciones/Configuracion??
```
$ touch nombre_fichero

$ git status
```
Si esta en tu directorio de trabajo pero no en git, esta **untracked**
```
$ git add nombre_fichero
```
El fichero cambia de estado cambia a Stage
```
$ vim nombre_fichero
```
Para modificar el archivo
```
$ git status
```
El archivo esta Modified
```
$ git status
```
Ahora esta Stage
```
$ touch fichero_2
```
El fichero_2 esta **untracked**
```
$ git add fichero_2
```
Ahora los dos archvos estan en Stage
```
$ git commit -m "Aqui va un comentario"
```
Todavia no estan en git

>En git crearemos un nuevo repositorio, en este ejemplo se llarará "Hola Mundo"



Para configurar el git/github con tu ordenador
```
$ git remote add origin *URL*
$ git remove -v
Aparecerán la *URL* del remoto
```

> La url sera algo asi como:
> https://www.github.com/tunombre/nombre-del-repositorio.git
```
$ touch laestoyliando
$ git add laestoyliando
```
```
$ git status
```
El archivo esta staged
```
$ git add nombre_fichero fichero_2
$ git commit -m "Aqui va otro comentario"
```
Para confirmar los cambios del último **commit** y guardarlos en el repositorio **main**.
```
$ git push origin main
```

## True comienzo

Sin el siguiente comando no se pueden hacer control de versiones, y crea un fichero con opciones
```
$git init
```

$ touch documento1

$ git status
no esta bien

$ git add documento1
Los ficheros estan en Stage

$ git status
Ya esta bien 

$ touch documento2
El fichero se tiene que añadir

$ git status
no esta bien

$ git add documento2
Los ficheros estan en Stage

$ git status
Ya esta bien 

$ git commit -m "Esto es un comentario"

Cuando commiteas se ponen en la cola de espera para subir.


Antes de hacer el `$ git push`, hay que crear el repositorio

En este ejemplo el repositorio se llama hello-world-dual

```
$ git remote -v
```
No aparece nada todavia
```
$ git remote add origin *URL*
$ git remote -v
```
Ahora aparece la url del repositorio al que se va a subir

Para confirmar los cambios del último **commit** y guardarlos en el repositorio **master**.
```
$ git push -u origin <ins>master</ins>
```
Y los archivos se han subido correctamente, espero

**ESTAMOS EN OTRA MAQUINA**: Vamos a clonar un branch del repositorio
```
$git clone *URL*(que pillas en la pagina del clon)
```
```
$ git pull
Already up to date.
```
Modificamos un archivo.
```
$ touch documento2
```
Modificando el archivo no modifica ni el que esta en el otro ordenador, ni el de github
```
$ git status
```
Dice que el archivo esta modificado, y por lo tanto hay que hacer el siguiente comando para subirlo
```
$ git add documento2
$ git status
```
Ahora el archivo ya esta agragado y puede ser commiteado

$ git commit -m "Esto es un comentario desde otro dispositivo"
Commiteado

```
$ git push origin master
```
Como estan intentando modificar los archivos de un repositorio necesitaremos nombre y contraseña
```
Username for "https://github.com": nombre
Password for "https://nombre@github.com": *access token*
```
Y ya se habran subido los cambios

**VOLVEMOS A LA PRIMERA MAQUINA**
Si hacemes un *git log*, no veremos las ultimas modificaciones de la otra maquina
Para actualizar los datos necesitamos hacer un pull
```
$ git pull
```

**Post**
Con el comando git checkout se puede volver a una version anterior con el incide del commit.

$ git checkout *indice_del_commit*


COSAS IMPORTANTES:
Dicho por el profesor: Cada repositorio tiene una rama master, y ya si eso se crean secundarias

Usar *git clone URL* crea automaticamente un archivo de configuracion .git, que normalmente se crea con el *git init*

Usar *git log* para ver los ultimos cambios del archivo

Por cada archivo modificado o creado tienes que hacer un add, commit, push, y en el otro sidpositivo se tiene que hacer un pull

La contraseña que necesitas para modificar un repositorio

La unica manera de que no pida la contraseña se necesita el git console gh. Ya lo enseñará. Spoiler: Hay otra manera

Cada vez que hacemos un commit se crea un indice unico en base a los archivos que existen
$ git log --oneline
