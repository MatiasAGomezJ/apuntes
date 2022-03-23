# De Entidad-Relacion a relacional
## Primero
Escoger una clave principal para cada entidad/relacion/tabla:
- Compañia(#nomCom)
- Vuelo(#numVuelo, fecha, hora, capacitat)
- Aeropuerto(nombreAeropuerto,#idAeropuerto)
- Reserva(fecha, plazas,#idReserva)
- Pasajero(nombre,#DNI)
- Ciudad(nombreCiudad,#idCiudad)
- Pais(#nomPais)
> El ***#*** representa un atributo único

## Segundo
Cada una de las entidades del modelo relacional se convierte en una tabla/relacion del modelo relacional
## Tercero
Cada una de las relaciones del modelo relacional se convierte en una tabla/relacion del modelo relacional, con sus atributos mas las claves de las entidades que relaciona.

- R_Compañia_Pais(nombreCompañia, nombrePais)
- R_Compañia_Vuelo(nombreCompañia, numVuelo)
- R_Vuelo_Pasajero(numVuelo, DNI)
- R_Vuelo_Aeropuerto_Origen(numVuelo, idAeropuerto)
- R_Vuelo_Destino(numVuelo, idAeropuerto)
- R_Aeropuerto_Ciudad(idAeropuerto, idCiudad)
- R_Ciudad_Pais(idCiudad, nombrePais)

## Cuarto
Se elige una clave principal para cada una de las nuevas relaciones/tablas.
- Si se tiene una relacion:
	- 0/1 .. 1 -0/1 ..  1 se elige cualquiera
	- 0/1 .. `*` - 0/1 .. 1 se elige la PK del `*`
	- 0/1 .. `*` - 0/1 .. `*` se elige como PK de las dos PK juntas

>  ***PK***: Primary Key
> Donde hay asterisco hay PK

- R_Compañia_Pais(#nombreCompañia, nombrePais)
- R_Compañia_Vuelo(nombreCompañia,#numVuelo)
- R_Vuelo_Pasajero(#nombreVuelo,#DNI)
- R_Vuelo_Aeropuerto_Origen(#numVuelo, idAeropuerto)
- R_Vuelo_Aeropuerto_Destino(#numVuelo, idAeropuerto)
- R_Aeropuerto_Ciudad(#idAeropuerto, idCiudad)
- R_Ciudad_Pais(#idCiudad, nombrePais)

# Quinto
Fusionar, si es posible diferentes tablas del modelo relacional.
- Compañia(#nombreCompañia, nombrePais)
- Vuelo(#numVuelo, fecha, hora, capacitat, nombreCompañia,  idAeropuertoOrigen, idAeropuertoDestino)
- Aeropuerto(nombreAeropuerto,#idAeropuerto, idCiudad)
- Reserva(fecha, plazas,#idReserva, numVuelo, DNI)
- Pasajero(nombre,#DNI)
- Ciudad(nombreCiudad,#idCiudad, nombrePais)
- Pais(#nombrePais)

![](https://i.imgur.com/XasbK5U.png)
