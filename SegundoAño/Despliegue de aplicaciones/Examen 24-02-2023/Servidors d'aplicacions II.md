# Tomcat
Variables de entorno
- CATALINA_BASE. Directorio con la configuración de una instancia de Tomcat.
- CATALINA_HOME. Directorio raíz de la instalación del servidor.
- CATALINA_TMPDIR. Directorio temporal de Apache-Tomcat.
- JRE_HOME. Ruta de los ejecutables de Java.
- CLASSPATH. Rutas de archivos ".jar" necesarios para ejecutar las aplicaciones web del servidor.

Para iniciarlo. 
```bash
cd xx/yy/apache-tomcat-xx.yy.zz/bin
startup.sh
```

Para acceder → `http://localhost:8080`

Para apagar 
```bash
cd xx/yy/apache-tomcat-xx.yy.zz/bin
shutdown.sh
```

Hay tres botones
- Server Status. Información sobre el estado del servidor.
- Manager App. Te permite ver y manipular aplicaciones web existentes.
	- /
	- docs
	- examples
	- host-manager
	- manager (App)
- Host Manager. Te permite ver y manipular los virtual hosts.

Cualquiera de estos botones nos va a pedir usuario y contraseña.
Creamos un usuario con los roles de `manager-gui` y `admin-gui`.

```xml
<user username="cicle" password="cicle" roles"manager-gui, admin-gui" />
```

Dentro del directorio `webapps` se encuentra `ROOT`. Aplicación raíz.

Dos maneras para desplegar nuestra aplicación:
- Desde la página `manager app`. Elegimos el WAR y damos a `Desplegar`.
- Meter el archivo en la carpeta `webapps`.

