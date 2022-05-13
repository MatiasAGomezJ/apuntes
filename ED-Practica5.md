# Practica 5: Test en java  
## Introducción  
En este trabajo veremos como crear un repositorio en GitHub, un proyecto en IntelliJ de Java con Maven y veremos como crear una simple interfaz, la cual documentamos con javadoc, además de una clase que implemente dicha interfaz con sus tests para comprobar que funcione correctamente.  
## Creación del repo y proyecto  
Antes de empezar a escribir código crearemos el repositorio con nombre "Practica5" a través de GitHub.  
  
![](https://i.imgur.com/k3dVWdC.png)  
  
![](https://i.imgur.com/dF6rFUN.png)  
  
> Esta página la dejaremos abierta para copiar la URL del repo.  
  
Después crearemos un nuevo proyecto de Java con IntelliJ, en este caso hemos realizado el proyecto con Maven.  
  
![](https://i.imgur.com/YnNbPZc.png)  
  
> Imagen 1  
>  
> Se puede observar la configuración que tendrá el proyecto.  
> El nombre del proyecto será `Pracita5`, se utilizará `Java 17` y la arquitectura de Maven `quickstart`. Además, hemos cambiado el GroupId a `edu.poniperro` y establecido que la versión de la que partirá el proyecto será la `0.0.0`.  
  
Una vez configurado con lo descrito le daremos a `Create`. Una ventana del IDE se abrirá con la carpeta del proyecto y todos los archivos que permiten tener una aplicación funcional de Java con Maven.  
  
![](https://i.imgur.com/Fhfh9W0.png)  
  
> Imagen 2  
>  
> Estructura principal del proyecto, donde se puede ver:  
> - La carpeta `.idea`, donde se encuentra la configuración del IDE.  
> - La carpeta `src`, en la cual dentro están las carpetas de `main` y `test`.  
> - El archivo `pom.xml`, donde está toda la configuración de Maven.  
  
Ahora entraremos en la terminal, la cual estará ubicada en la raíz del proyecto, para poder usar el control de versiones. Para ello utilizaremos el comando:  
```bash  
$ git init
```  
  
![](https://i.imgur.com/N2whKBN.png)  
  
> Imagen 3  
>  
> Ejecución del comando descrito.  
  
A continuación añadiremos el repositorio que hemos creado correctamente, copiaremos la URL HTTP o SSH, dependiendo de nuestra preferencia, y utilizaremos el siguiente comando:  
```bash  
$ git remote add origin git@github.com:MatiasAGomezJ/Practica5.git
```  
![](https://i.imgur.com/Ex7lsTP.png)  
> Imagen 4  
>  
> Ejecución del comando descrito. Un poco modificado debido a mi configuración.  
  
Para comprobar el comando ha funcionado correctamente utilizaremos el siguiente comando que nos mostrará el repositorio remoto al que está apuntando:  
```bash  
$ git remote -v
```  
![](https://i.imgur.com/LQJNhgM.png)  
  
Para acabar subiremos todos los archivos al repo, aunque antes moveremos el archivo `.gitignore` a la raíz del proyecto. Además, añadiremos una nueva línea en la que excluiremos la carpeta `target` e `.idea`.  
  
![](https://i.imgur.com/hhLPIcm.png)  
> Imagen 5  
>  
> Muestra los archivos `README.md` y `.gitignore` en la raíz del proyecto junto a la información que hay dentro del segundo.  
  
Con esto ya hecho podemos subir los archivos al repositorio con los siguientes comandos.  
  
```bash  
$ git add .$ git commit -m "Commit inicial"$ git push -u origin master
```  
  
![](https://i.imgur.com/DXPSiPo.png)
  
> Imagen 6  
>  
> Ejecutando los comandos.

Hemos creado una nueva rama llamada `develop` en la cual será donde realizaremos los nuevos cambios. Esta rama se creará a partir del estado de la rama `master`. Nos moveremos en ella y la subiremos al repositorio.
```bash
$ git branch develop
$ git checkout develop
$ git push -u origin develop
```

![](https://i.imgur.com/hvvuHx9.png)

> Imagen 7
> 
> Ejecucion de los comandos.

![](https://i.imgur.com/2Sj6Ho9.png)

> Imagen 8
> 
> Screenshot del repo mostrando las ramas que existen.

## Crear la interfaz ICalculadora
Empezaremos creando el arhivo, lo tendremos crear dentro de la carpeta `src/main/java/edu/poniperro`, aunque las ultimas dos carpetas no tienen que tener el mismo nombre. Allí crearemos un arhivo llamado `ICalculadora.java` o en el caso de IntelliJ simplemente `ICalculadora`.

![](https://i.imgur.com/6xW7aac.png)

Dentro tendremos, además de indicar que es una interfaz, vamos a declarar los métodos: `sumar`, `restar`, `multiplicar`, `dividir`. Todos ellos requerirán de dos parametros de tipo `double` y devolveran el mismo tipo.

~~Codigo:~~

~~Foto del codigo 9~~

> Imagen 9
>
> Screenshot del código de la interfaz.
