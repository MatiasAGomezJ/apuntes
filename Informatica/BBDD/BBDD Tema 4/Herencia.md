# Herencia
Hay dos tipos de herencia:
- M: Mandatory
- O: Optional	

Mandatory: te que ser si o si les subclasses
Optional: Puede no ser una de sus subclases
## AND-OR-XOR
Logica bool

a | b | AND | OR | XOR
:--: | :--: | :--: | :--: | :--:
0 | 0 | 0 | 0 | 0
1 | 0 | 0 | 1 | 1
0 | 1 | 0 | 1 | 1
1 | 1 | 1 | 1 | 0

# 1º ejemplo
- Trabajador, con subclases asalariado y autonomo {M, XOR} || {M, OR}
# 2º ejemplo
- Enfermedad, con subclases vírica y bacteriana {O, XOR}
# 3º ejemplo
- Empresa, con sublases publica y privada {M, OR}
# 4º ejemplo
-  Persona, con subclases alumno y trabajador {O, OR}