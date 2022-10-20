# Docker en Azure
Trabajo creado por [Matias Gomez](https://github.com/MatiasAGomezJ/) & [Andreu Sorell](https://github.com/AndreuSorell/)

### 1. Primero creamos una máquina virtual en Microsoft Azure.

![1](https://user-images.githubusercontent.com/91556405/159377682-1ea37934-954c-43c2-8377-5a62c50f8505.png)

### 2. Luego, rellenamos los datos básicos para nuestra VM.

![2](https://user-images.githubusercontent.com/91556405/159378194-ecb43925-d269-467a-889b-8ee1c51dbcb6.png)
![3](https://user-images.githubusercontent.com/91556405/159378250-889be256-30bc-4c85-8d2e-b203b8b25df4.png)
![4](https://user-images.githubusercontent.com/91556405/159378266-c2ac658f-4a4b-468b-b2f1-37389308f832.png)

### 3. Cuando tenemos los campos rellenados correctamente, hacemos click en 'Revisar y crear'.

![5](https://user-images.githubusercontent.com/91556405/159378493-32378cc3-2df8-4460-8ad0-b3c38b730cf4.png)

### 4. Una vez que comprobamos que se ha validado correctamente, descargamos la clave privada y creamos el recurso.

![6](https://user-images.githubusercontent.com/91556405/159378506-c402ec2b-4f00-41cf-8a85-252d7d8cfa2a.png)

### 5. Como podemos ver en la imagen de abajo, se ha creado correctamente.

![7](https://user-images.githubusercontent.com/91556405/159378512-5cd0a857-39a6-4d9b-a386-73cd6b9f82ac.png)

### 6. Ahora, solo hace falta lanzar el siguiente comando para conectarse a nuestra VM desde la consola.

```bash
$ ssh -i ruta_clave_privada nombre_usuario@ip_maquina
```

![](https://i.imgur.com/d7WOQo3.png)

### 7. Ya dentro de la máquina, actualizaremos e instalaremos los paquetes de la máquina.
```bash
$ sudo apt-get update
```
![](https://i.imgur.com/6eTW0lY.png)

```bash
$ sudo apt-get upgrade
```
![](https://i.imgur.com/UH3MFAF.png)

### 8. Instalamos git.

```bash
$ sudo apt-get install git
```
![](https://i.imgur.com/HduI97T.png)

### 9.  E instalaremos docker.

```bash
$ curl -fsSL https://get.docker.com -o get-docker.sh
$ sh get-docker.sh
```
![](https://i.imgur.com/s87Q9u3.png)

### 10. Una vez descargado, clonaremos el repo que dockerizaremos

```bash
$ git clone ruta_repo
```
![](https://i.imgur.com/4IlN7P1.png)

### 11. Como ya teniamos creado el Dockerfile, podemos construir la imagen directamente.

Codigo del dockerflide:
```dockerfile
FROM maven:3.8.4-openjdk-11-slim AS build

WORKDIR /home/app

COPY src src
COPY pom.xml pom.xml
RUN mvn -f /home/app/pom.xml clean package -q

FROM openjdk:11.0-jre-slim-buster

LABEL "edu.poniperro.gildedrose"="gildedrose"
LABEL version=1.0-SNAPSHOT

COPY --from=build /home/app/target/gildedrose-1.0-SNAPSHOT.jar /usr/local/lib/gildedrose.jar
CMD ["java","-jar","/usr/local/lib/gildedrose.jar"]
```

```bash
$ sudo docker build -t nombre_imagen .
```
![](https://i.imgur.com/LLsdPYM.png)

### 12. Para acabar, ejecutaremos el contenedor

```bash
$ sudo docker run nombre_imagen
```
![](https://i.imgur.com/J3JIhQp.png)

Solo está paco :(