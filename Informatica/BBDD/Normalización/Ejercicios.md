Suponiendo que están en 1FN!! Normalizra hasta FNBC
# Ejercicio 1
R(A, B, C, D, E, F)
A, B -> E
A -> C, D
C -> F
E -> A

**PK**: A, B
## 2FN
R1(A, B, E)
R2(A, C, D, F)
## 3FN
R1(A, B, E)
R2(A, C, D)
R3(C, F)
## FNBC
R1(A, B)
R2(A, C, D)
R3(C, F)
R4(E, A)

# Ejercicio 2
R(A, B, C, D, E, F)
A ->B, C
C -> D, F
A, F -> D
D -> E

**PK**: A


## 2FN
R1(A, B, C)
R2(C, D, F)
R3(D, E)
## 3FN
# Ejercicio 3
Profesores(DNIProf, NombreProf, DespachoProf, NombreDesp)

DNIProf | NombreProf | DespachoProf | NombreDesp
:--: | :--: | :--: | :--:
11111A | Pedro Martínez | 2.2.B05 | Despacho naranja

DNIProf -> NombreProf, DespachoProf, NombreDesp
DespachoProf -> NombreDesp

## 1FN & 2FN
Profesores(DNIProf, NombreProf, ApellidoProf, DespachoProf, NombreDesp)

## 3FN & FNBC
Profesores(DNIProf, NombreProf, ApellidoProf, DespachoProf)
Despachos(DespachoProf, NombreDesp)

![](https://i.imgur.com/F80GWmO.jpg)

# Ejercicio 4
> Esta en 1FN

Pelicula(Título, Año, Duracion, Tipo, Estudio, Direccion, Actor)
Título, Año -> Duracion, Tipo, Estudio
Estudio -> DireccionEstudio

## 2FN
A_P(**Título, Año, Actor**)
Pelicula(**Título, Año**, Duracion, Tipo, Estudio, Direccion)

![](https://i.imgur.com/QR2xLEK.jpg)
## 3FN & FNBC
A_P(**Título, Año, Actor**)
Pelicula(**Título, Año**, Duracion, Tipo, Estudio, Direccion)
Estudio(**Estudio**, Direccion)

![](https://i.imgur.com/oE1BipK.jpg)
