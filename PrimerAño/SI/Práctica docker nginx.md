# Práctica docker nginx
## Introduccion
En esta práctica veremos como utilizar la imagen docker nginx, como modificar el archivo por defecto el cual abre y como publicar la web utilizando azure.

Conocimientos previos necesarios:
- Saber crear y utilizar imagenes docker
- Saber utilizar maquinas azure
## Descargar imagen

Primero de todo descargaremos la imagen de nginx de la [página oficial de docker](https://hub.docker.com/_/nginx).

![](https://i.imgur.com/VyryX5c.png)

Copiaremos el comando que aparece en la página y lo ejecutaremos en la terminal.

```bash
$ docker pull nginx
```

![](https://i.imgur.com/ir5XJNG.png)

En mi caso, como yo ya lo he descargado previamente, me dice que la imagen está actualizada a la ultima versión.

## Ejecutar la imagen
```bash
$ docker run --rm -d -p 8080:80 --name web nginx
```

Usando el comando anterior, ejecutaremos la imagen con diferentes parametros:
-  `--rm`: Borra automaticamente cuando sale del contenedor
-  `-d`: MODO DEMONIO, el contenedor se ejecuta en segundo plano y solo se muestra su ID
-  `-p`: Especificas el puerto del host
-  `--name`: Asignas un nombre al contenedor
-  Por ultimo indicamos la imagen que queremos ejecutar

![](https://i.imgur.com/fwrNMAB.png)

Una vez ejecutado la instrucción prodremos ir a la dirrecion `localhost:8080` y veremos la página por defecto de Nginx.

![](https://i.imgur.com/dwYq77L.png)

Despues, para cerrar el contenedor utilizaremos el siguiente comando especificando el nombre del contenedor que queremos cerrar.
```bash
$ docker stop web
```

## Ejecutar la imagen cambiando el documento por defecto
 Por defecto nginx busca los archivos html, como el `index.html`, en la carpeta por defecto dentro del contenedor, la cual es `/usr/share/nginx/html`. Para poder cambiarla tendremos que usar el siguiente comando.
```bash
 $ docker run --rm -d -p 8080:80 --name web -v ruta:/usr/share/nginx/html nginx
 ```
 En este comando `ruta` será la nueva carpeta que vamos a crear. En este ejemplo lo crearé en `~/nginx/site-content/` con los siguientes comandos.
 ```bash
 $ mkdir ~/nginx
 $ cd ~/nginx
 $ mkdir site-content
 $ cd site-content
 ```
 ![](https://i.imgur.com/b9eI32Z.png)

Una vez creada la carpeta crearemos un pequeño archivo html para poder hacer el ejemplo. En este caso crearé un archivo llamado `index.html` con la información que aparecerá mas adelante.
```bash
$ touch index.html
$ nano index.html
```
![](https://i.imgur.com/HIXMZeI.png)

Informacion del archivo:
```html
<!DOCTYPE html>
<html lang="en">
  <head>
	<meta charset="utf-8">
    <title>Practica docker Nginx</title>
  </head>
  <body>
    <h2>Welcome To Jurassic Park!</h2>
  </body>
</html>
```
![](https://i.imgur.com/4Fm3k1D.png)

Una vez guardado tendremos que ejecutar el comando que mostré previamente, pero ahora con la ruta bien escrita, en este caso sería:
```bash
 $ docker run --rm -d -p 8080:80 --name web -v ~/nginx/site-content:/usr/share/nginx/html nginx
 ```
![](https://i.imgur.com/Lop3uDN.png)

Y si volvemos a `localhost:8080` veremos el html que hemos escrito.

![](https://i.imgur.com/I3P2Wia.png)

## Crea imagen personalizada
Como hemos visto antes, se puede cambiar el archivo html inicial usando el método anterior, pero otra forma sería crea una imagen personalizada.

Para ello, empezaremos creando un dockerfile, en mi caso lo hare en la carpeta donde estaba la carpeta con el archivo html, esta es mi estructura:
```bash
$ tree 
.
└── site-content
    └── index.html
```
Primero crearemos el archivo `Dockerfile` en el cual podremos las intrucciones para crear la imagen
```bash
$ nano Dockerfile
```
![](https://i.imgur.com/RLGo0RK.png)

Dentro escribiremos la siguiente información:
```dockerfile
FROM nginx:latest
COPY ./site-content/index.html /usr/share/nginx/html/index.html
```
![](https://i.imgur.com/Oz21KQv.png)

Con la primera linea especificamos que utilizamos la imagen de nginx. Con la segunda copiamos nuestro archivo `index.html` en la carpeta por defecto de nginx. Esto lo haciamos antes cuando usabamos el comando docker run dentro del atributo `-v`.

Una vez guardado el archivo crearemos la imagen a partir del dockefile, para ello utilizaremos el siguiente comando:
```bash
$ docker build -t mi_server_nginx .
```
- El atributo `-t` nos permite especificar un nombre de tag/imagen.

Cuando lo ejecutemos aparecera en consola algo parecido.
![](https://i.imgur.com/9xMoTST.png)

Con la imagen ya creada usaremos el comando para ejecutar la imagen de manera similar a como lo haciamos antes.
```bash
$ docker run --rm -d -p 8080:80 --name web mi_server_nginx
```
![](https://i.imgur.com/CknFJ1K.png)

Podemos ver que se ejecuta como antes y cuando entromos a `localhost:8080` deberiamos ver el html que hemos creado.
![](https://i.imgur.com/fs9yp9f.png)

## Acceder a la maquina azure
Para poder publicar una página en azure tendremos que crear una máquina en azure, tendremos que entrar en ella y cear la imagen personalizada, siguiendo los pasos que hemos realizado previamente.
> Importante: Antes de instalar nada hay que actualizar todo con `sudo apt update` y `sudo apt upgrade`

Una vez tengamos la imagen ejecutada en la maquina de azure tendremos que añadir un puerto de entrada a la maquina virtual, para ello seguiremos los siguientes pasos.
1. Entraremos en la maquina desde el portal de azure y nos iremos al menu lateral, alli accederemos a la pestaña de `Networking`. Aqui veremos una lista ya creada de puertos a los que se pueden acceder.

![](https://i.imgur.com/pa12m7f.png)

2. Crearemos un nuevo puerto dando clic al botón azul `Add inbound port rule` y se abrirá una ventana.

![](https://i.imgur.com/ySKi7je.png)

3. Aqui solo modificaremos el puerto destino a 80 ( o 8080) y lo añadiremos dando click al botón azul que pone `Add`.

![](https://i.imgur.com/f06IFWG.png)

4. Para finalizar podemos ver que se ha añadido correctamente el puero elegido en la lista de reglas.

![](https://i.imgur.com/0e9j0Rt.png)

Hecho esto, si accedemos a la ip de nuestra maquina de azure podremos ver que todo funciona correctamente.

![](https://i.imgur.com/i8ohWht.png)