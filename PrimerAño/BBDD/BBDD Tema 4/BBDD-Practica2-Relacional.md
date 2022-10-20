# De Entidad-Relacion a relacional
##  Primero & Segundo
Escoger una clave principal para cada entidad/relacion/tabla:
- Socio(nombre, ***# dni***, direccion, telefono, cuentaCorriente)
- Embarcacion(nombre, ***# matricula***, materialConstruccion, eslora, calado, manga, añoMatriculacion, tipoEmbarcacion, )
- Motor(tipoMotor, marca, potencia, ***# matricula***)
- Vela(tipoVela, cantidad, ***# matricula***)
- Amarre(***# nombre***, tamaño, geoposición)
- TipoAmarre(***# tipo***, precioAnual, tamañoMaximoEmbarcacion)
- Reserva(fechaInicio, fechaFinal, ***# idReserva***)
- Alquiler(fechaInicio, fechaFinal, ***# idAlquiler***)
- Localizacion(fechaInicio, fechaFinal, ***# idLocalizacion***)

## Tercero
Cada una de las relaciones del modelo relacional se convierte en una tabla/relacion del modelo relacional, con sus atributos mas las claves de las entidades que relaciona.
- R_Socio_Reserva(dni, idReserva)
- R_Socio_Alquiler(dni, idAlquiler)
- R_Embarcacion_Reserva(matricula, idReserva)
- R_Embarcacion_Localizacion(matricula, idLocalizacion)
- R_Amarre_Alquiler(nombre, idAlquiler)
- R_Amarre_Localizacion(nombre, idLocalizacion)
- R_Amarre_TipoAmarre(nombre, tipo)

## Cuarto
Se elige una clave principal para cada una de las nuevas relaciones/tablas.
- Si se tiene una relacion:
	- 0/1 .. 1 -0/1 ..  1 se elige cualquiera
	- 0/1 .. `*` - 0/1 .. 1 se elige la PK del `*`
	- 0//1 .. * - 0/1 .. * se elige como PK de las dos PK juntas

- R_Socio_Reserva(dni, ***# idReserva***)
- R_Socio_Alquiler(dni, ***# idAlquiler***)
- R_Embarcacion_Reserva(matricula, ***# idReserva***)
- R_Embarcacion_Localizacion(matricula, ***# idLocalizacion***)
- R_Amarre_Alquiler(nombre, ***# idAlquiler***)
- R_Amarre_Localizacion(nombre, ***# idLocalizacion***)
- R_Amarre_TipoAmarre(***# nombre***, tipo)

# Quinto
Fusionar, si es posible diferentes tablas del modelo relacional.
- Socio(nombre, ***# dni***, direccion, telefono, cuentaCorriente)
- Embarcacion(nombre, ***# matricula***, materialConstruccion, eslora, calado, manga, añoMatriculacion, tipoEmbarcacion, )
- Motor(tipoMotor, marca, potencia, ***# matricula***)
- Vela(tipoVela, cantidad, ***# matricula***)
- Amarre(***# nombre***, tamaño, geoposición, tipo)
- TipoAmarre(***# tipo***, precioAnual, tamañoMaximoEmbarcacion)
- Reserva(fechaInicio, fechaFinal, ***# idReserva***, dni, matricula)
- Alquiler(fechaInicio, fechaFinal, ***# idAlquiler***, dni, nombre)
- Localizacion(fechaInicio, fechaFinal, ***# idLocalizacion***, matricula, nombre)

![](https://i.imgur.com/nIaOOOI.png)
