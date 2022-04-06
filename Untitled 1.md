# Docker-APIRest
## Creando una imagen personalizada para la API REST con Flask y Mongo Atlas en Docker
Trabajo realizado por [Matias Gomez](https://github.com/MatiasAGomezJ/) & [Andreu Sorell](https://github.com/AndreuSorell/)
## Índice
1. Crear imagen personalizada de la API
2. Subir imagen a docker hub
3. Publicar la API a través de una máquina Azure
## 1. Crear imagen personalizada de la API
Para empezar clonaremos el repo en el cual está la API.
```bash
$ git clone git@github.com:MatiasAGomezJ/ollivanders-flask.git
```
![](https://i.imgur.com/iVekSWk.png)

Ya clonado, entraremos en la carpeta y crearemos un `Dockerfile` con la siguiente información.
```Dockerfile
FROM python:3.8-alpine

EXPOSE 5000

COPY ./requirements.txt /app/requirements.txt
WORKDIR /app
RUN pip install -r requirements.txt
COPY . /app

CMD ["python3", "api.py"]
```
![](https://i.imgur.com/DbN30BV.png)

Una vez guardado utilizaremos el siguiente comando para crear la imagen.
```bash
$ docker build -t ollivanders-api .
```
![](https://i.imgur.com/IRSPtwM.png)

Despues de que instale todo lo necesario para poder utilizar la API podemos comprobrar que funciona usando el siguiente comando.
```bash
$ docker run ollivanders-api
```
![](https://i.imgur.com/EpOTZur.png)

Podemos cromprobar que funciona entrando en el link que nos indica por consola.
![](https://i.imgur.com/pvjNZZ4.png)

## 2. Subir imagen a docker hub
Para poder subir una imagen a docker hub necesitaremos tener una cuenta creada, en esta guia no se explicará ya que es algo muy sencillo.

Con la cuenta creada nos iremos a la consola y utilizaremos el siguiente comando.
```bash
$ docker tag nombre_imagen nombre_usuario/nombre_imagen
```
![](https://i.imgur.com/JaZ7Vm6.png)

Para acabar subiremos la imagen con el siguiente comando.
```bash
$ docker push nombre_usuario/nombre_imagen
```
![](https://i.imgur.com/cpYxdfR.png)

Cuando haya acabo de subirse la imagen podemos irnos a nuestro usuario y veremos que está la imagen.
![](https://i.imgur.com/C4rk3KV.png)

## 3. Publicar la API a través de una máquina Azure
