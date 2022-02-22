# Tarea 1 - Comandos básicos de Git
0. Introducción
1. Git init
2. Git remote add origin *URL*
3. Git add
4. Git commit
5. Git push
## 0. Introducción
En este trabajo se verán los comandos basicos de git, el objetivo será subir un archivo README.md a un repositorio de GitLab.

Se asume que:
- Se tiene el conocimiento basico de comandos en la terminal. Por ejemplo comandos para la creacion de carpetas, archivos y comandos para moverse entre carpetas.
- Tener instalado [Git](https://git-scm.com/).
- Tener un repositorio creado, en este caso se utiliza uno en [GitLab](https://about.gitlab.com/).
## 1. Git init
Primero de todo utilizaremos el comando `git init` en la carpeta que queremos guardar el repositorio.
```bash
~/Documentos/Repositorios/tarea1
$ git init
```
![](https://i.imgur.com/sH8iyHu.png)
Esto nos permitira usar el control de veriones y poder utilizar los comandos que proporciona Git.
## 2. Git remote add origin *URL*
Con los ya disponibles comandos de git añadiremos el repositorio al que queremos subir los archivos, en este caso el repositorio esta en `git@gitlab.com:mgomez9/tarea1.git`, por lo tanto utilizaremos el siguiente comando para añadir el repo.
```bash
~/Documentos/Repositorios/tarea1
$ git remote add origin git@gitlab.com:mgomez9/tarea1.git
```
![](https://i.imgur.com/rRA8qGE.png)
En la foto utilizo el comando `$ git remote -v`, este sirve para ver a que repositorio esta conectado, lo he puesto para comprobrar que todo haya ido correctamente.
## 3. Git add
Hecho eso ya podemos trabajar con archivos, es esta tarea lo primero que haremos será crear un documento README.md y despues utilizaremos `git add` para empezar el proceso de subida.
```bash
~/Documentos/Repositorios/tarea1
$ touch README.md
```
![](https://i.imgur.com/r7IDSdN.png)
Antes de hacer el `add` haremos un `status`
```bash
~/Documentos/Repositorios/tarea1
$ git status
```
![](https://i.imgur.com/COlG9Dp.png)
Esto lo que nos muestra es que en el proceso de subida todavia estamos abajo del todo, asique el primer paso para subir el archivo al repositorio sera con un `add`.
```bash
~/Documentos/Repositorios/tarea1
$ git add .
```
![](https://i.imgur.com/zvH43MI.png)
## 4. Git commit
El `commit` es el siguiente paso para actualizar los datos en un repositorio.
![](https://i.imgur.com/Ca1qt73.png)
Ahora en el status nos pide hacer un `commit` asi que lo haremos.
```bash
~/Documentos/Repositorios/tarea1
$ git commit -m "Primer commit"
```
![](https://i.imgur.com/xWbJP0K.png)
El comando `git commit` requiere que especifiquemos un comentario, esto se puede hacer en el mismo comando, como se muestra en la imagen, o si no ponemos ningún parametro, nos saldrá un editor para añadirlo.
## 5. Git push
El `push` es el último comando para subir los archivos al repositorio. 
```bash
~/Documentos/Repositorios/tarea1
$ git push -u origin master
```
![](https://i.imgur.com/pPXYeRU.png)

## Fin
Y con esto ya estara subido a GitLab el archivo README.md
https://gitlab.com/mgomez9/tarea1

![](https://i.imgur.com/ndb8dSo.png)
