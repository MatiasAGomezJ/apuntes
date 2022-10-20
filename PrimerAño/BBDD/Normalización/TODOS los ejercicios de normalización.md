# Ejercicios de los apuntes
> Tanto del primer PDF como del segundo
## Ejercicio 1.1
Suministros(CodiProv, CodiArticulo, Cantidad, CiudaProv)
- **CodiProv** -> CiudadProv
- **CodiProv, CodiArticulo** -> Cantidad, CiudadProv
- 
## Ejercicio 1.2
Clientes(CodiProv, Calle, Numero, Ciudad, Provicincia)
- **CodiProv** -> Calle, Numero, Ciudad, Provincia
- **Ciudad** -> Provincia

## Ejercicio 1.3
Notas(DNIALumno, CodiAsignatura, CodiMatricula, Nota)
- **DNIAlumno** -> CodiMatricula
- **CodiMatricula** -> DNIAlumno
- **DNIAlumno, CodigoAsignatura** -> CodiMatricula, Nota
- **CodiAsignatura, CodiMatricula** -> DNIAlumno, Nota

## Ejercicio 2.1
Empleado(Empleado, Habilidad, Lugar_trabajo)
- **Empleado, Habilidad** -> Lugar_trabajo
- **Empleado** -> Lugar_trabajo

## Ejercicio 2.2
Emp(DNI, NumProyecto, Horas, NombreE, NombreProyecto, UbicaciónProyecto)
- **DNI, NumProyecto** -> Horas
- **DNI** -> NombreE
- **NumProyecto** -> NombreProyecto, UbicaciónProyecto

## Ejercicio 2.3
Emp(NombreE, DNI, FechaNac, Dirección, NúmeroDpto, NombreDpto, DNIDirector)
- **DNI** -> NombreE, FechaNac, Dirección, NúmeroDpto
- **NúmeroDpto** -> NombreDpto, DNIDirector

## Ejercicio 2.4
> **IMPORTANTE!!!!**
> Este lo hemos visto en clase, pero utlizando letras.

Parcelas(idPropiedad, NombreMunicipio, NúmeroParcela, Área, Precio, Impuestos)
- **idPropiedad** -> NombreMunicipio, NúmeroParcela, Área, Precio, Impuestos
- **NombreMunicipio, NúmeroParcela** -> idPropiedad Área, Precio, Impuestos
- **NombreMunicipio** -> Impuestos
- **Área** -> Precio

## Ejercico 2.5
R(Nombre, Teléfono, Afición, Dirección)
- **Nombre, Teléfono, Afición** -> Dirección
- **Dirección** -> Teléfono

## Ejercicio 2.6
Parcelas(idPropiedad, NombreMunicipio, NúmeroParcela, Área)
- **idPropiedad** -> NombreMunicipio, NúmeroParcela, Área
- **NombreMunicipio, NúmeroParcela** -> idPropiedad Área
- **Área** -> NombreMunicipio

# Ejercicios de fuera de los apuntes

## Ejercicio 1
R(A, B, C, D, E, F)
- **A, B** -> E
- **A** -> C, D
- **C** -> F
- **E** -> A

## Ejercicio 2
R(A, B, C, D, E, F)
- **A** ->B, C
- **C** -> D, F
- **A, F** -> D
- **D** -> E

## Ejercicio 3
Profesores(DNIProf, NombreProf, DespachoProf, NombreDesp)

DNIProf | NombreProf | DespachoProf | NombreDesp
:--: | :--: | :--: | :--:
11111A | Pedro Martínez | 2.2.B05 | Despacho naranja

- **DNIProf** -> NombreProf, DespachoProf, NombreDesp
- **DespachoProf** -> NombreDesp

## Ejercicio 4
Pelicula(Título, Año, Duracion, Tipo, Estudio, Direccion, Actor)
- **Título, Año** -> Duracion, Tipo, Estudio
- **Estudio** -> DireccionEstudio

## Ejercicio 5
R(A, B, C, D, E, F)
- **A, B** -> E
- **B** -> C
- **C** -> D

## Ejercicio 6
R(A, B, C, D, E, F)
- **A** -> C
- **B** -> D

## Ejercicio 7
R(A, B, C, D, E, F)
- **A** -> B, C, D
- **B, C** -> A, D
- **D** -> B

## Ejercicio 8
> Mu complicado. No hacer.

R(Colegio, Profesor, Habilidad, Aula, Curso, Libro, Editorial, FechaPrestamo)
- **Profesor** -> Colegio
- **Profesor** -> Aula
- **Habilidad** -> Curso
- **Aula** -> Curso
- **Libro** -> Editorial
- **Profesor, Editorial, FechaPrestamo** -> Libro
- **Profesor, Habilidad, Libro** -> FechaPrestamo

## Ejercicio 9
> Hay tres soluciones. Se escoge la mas eficiente.

R(A, B, C)
- **A, B** -> C
- **C** -> B

## Ejercicio 10
R(A, B, C, D, E, F, G, H)
- **A, B** -> C, D, E, F, G, H
- **C, D** -> A, B, E, F, G, H
- **A** -> F
- **C** -> B
- **D** -> E
- **G** -> H