# Seguridad en docker
## Parte A. Seguridad host
Como comparte el mismo kernel de la máquina host, todo el software del sistema debe estar actualizado a la máxima versión estable.

Antes de aplicar seguridad en el host, se debería usar alguna tipo de seguridad en el host mediante `ip_tables`, `SELinux`, `apparmor`, defensa en profundidad, perímetro etc.

Algo también muy importante es controlar los permisos de usuarios. Sólo deben acceder a docker aquellos usuarios con permiso de root, ya que docker debe acceder al kernel. Lo aconsejable es crear un grupo de docker e ir añadiendo ahí los usuarios que puedan lanzar contenedores.

```bash
sudo usermod -aG docker $USER
```

![](https://i.imgur.com/WoEgjqM.png)

y recargar los permisos (o reiniciar sesión)

```bash
newgrp docker
```

![](https://i.imgur.com/51ghkWD.png)

## PARTE B. Seguridad en el demonio
El demonio corre como superusuario, así que debemos impedir que los usuarios puedan tocar la configuración y el socket no deberían poder verlo.

El archivo es `/etc/docker/daemon.json` (si no existe, se debe crear para introducir las siguientes configuraciones)

Para modificar el archivo:
```bash
sudo nano /etc/docker/daemon.json
```

![](https://i.imgur.com/S2T6X2X.png)

Poner `debug: false` y es muy interesante configurar `ulimits` que permiten definir los archivos que pueden cargar los contenedores y es interesante dejar unos límites por defecto.

También es interesante `icc` que impide que haya conectividad entre los contenedores ya que todos están en la misma red por defecto de tal manera que no se verán entre sí y sólo aquellos que estén linkados explícitamente en su configuración. Por ejemplo wordpress y mysql

Ejemplo de archivo `daemon.json`

```json
{
    "debug": false,
	"icc": false
}
```

![](https://i.imgur.com/rQ7K5J7.png)

Otro archivo es `key.json` y ningún usuario que no sea root no debería acceder porque ahí se almacena en base64 la key para conectarse por TLS (por ejemplo con el Registry).

## PARTE C. Seguridad en contenedores
Son uno de los ejes principales del hardening pues donde hay más configuraciones afectadas.

Por ejemplo asignando un `ulimit` al contenedor:

```bash
docker run --ulimit nofile=512:512 --rm debian sh -c "unlimit -n"
```

![](https://i.imgur.com/DVXMK1A.png)

Si se retira el flag de ulimits, daría los de por defecto. Se puede modificar el archivo de configuración para fijar unos límites pequeños y luego modificarlo en tiempo de ejecución.

El comando sin la flag `ulimits`:

![](https://i.imgur.com/1S3i2ip.png)

También se pueden meter límites para otro tipo de recursos. Por ejemplo para limitar el alcance de una ataque un DDoS en el que nuestro contenedor puede quedarse sin recursos y esto afectaría al resto de contenedores (incluso a la máquina host) pues se quedarían sin recursors

Por ejemplo:

```bash
docker run -it --cpus=".5" ubuntu /bin/bash
```

![](https://i.imgur.com/mx6ta2H.png)

De esta forma nunca gastaría más de 0.5 CPUs

Otra configuración interesante es reiniciar en el fallo:

en el comando `--restart=on-failure`

![](https://i.imgur.com/cDgIAVF.png)

### Privilegios

Por defecto el usuario es `root`

Se puede cambiar el usuario por defecto al correr la  imagen y podemos forzar a ello con el flag `-u uuid`

Por ejemplo, si corremos el siguiente comando con el usurio 4400 

```bash
docker run -u 4400 alpine ls /root
```

Nos devolverá que no tengo accesos

```bash
ls: can't open '/root': Permission denied
```

![](https://i.imgur.com/dvDesel.png)

Otro flag relacionado con permisos es `--privileged`:

```bash
docker run -it --privileged ubuntu
```

```bash
mount -t tmpfs none /mnt
```

Luego correr:

```bash
df -h
```

![](https://i.imgur.com/nd8ws2e.png)

Y nos muestra que ha sido capaz de montarlo, pero si no le añadimos privilegios devuelve:

```bash
mount: /mnt: permission denied.
```

![](https://i.imgur.com/XZCxcKl.png)

El que sí tiene privilegios hereda todas las [capabilities](https://www.incibe-cert.es/blog/linux-capabilities) de linux.

Otra cosa es montar el socket de docker en un contenedor. Por ejemplo, levantar un docker dentro de docker. Esto se ve mucho en CD/CI.

Por ejemplo:

```bash
docker  run -v /var/run/docker.sock:/var/run/docker.sock -it docker
```

![](https://i.imgur.com/KHCjCvB.png)

Cuando se lanza tengo un docker dentro de docker es la misma ejecución de docker porque comparten el socket. Si lanzo dentro un contenedor ubuntu, también lo podré listar si hago docker ps en el host

## Seguridad en imágenes

Es más fiable confiar en una imagen de la que tengo acceso al `Dockerfile` que una que ya viene construida. Puede tener malware si la imagen no es confiable.

Con docker commit se crea una imagen, aunque su uso es desaconsejable. ya que no se puede auditar. Sólo confiar en las imágenes de Docker, o de fuente confiable como Google Cloud o Microsoft Azure.

Por ejemplo, si buscamos un imagen de Wodpress encontraremos unas 8000 imágenes. La más popular es la imagen oficial que es la generada por Docker. En el caso de que la haya generado otro desarrollador estará indicado en la imagen. Por ejemplo `Multicontainer WordPress` de **Microsoft**

Se puede hacer una imagen a partir de un repositorio en GitHub como por ejemplo, esta [imagen](https://hub.docker.com/r/irespaldiza/whoami) alojada en https://github.com/irespaldiza/whoami por lo que se puede clonar o crearlo tú a partir del Dockerfile.

El servicio que lo soporta es Notary que es una de las aplicaciones a las que da soporte Docker.

Esta variable de entorno es muy aconsejable tenerla a true. Por ejemplo se puede incluir en el `bash.rc`.

A partir de una imagen es parecido a compilar a partir de la definición para generar las capas y guardarla en un registry como `docker.hub`

La imagen de alpine sólo pesa  5.61 MB porque comparte el kernel con el host.

Los comandos se ejecutan en tiempo de compilación en la preparación del entorno y ENTRYPOINT y CMD en tiempo de ejecución.

Lo normal es poner en ENTRYPOINT un comando y en CMD los parámetros (que se pueden sobrescribir)

También existe el comando ADD que es muy parecido a COPY. La diferencia es que COPY sólo permite copiar desde el equipo y ADD desde una url.

Y otra diferencia es que ADD puede copiar y descomprimir archivos, pero la capa no se podrá cachear.

Es una mala praxis no usar la versión al utilizar un paquete. Por ejemplo, `alpine`

para buscar imágenes se usa `docker search alpine`, pero no nos muestra tag

De esta forma, se puede comprobar si tiene vulnerabilidades o si dentro de un tiempo la vuelvo a generar puede dar problemas de compatibilidad.

Es  bastante normal que el código deba estar compilado lo que añade más superficie a ser atacada porque no interesa tener un compilador en la imagen ya que si nuestro contenedor es atacado el atacante podría compilar programas en nuestro sistema, cosa que está totalmente prohibida.

Por ejemplo

```dockerfile
FROM golang:alpine AS builder
ENV GO111MODULE=auto
COPY whoami.go /app/
WORKDIR /app
RUN go build -o whoami

FROM alpine
WORKDIR /app
COPY --from=builder /app/whoami /app/
ENTRYPOINT ./whoami
```

![](https://i.imgur.com/LMRCjX1.png)

El concepto `pot` es de **Kubernetes** que son un grupo de contenedores que comparten en el mismo espacio de puertos