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
R2(A, C, D)
R3(C, F)
## 3FN
R1(A, B, E)
R2(A, C, D)
R3(C, F)
## FNBC

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