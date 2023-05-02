## Proceso de resolución
### Consultas recursivas
Da una respuesta completa o exacta. Tres posibilidades:
- Respuesta positiva. Da la información que se ha pedido. Se indica si es autorizada o no. No se sabe si quien ha respondido es maestro o esclavo.
- Respuesta negativa. Indica que no se pudo resolver (NXDOMAIN).
- Un error.
### Consultas iterativas (o no recursiva)
Proporciona una respuesta parcial. Cuatro posibilidades:
- Respuesta positiva. Informa por lo que se ha preguntado. Se indica si es autorizada o no.
- Respuesta negativa. Indica que no se pudo resolver (NXDOMAIN).
- Respuesta indicando una referencia a otros servidores a los que se puede preguntar para resolver la pregunta.
- Un error.
## Caché y TTL
### Cache
Si los servidores están preparados, las respuestas se guardan en caché.
Se almacena información:
- Positiva. Recursos resueltos.
- Negativas. Informació que no existe.
### TTL (Time To Live)
Tiempo que guardan las respuestas en caché. Se definen en las zonas.
- Positivo. 1 día o más.
- Negativo. 3 horas
## Resolución inversa
Preguntar por una dirección IP y que devuelva los dominios.
Motivos:
- Resolver problemas de red.
- Detectar spam en los servidores de correo.
- Seguir la traza de un ataque.
- Conocer qué nombres aloja un servidor de hosting.
## Mapeo de direcciones IP y dominio arpa
Las direcciones IP se tratan como nombres donde cada byte es un dominio que cuelga de los dominios "in-addr.arpa" para direcciones IPv4, e "ip6.arpa" para las direcciones IPv6.
## Zonas de resolución inversa
Tienen registros de recursos que asocian nombres de dominio con direcciones IP (al revés). Existen maestras y esclavas.
![[DNS_Directa_Inversa.png]]
- Pregunta por 'obelix.asir.es' → devolverá la IP 193.100.200.101.
- Pregunta la dirección IP 193.100.200.101 → devolverá el nombre 'obelix.asir.es'.
- Pregunta por 'panoramix.asir.es' → devolverá la IP 193.100.200.103.
- Pregunta la dirección IP 193.100.200.103 → devolverá que no ha encontrado nada.
- Pregunta la dirección IP 193.100.200.133 → devolverá el nombre 'panoramix.asir.es'.
## Registros de recursos DNS
Cada fichero de zona organiza esta información en registros de recurso (RR, Resource Records). Se envian en las preguntas y respuestas.
## Formato general
Los RR tienen dos representaciones:
- Textual. Utilizada en los archivos de zona.
- Binario. Se emplea en los mensajes del protocolo
### Registro SOA (Start Of Authority)
Primer registro de una zona. Define una serio de opciones generales.
Datos asociados:
- MNAME.
	- Nombre FQDN del servidor de nombres maestro
- Contacto (contact).
	- Correo de la persona responsable. La arroba se remplaza con un punto.
- Número de serie (serial).
	- Versión del archivo de zona. Se debe incremetar por cada modificación.
	- Los servidores secundarios consultan el registro SOA para realizar transferencias de zona. Si ha cambiado, entonces se realiza la transferencia de zona.
	- Se utiliza el formato de fecha "aaaammdd" y dos digitos mas para los cambios del dia.
- Actualización (refresh).
	- Tiempo de espera para prguntar al maestro si hay cambios de zona. Entre 1200 y 43200 segundos (12 horas).
	- Los valores de "NOTIFY" suelen ser mayor a 1 día.
- Reintentos (retry).
	- Si falla la transferencia, es el tiempo de espera para reintentarlo.
	- Inferior al de actualización.
- Caducidad (expire).
	- Tiempo en el que el esclavo intenta contactar con el maestro para ver si hay cambios.
	- Si expira, el esclavo considera que algo ha pasado y declara no autorizado la zona, por lo tanto no respodera a preguntas sobre la zona.
	- Valores entre 2 y 4 semanas.
- TTL negativo (Time To Live).
	- Tiempo minimo que se almacenan las respuestas negativas sobre esa zona.
	- Diferente al TTL de los RR.
### Registro NS
Permite establecer:
- Servidores de nombres autorizados una zona.
	- Cada zona, mínimo un NS
	- Los servidores pueden tener nombres de la misma zona o de otras.
- Quiénes son los servidores de nombres en los subdominios.
	- Cada zona, mínimo un NS por subdominio.

