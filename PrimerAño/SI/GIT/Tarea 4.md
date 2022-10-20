# Tarea 4 - Trabajando con ramas
## 0. Colocarse
Primero de todo nos colocaremos en la carpeta de un repositorio, ya sea mediante creandolo nosotros con un `git init` o clonandolo con un `git clone`.
```bash
~/Documentos/Repositorios/ramas
$ git init
```
o
```bash
~/Documentos/Repositorios
$ git clone https://github.com/MatiasAGomezJ/ramas.git
...
$ cd ramas
```
![](https://i.imgur.com/Rr48dNJ.png)
##  1. Crear una rama
Para crear una rama usaremos el siguiente comando
```bash
$ git branch readme-changes
```
Y despues para colocarnos dentro de ella usaremos:
```bash
git checkout readme-changes
```
![](https://i.imgur.com/eH8OgRE.png)
##  2. Git add
A continuacin, podemos modificar o crear documentos, en este caso yo modificare el README.md con el comando `nano`
![](https://i.imgur.com/NTBbKFW.png)

![](https://i.imgur.com/XFIGAJg.png)

Y despues lo añadiremos
```bash
git add README.md
```
![](https://i.imgur.com/l4SR10V.png)
##  3. Git commit
Hecho esto le haremos un commit:
```bash
git commit -m "Cambio readme"
```
![](https://i.imgur.com/0DteLyi.png)
##  4. Git push
Y para finalizar lo subiremos al GitHub, especificando la rama
```bash
git push --set-upstream origin readme-changes
```
![](https://i.imgur.com/WgSwSU5.png)
## Fin
En el repositorio se podrá ver que hay dos ramas y que en una el readme está modificado.
![](https://i.imgur.com/824JEN2.png)
