### Domain Name System
Sistemas de nombres utilizados por servicios de resolución de nombres que permiten asociar nombres sencillos con direcciones numéricas. 

Los sistemas de nombres, no solo los usados en redes, se pueden clasificar en:
- Planos:
	- Ningún tipo de agrupamiento.
	- No existe una jerarquía.
	- Ejemplos: DNIs, nombres de ciudades, nombres de calles, nombres NetBIOS de Windows, etc.
- Jerárquicos:
	- Nombres agrupados y clasificados.
	- Facilitan la administración y gestión distribuida.
	- Ejemplos: número de teléfono, nombres usados en los sistemas de ficheros, etc.

DNS es jerárquico.

DNS se basa en los siguientes componentes:
- **Espacio de nombres de dominio (domain name space).** Nombres que sirven para identificar máquinas o servicios en una red.
- **Base de datos DNS.** 
- **Servidores de nombres (o servidores DNS) (name servers).** Base de datos de DNS, zonas.
- **Clientes DNS (resolvers).** Realizan preguntas al servidor y dan respuesta al usuario/ aplicaciones.
- **Protocolo DNS.** Normas y reglas entre cliente-servidor.

DNS se basa en el modelo cliente-servidor.
- Los servidores pueden preguntarse entre sí.
- Pueden intercambiar información sobre sus zonas (**transferencias de zona**).

## Espacio de nombres de dominio
Nombres de dominio puede estar formado caracteres separados por puntos. Case insensitive.
- Máximo 127 niveles. Cada uno, como máximo, 63 caracteres. En total no puede superar los 255.

## Dominio raíz. Dominios y subdominios.
Raíz ->"." (root). Nombre nulo con 0 caracteres.
Los subdominios que cuelgan de la raíz son los **dominios de primer nivel o TLD, Top Level Domains.** A partir de ahí: segundo nivel, tercer nivel

## Nombres relativos y absolutos. FQDN
- Nombres relativos: Es necesario saber el dominio superior
- Nombres absolutos: FQDN, Fully Qualified Domain Names. Punto al final ".".

## Administración de nombres de dominio en Internet. Delegación
ICANN (Internet Corporation for Assigned Names and Numbers).
InterNIC es la organización asociada a la ICANN que permite registrar dominios TLD.

## Dominios TLD y los operadores de registro (registry)
ICCAN clasifica los dominios de nivel superior (TLD):
- Genéricos. Nombre significativo en función del propósito u organización.
	- Dominios patrocinados
	- Entidad que soporta su patrocinio
	- Dominios no patrocinados
- Geográficos (ccTLDs, country code TLDs).
	- Dos letras que identifica un país.
	- Nombre definido por país destinado a tarea de gestión y políticas.
- arpa
	- infraestructura técnica de Internet bajo la dirección de la IAB (Internet Architecture Board).
	- Se utiliza para la resolución inversa de IPs.
- Dominios reservados.
	- Nombres para pruebas privadas reservados para que no entren en conflicto.
	- "test", "example", "invalid" y "localhost".


## Delegación
ICCAN se encarga de la raíz.
Red.es se encarga de resolver dentro de "es.".
Res.es es un **operador de registro**.

## Registro de dominios. Agentes registradores (registrar)
Reservar un nombre durante un tiempo. Un año.
Los registradores registran nombres de segundo nivel.