La parte de derecha de un registro NS no debe ser un nombre de tipo CNAME
### Registro A (Adress)
Establece correspondencia entre un nombre de dominio y una IPv4.
### Registro AAAA (Adress Adress Adress Adress)
Establece correspondencia entre un nombre de dominio y una IPv6.
### Registro CNAME (Canonical Name)
Permite crear alias para nombres de dominio especificados en registros A y AAAA.
Puede apuntar a otro dominio.
Los registro de CNAME no se debe usar en registro MX o NS.
Muchos de estos perjudica el rendimiento.
### Registro MX (Mail Exchange)
Permite definir equipos encargados de la entrega de correo en el dominio.
Los consultan agentes de transporte de correo como SMTP.
Un MX puede apuntar a un nombre de otro dominio.
Se pueden definir varios servidores para un mismo dominio.
En el nombre se especifica un número entre 0 y 65535 que determina la preferencia. Menor mejor.
La parte de derecha de un registro MX no debe ser un nombre de tipo CNAME.
### Registro SRV (Service record)
Permite definir equipos que soportan un servidor en particular.
### Registro PTR (Pointer Record)
Resolución inversa.
Establece una correspondencia entre nombres de direcciones IPv4 e IPv6 y nombres de dominio. 
### Delegación y registros pegamento (Glue record)
Sirve para delegar la resoluición a otro dominio.

- Si el nombre del servidor DNS autorizado del sub dominio (en el que se delega) se encuentra a su vez dentro del propio subdominio.
	- Hay que añadir un registro NS en la zona del padre que define el servidor de nombres autorizado para la zona delegada.
	- Hay que añadir un registro de tipo A para indicar la dirección IP del servidor de nombres autorizado para la zona delegada.
		- A este tipo de registros se les denomina "glue record" porque unen o pegan la zona hija con la zona padre (realmente no pertenecen a la zona padre).
		- Observa que si no se define este registro, el cliente que realiza una pregunta iterativa (por ejemplo pe1.redes.asir.es) y obtiene una referencia al siguiente servidor DNS al que preguntar (ns1.redes.asir.es) no podría obtener la IP del nuevo servidor DNS hasta que no acceda a él (ns1 es un nombre del dominio redes.asir.es). Observa que no puede preguntarle si no sabe su IP (" .. .la pescadilla que se muerde la cola ... ").
	- Si se omiten o se colocan registros de pegamento incorrectos, se dejará parte del espacio de nombres inaccesible.
	- Por lo tanto, los servidores de un dominio padre deben conocer la dirección IP de los servidores de nombres de todos sus subdominios .
- Si el nombre del servidor DNS del subdominio (en el que se delega) no se encuentra en el subdominio.
	- Hay que añadir un registro NS en la zona del padre que define el servidor de nombres autorizado para la zona delegada.
	- No hace falta ni hay que añadir un registro de tipo A para indicar la dirección IP del servidor de nombres autorizado para la zona delegada.
		- En este caso, el cliente que realiza una pregunta iterativa (por ejemplo pe1.sistemas.asir.es) y obtiene una referencia al siguiente servidor DNS al que preguntar (dns.asir.org) podrá resolver el nombre dns.asir.org normalmente.
		- Es un error incluir registros de pegamento para nombres de host que no los necesitan. La regla general es que se deben incluir registros A únicamente para los hosts que están dentro del dominio o cualquiera de sus sub dominios.
## Transferencias de zona
Los servidores DNS esclavos obtienen las zonas de otros servidores. Usan el puerto 53/TCP.
Existen dos tipos.
### Completas (AXFR)
El maestro envía al esclavo todos los datos de la zona.
Es lo que se utilizaba al principio.
### Incrementales (IXFR)
El maestro envía al esclavo solo datos que han cambiado desde la última transferencia.

## Proceso de transferencia de zona
Se inicia de dos maneras:
- El S esclavo pregunta al servidor maestro si hay cambios en los archivos de zona. Lo hace cuando se inicia y periódicamente.
- El maestro nitifica (NOTIFY) al/a los esclavos que hay cambios.

**O el maestro avisa de que hay cambio, o el esclavo, la primera vez que arranca o periódicamente, pregunta si los hay.**
## Protocolo DNS
Normas y reglas que se usan entre los clientes y servidores. TCP, capa de transporte.

![[DNS_Message.png]]
>Formato de un mensaje DNS

**Header**: específica las secciones presentes, el tipo de mensaje y otros campos.
**Question**: campos que definen una consulta.
**Answer**: RRs que responden a la consulta.
**Authority**: RRs que apuntan a los servidores de nombre autoritativos.
**Additional**: RRs que contienen información adicional.

## Vulnerabilidades, amenazas y ataques
1. Servidores DNS
	- Aprovechamiento de vulnerabilidades (uso de exploits).
	- Modificación de los archivos de zona.
	- Ataques de denegación de servicio (DoS).
2. Consultas de clientes DNS a servidores DNS.
	- Suplantado al servidor DNS y enviando información incorrecta.
3. Consultas de servidores DNS a otros a servidores DNS
	-  Suplantado al servidor DNS y enviando información incorrecta.
4. Transferencias de zona
	- Suplantación del servidor maestro.
5. Actualizaciones dinámicas a servidores DNS
	- Suplantación de la fuente externa que envia las actualizaciones.