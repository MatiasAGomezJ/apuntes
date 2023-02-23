# Servidores de aplicaciones
Actuar como host para la lógica comercial para la lógica comercial del usuario, al tiempo que facilita el acceso y el rendimiento de la aplicación comercial.

Recibir las solicitudes de los clientes, las procesa y envía respuesta.

## Ventajas
- Escalabilidad. Horizontal y vertical, más recursos a un servidor o más servidores.
- Seguridad. Autenticación y autorización.
- Rendimiento. Caché, balanceo de carga y monitoreo en tiempo real.
- Facilidad de uso. Fáciles de usar y configurar. Implementar y administrar aplicaciones de manera más eficiente.
- Integración con otros sistemas.

## Desventajas
- Costo. Escalabilidad y la seguridad.
- Complejidad. Configuración y mantenimiento. Requieren conocimientos técnicos especializados.
- Vulnerabilidades de seguridad. Ataques cibernéticos si no se configuran y mantienen correctamente.
- Dificultad para solucionar errores. Difícil identificar y solucionarlos.
- Limitaciones de rendimiento. Limitados por factores como el hardware subyacente y la capacidad de procesamiento.

# Tomcat
Servidor de aplicaciones. Desplegar y ejecutar aplicaciones Java basadas el estándar JakartaEE. Incluye: Servlets, JSPs,  J WebSocket...

Simplicidad y facilidad de uso. Código abierto.

## Componentes
- Server. Es todo. Representa el contender al completo y dentro de él se ejecuta los demás componentes.
- Service. Intermedio. Dentro de "Server". Posee varias conexiones. Motor, Catalina. Conectores, HTTP y AJP.
- Engine. Procesa las peticiones. Posee múltiples conectores.
- Host. Define los virtual hosts. Puede tener muchas aplicaciones web "context".
- Connector: Encargado de controlar las comunicaciones. Varios. AJP connector o HTTP connector.
- Context. Una aplicación web. Varios por host, pero con una única ruta.
![[Tomcat_Model.png]]

## Directorios
- bin. binarios y scripts de Tomcat.
- conf. Configuración global.
- lib. Todos los archivos ".jar".
- logs. Registros.
- temp. Archivos temporales que necesita tomcat durante la ejecución.
- webapps. Guarda las aplicaciones web.
- work. Directorio para los archivos de uso, cuando se compilan los JSPs, etc.

## Archivos de configuración
- catalina.policy. Política de seguridad de Java. Los servlets o jsp no pueden modificarlo.
- catalina.properties. Archivos ".jar" que no pueden sobrescribirse y otros de uso común.
- context.xml. Indica donde se encuentra el archivo "web.xml" de cada aplicación.
- logging.properties. Politicas generales para el registro de actividad.
- server.xml. Arquitectura de Tomcat.
- tomcat-users.xml. Usuarios, contraseñas y roles. Información de seguridad para las aplicaciones de administración de Tomcat.
- web.xml. Descriptor de despliegue. Directivas de funcionamiento de las aplicaciones. Los descriptores de cada aplicación sobreescribira este.