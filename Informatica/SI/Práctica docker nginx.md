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

Para ello, empezaremos creando un dockerfile, en mi caso lo hare en la carpeta donde estaba el archivo html.