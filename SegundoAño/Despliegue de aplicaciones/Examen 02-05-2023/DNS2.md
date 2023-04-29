## Registros
## Faltan
## Registro MX (Mail Exchange)
Permite definir equipos encargados de la entrega de correo en el dominio.
Los consultan agentes de transporte de correo como SMTP.
Un MX puede apuntar a un nombre de otro dominio.
Se pueden definir varios servidores para un mismo dominio.
En el nombre se especifica un número entre 0 y 65535 que determina la preferencia. Menor mejor.
La parte de derecha de un registro MX no debe ser un nombre de tipo CNAME.
## Registro SRV (Service record)
Permite definir equipos que soportan un servidor en particular.
## Registro PTR (Pointer Record)
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