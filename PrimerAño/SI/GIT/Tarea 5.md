# Tarea 5 - Trabajando con ramas
Esta tarea va a ser mas rapida que las anteriores

## 1. Creacion y subida de archivos en rama
Primero de todo clonaremos el repositorio con lo siguiente:

Lo siguiente que haremos será moveremos a una rama con el comando:
```b
$ git checkout rama
```
![](https://i.imgur.com/ZPCQ8l3.png)

Una vez alli, sencillamente crearemos o moveremos archivos a la carpeta del repositorio, para despues hacer la sucecion clasica de comandos -> add, commit, push
```b
$ touch documento5.py
$ git add .
$ git commit -m "documento5"
$ git push -u origin Matias-ramit
```
![](https://i.imgur.com/XpvnswT.png)

Y ya tendremos el archivo subido al repositorio

## 2. Merge de las ramas
Para ello tenemos que ir a la rama principal, en este caso la main:
```b
$ git checkout main
```
![](https://i.imgur.com/Qx3oxmr.png)

Luego usamos el siguiente comando para decidir que rama queremos mezclar on la main.
```b
$ git merge JuanC-ramita
```
![](https://i.imgur.com/zXiMv8J.png)

En este caso sale un conflicto ya que el se han hecho cosas diferentes con el mismo archivo, si hacemos un status podemos ver que simplemente haciendo un `add` podemos arreglar el problema.
![](https://i.imgur.com/mqALJSS.png)

Y ya tendremos la rama mezclada con la principal
