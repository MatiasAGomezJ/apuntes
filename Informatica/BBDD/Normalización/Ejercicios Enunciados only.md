Suponiendo que están en 1FN!! Normalizra hasta FNBC
# Ejercicio 1
R(A, B, C, D, E, F)
A, B -> E
A -> C, D
C -> F
E -> A

# Ejercicio 2
R(A, B, C, D, E, F)
A ->B, C
C -> D, F
A, F -> D
D -> E

# Ejercicio 3
Profesores(DNIProf, NombreProf, DespachoProf, NombreDesp)

DNIProf | NombreProf | DespachoProf | NombreDesp
:--: | :--: | :--: | :--:
11111A | Pedro Martínez | 2.2.B05 | Despacho naranja

DNIProf -> NombreProf, DespachoProf, NombreDesp
DespachoProf -> NombreDesp

# Ejercicio 4
> Esta en 1FN

Pelicula(Título, Año, Duracion, Tipo, Estudio, Direccion, Actor)
Título, Año -> Duracion, Tipo, Estudio
Estudio -> DireccionEstudio
