# Introducción

FTP: File Transfer Protocol → Protocolo de Transferencia de Archivos
Conectado por una red TCP, cliente-servidor
Capa de aplicación del modelo TCP/IP
Utiliza normalmente el puerto 20 y 21.
+velocidad -seguridad. No hay cifrado → texto plano.

# Historia

Empezó en abril 1971 (RFC 114), antes de que existiera la pila TCP/IP.
La estructura general en 1973. Tuvo modificaciones (+ comandos y funcionalidades).
Octubre de 1985 (RFC 959), que es la que se utiliza actualmente.

# Modelo FTP

Él [[PI]] de **usuario** inicia la **conexión de control** en el puerto 21. Las **órdenes FTP** las genera el PI de usuario hacia al proceso servidor a través de la conexión de control.

**Respuestas estándar**. Se envían desde la PI del servidor a la del usuario por la conexión de control como respuesta.

**Órdenes FTP**. Parámetros para la conexión de datos (puerto, modo de transferencia, estructura) y naturaleza de la operación sobre el sistema de archivos (almacenar, recuperar, borrar).

**Proceso de transferencia de datos (DTP)** (de usuario). Espera a que el servidor inicio la conexión al puerto especificado y transfiere datos en función de los parámetros especificados.

![[FTP_Model.png]]

La comunicación:
- Es independiente del sistema de archivos.
- Bidireccional. Enviar y recibir.

# Servidor FTP
Programa. El equipo deberá estar conectado a una red.

# Cliente FTP
Programa. Utiliza el protocolo FTP para conectarse al servidor.

# Cliente FTP en el navegador

```ftp
ftp://<usuario>:<contraseña>@<servidor ftp>/<urlruta>
ftp://admin:password@ftp.nombre.com/public
```

# Tipos de usuarios
## Anónimo
Usuario: anonymous. Contraseña: (normalmente es el correo electronico).
Nada más.
## Normal 
Usuario y contraseña válido.

# Ejemplos de Servidores y Clientes FTP

- Servidores. FileZilla server, vsftpd, ProFTPD
- Clientes. cURL, FileZilla, Cyberduck.

# Modos de conexión del cliente FTP
En los dos el cliente establece conexión mediante el puerto 21, que establece el canal de control. 

Antes de cada transferencia se reenviará el modo de conexión, y se volverá a conectar al puerto correcto. Activo → 20. Pasivo → Aleatorio.

## Activo, Estándar o PORT
- Siempre crea el canal de datos en su puerto 20
- En el cliente el canal de datos es puerto aleatorio mayor que el 1024.
El cliente manda un comando PORT al servidor por el canal de control indicándole el número de puerto del cliente que se utilizará para transferir la información.
Vulnerabilidad. Cliente debe abrir el puerto que se utilizará.

## Pasivo
Cuando el cliente envía un comando PASV, el servidor indica el puerto de datos del servidor. El cliente desde un puerto elegido se conectará al indicado del servidor para transferir datos. El puerto 20 del servidor no se usa.

# Tipos de transferencia de archivos en FTP
- ASCII. Caracteres imprimibles. Por ejemplo, HTML, pero no imágenes.
- Binario. Archivos comprimidos, ejecutables, imágenes, audio…

# Comandos de FTP
Recomendaciones del protocolo Telnet.
- Cadenas de caracteres Telnet. Final de línea. `<CR>+<LF>`.
- **Retorno de carro** seguido del carácter **Avance de línea** indicado como `<CRLF>`
- Espacio `<SP>`.

Existen tres tipos de comandos FTP diferentes:
- Comandos de control de acceso.
- Comandos de parámetros de transferencia.
- Comandos de servicio FTP.

## C. de control de acceso
| Comando | Descripción                                                                                                                                   |
| ------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| USER    | Identifica al usuario.                                                                                                                        |
| PASS    | Especifica la contraseña. Debe ser inmediatamante precedida por el comando USER. Se tiene que indicar si se quiere esconder la visualización. |
| ACCT    | Especifica la cuenta de usuario. 230 -> no. 322 -> si.                                                                                        |
| CWD     | cd "dir"                                                                                                                                      |
| CDUP    | cd ..                                                                                                                                         |
| SMNT    | Montar estructura                                                                                                                             |
| REIN    | Reinicia                                                                                                                                      |
| QUIT    | Abandona la sesión. Espera a acabar las transferencias.                                                                                       |

## C. de parámetros de transferencia
| Comando | Descripción                                                                                                        |
| ------- | ------------------------------------------------------------------------------------------------------------------ |
| PORT    | Especifica puerto.                                                                                                 |
| PASV    | Indica al servidor DTP que espere a una conexión en un puerto aleatorio. La respuesta es la dirección IP y puerto. |
| TYPE    | Indica el formato de transferencia.                                                                                |
| STRU    | Carácter Telnet. Especifica la estructura de archivos. F, R, P.                                                                             |
| MODE    | Carácter Telnet. Especifica método de transferencia. S, B, C.                                                                                                                   |

## C. de servicio FTP
| Comando | Descripción                                                                             |
| ------- | --------------------------------------------------------------------------------------- |
| RETR    | Descargar un archivo.                                                                   |
| STOR    | Subir un archivo                                                                        |
| STOU    | Subir un archivo. Pero con nombre único. El nombre vuelve en la respuesta.              |
| APPE    | Añade información al archivo especificado. Si no existe, lo crea.                       |
| ALLO    | Pide al servidor que reserve el espacio necesario para un archivo.                      |
| REST    | Reiniciar una transferencia desde donde se detuvo.                                      |
| RNFR    | Indica el archivo a renombrar. Seguido de RNTO.                                         |
| RNTO    | Indica el nuevo nombre del archivo. Justo después de RNFR                               |
| ABOR    | Abandona todas las transferencias del comando anterior. Si no hay, no hace nada.        |
| DELE    | Borrar un archivo.                                                                      |
| RMD     | Borrar un directorio.                                                                   |
| MKD     | Crear un directorio.                                                                    |
| PWD     | Mostrar el nombre del directorio actual.                                                |
| LIST    | Listar contenido de directorio actual o cualquier otro.                                 |
| NLST    | Listar contenido de directorio actual                                                   |
| SITE    | Proporciona servicios específicos no definidos en el protocolo FTP.                     |
| SYST    | Enviar información del servidor.                                                        |
| STAT    | Transnmite información del servidor. Ej: estado de una transferencia                    |
| HELP    | Muestras todos los posibles comandos.                                                   |
| NOOP    | Devuelve un OK del servidor. Sirve para no desconectarse tras un periodo de inactividad |

# Códigos de respuesta de FTP
Tres digitos
- Primero. Exito (2yz), fracaso (4yz o 5yz) o no hay respuesta (1yz o 3yz).
- Segundo. Clase de error.
	- 0z - Sintaxis. Estas respuestas se refieren a errores de sintaxis.
	- x1z - Información. Las respuestas a las solicitudes de información.
	- x2z - Conexiones. Respuestas en referencia al control y las conexiones de datos.
	- x3z - Autenticación y contabilidad. Respuestas para el proceso de inicio de sesión y los procedimientos contables.
	- x4z - No definido.
	- x5z - Sistema de archivos. Estas respuestas transmiten códigos de estado del sistema de archivos del servidor.

Falta acabar
