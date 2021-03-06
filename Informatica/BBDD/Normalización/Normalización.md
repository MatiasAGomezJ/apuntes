# Normalización
- Garantizar buen diseño de las BBDD relacionales -> manipular la estructura de datos para cumplir con unos requisitos establecidos para la normalización.
- Pueden producirse anomalías y difilcutar el mantenimiento al haber un alto grado de redundancia en las relaciones.
	- Para evitarlo => Normalizacion
## Primera Forma Normal ( 1FN )
Una relación está en 1FN, si y solo si, ningún atributo de la relación es sí mismo una relación, es decir, si todo atributo de la relación es **atómico**.

Mal, no atomico el numero del enfermero:

Habitación | Paciente | Enfermero
:--: | :--: | :--:
111 | Juan | 2,3
222 | Miguel | 5
333 | Pere | 4,6 

Bien:

Habitación | Paciente | Enfermero
:--: | :--: | :--:
111 | Juan | 2
111 | Juan | 3
222 | Miguel | 5
333 | Pere | 4 
333 | Pere | 6 

## Segunda Forma Normal ( 2FN )
Una relación está en 2FN, si y solo si, está en 1FN y todo atributo no clave **depende** funcionalmente **en forma completa de la PK**.

Excepción: un atributo puede **depender** funcionalmente de **parte de la PK** si este atributo es parte de una clave alternativa. 

> Dependencia no completa: depende de una de las deos atributos de la pk

Suministros(**CodiProv, CodiArticulo**, Cantidad, CiudaProv)

CodiProv -> CiudadProv

CodiProvm, CodiArticulo -> Cantidad, CiudadProv
## Tercera Forma Normal ( 3FN )
Una relación está en 3FN, si y solo si, está en 2FN y ningún atributo no clave depende funcionalmente de otro conjunto  de ( o un ) atributos no clave.

La excepcción aplicada en la 2FN también se propaga a la 3FN.

Clientes(**CodiProv**, Calle, Numero, Ciudad, Provicincia)

CodiProv -> Calle, Numero, Ciudad, Provincia

Ciudad -> Provincia

## Forma Normal Boyce-Codd ( FNBC )
Una relación está en FNBC, si y solo si, está en 3FN y si todos los determinantes son clave candidata de la relación.

Dada una dependencia funcional { $X$ } -> { $Y$ }, un determinante es el conjunto { $X$ }.

Notas(DNIALumno, CodiAsignatura, CodiMatricula, Nota)

DNIAlumno | CodiAsignatura | CodiMatricula | Nota
:--: | :--: | :--: | :--:
111 | 1000 | 123 | A
111 | 2000 | 123 | B
222 | 3000 | 215 | B
222 | 1000 | 215 | B
222 | 2000 | 215 | C

### Determinantes
**DNIAlumno** -> CodiMatricula
**CodiMatricula** -> DNIAlumno
**DNIAlumno, CodigoAsignatura** -> CodiMatricula, Nota
**CodiAsignatura, CodiMatricula** -> DNIAlumno, Nota
### Claves candidatas
DNIAlumno, CodigoAsignatura 
CodiAsignatura, CodiMatricula
## Conceptos importantes
### Superclave
La superclave de una relación R(A1, A2, ...,An) es un conjunto de los atributos del esquema tal que en su instancia no puede haber dos tuplas que tengan la misma combinación de valores para los atributos del subocnjunto.

$R(A1, A2, A3, A4, A5)$

### Clave/LLave candidata
La clave candidata de una relación es una superclave C de la relacion que cumple que ningún subconjunto propio de C no es superclave.

Nota(DNI, id_Asignatura, id_Nota, nota)
- DNI, id_Asignatura: Posible superclave
- id_Nota: Posible superclave

### Clave/LLave principal

### Clave/LLave alternativa
> Cuando hay dos posibles superclaves, la que no se convierte superclave no es clave alternativa
### Dependencia indirecta
Si:
{ $X$ } -> { $Y$ }
{ $Y$ } -> { $Z$ }
Entonces:
{ $X$ } -> { $Z$ }

### Otra regla del 2FN???
Si un atributo no clave depende de manera parcial de la clave

Un atributo no puede depender de manera parcial ni de la PK ni de una clave candidata.
