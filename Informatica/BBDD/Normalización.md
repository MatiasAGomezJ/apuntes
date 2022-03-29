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
Una relación está en 2FN, si y solo si, está en 1FN y todo atributo no clave depende funcionalmente en forma completa de la PK.

Excepción: un atributo puede depender funcionalmente de parte de la PK si este atributo es parte de una clave alternativa. 

## Conceptos importantes
### Superclave
La superclave de una relación R(A1, A2, ...,An) es un conjunto de los atributos del esquema tal que en su instancia no puede haber dos tuplas que tengan la misma combinación de valores para los atributos del subocnjunto.

$R(A1, A2, A3, A4, A5)$

### Clave/LLave candidata
La clave candidata de una relación es una superclave C de la relacion que cumple que ningún subconjunto propio de C no es superclave.

> Una superclave está compuesta de claves candidatas 
> -Matias

Nota(DNI, id_Asignatura, id_Nota, nota)
- DNI, id_Asignatura: Posible superclave
- id_Nota: Posible superclave

### Clave/LLave principal


- Clave/LLave alternativa