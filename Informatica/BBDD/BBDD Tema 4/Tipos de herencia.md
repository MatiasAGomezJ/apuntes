Sea `C` una superclase, `K` su PK, `A1`, `A2`, ..., `An` atributos de `C` y `S1`, `S2`, ..., `Sn` las subclases de `C`.

# Opcion 1
- `C` = {K, A1, ..., An}
- Li, 1 <= i <= m; AH (Li)  = {B1, B2, ..., Bn, K}
- Li, 1 <= i <= m; AH (Li)  = {C1, C2, ..., Cn, K}
- Para M, O; O, XOR

- C (#K, A1, A2, ..., An)
- S1 (B1, B2, ..., Bn) U { K } -> S1 (#K, B1, B2, ..., Bn)
- S2 (C1, C2, ..., Cn) U { K } -> S2 (#K, C1, C2, ..., Cn)


Ejemplo 1:

Trabajador (#DNI, edad, nombre)
Autonomo (numAutonomo) U {#DNI} -> Autonomo (#DNI, numAutonomo)
Asalariado (sueldoBase, nombreEmpresa) U {#DNI}  -> Asalariado (#DNI, sueldoBase, nombreEmpresa)

Trabajador (#DNI, edad, nombre)
Autonomo (#DNI, numAutonomo)
Asalariado (#DNI, sueldoBase, nombreEmpresa)

# Opcion 2 (solo en {M, XOR})
Crear una tabla para Si conatributos:
- Atributos (Li) = {Atributos Si} U { K, A1, A2, ..., An}, PK (Li) = K
- Atributos (L1) = {B1, B2, ..., Bn} U { K, A1, A2, ..., An}, PK (L1) = K

- L1 (B1, B2, ..., Bn, K, A1, A2, ..., An)
- L2 (C1, C2, ..., Cn, K, A1, A2, ..., An)


> Li: tabla de una subclase de numero i

Ejemplo 2:
{ M, XOR }
- Vehiculo (#matricula, precio)
- Coche (numPuertas)
- Camión (numEjes, carga)

- Coche (numPuertas,#matricula,precio)
- Camión (numEjes,carga,#matricula,precio)

# Opcion 3
Crear una tabla L que tendrá como atrbibutos:
Atributos (L)  = {K,A1, ..., An} U { Atributos Sn} U {Atributos Sn} U {T}

Ejemplo 3:

{M, XOR}
Opcion1:
Deportista (#NSS, edad)
Tenista (#NSS, diestro)
Futbolista (#NSS, posicion)

Opcion2:
Tenista (#NSS, diestro, edad)
Futbolista(#NSS, posicion, edad)

Opcion3:
Deportista(#NSS, edad, diestro, posicion, tipoDeportista)

Deportista | NSS | edad | tipoDep | diestro | posicion
:--: | :--: | :--: | :--: | :--: | :--: 
_ | 1 | 28 | T | D | null
_ | 2 | 35 | F | null | P
_ | 3 | 28 | null | null | null

{O, XOR}
Opcion1:



Opcion3:

# Opcion 4
Crear una sola tabla L con atributos:
Atributos (L) = {Atributos C} U {Atributos S1} U ... U {Atributos Sn} U {T1,...,Tn} y PK (L) = K

L | K | A1 | ... | An | T1 | B1 | ... | Bn | T2 | C1 | ... | Cn | ... | Tn | Z1 | ... | Zn
:--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--:
1 | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - |


Ejemplo 4:

Empleado| NSS | nombre | fechaNacimiento | direccion | isSecretario | VelocidadTecleo | isTecnico | gradoTecnico | isIngeniero | tipoIngeniero 
:--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: 
1 | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - |
