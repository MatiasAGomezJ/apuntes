# Operacion renombrar
Permite asignar un nombre R a una relacion resultante de una operacion de algegra relacional
R := E

# Operación de selección
Partiende de una relacion R, obtiene una nueva relacion formada con todas las tuplas de R que cumple la condicion c.
σc (R)

## Ejemplo 1
Compañia

NomCo  | Pais 
:--: | :--: 
iberia | ESP  
-  | UK 
-  | AL
-  | FR
Air Europa | ESP
- | UK
- | CH

σ(Pais='ESP') (Compañia)

## Ejemplo 2
NumVol | dia | NumAerOrigen
:--: | :--: | :--:
111 | 10/10/09 | Gatwick
444 | 10/10/09 | Gatwick

Vuelos que salen de Gatwick el dia 10/10/09

σ(Dia='10/10/9' & NumAerOrigen='Gatwick') (Compañia)
σ(Dia='10/10/9' AND NumAerOrigen='Gatwick') (Compañia)

# Operacion de proyección
Partiendo de una relacion R, obtiene una nueva relación formada con todas las tuplas de R, pero únicamente los atributos A1, A2, ... , An especificados.

π A1, A2, ..., An (R)

## Ejemplo 1
NomAero | Ciudad |  Pais
:--: | :--: | :--:
Son Sant Joan | Palma | Espanya
Gatwick | Londres | Regne Unit
Heathrow | Londres | Regne Unit
Halle-Leipzig | Leipzig | Alemanya
El Prat | Barcelona | Espanya

π NumVuelo (Vuelo)

## Ejemplo 2

Saca todos los nombres de areopuertos de españa

π NomAeroport (σ(Pais='Espanya') (Aeroport))
SELECT NomAero FROM Aeroport WHERE pais='Espanya';

# Operacion combinacción o JOIN
Partiendo de dos relaciones R y S, obtiene una nueva relación formada por las tuplas que resultan de concatenar las tuplas de R con las de S u que cumple una condición c especificada.
R[c]S

## Ejemplo 1
Lista de vuelos reservados de Gandalf.
![](https://i.imgur.com/zItSpeq.png)
A = Viatge
B = Passatger

π NumVuelo (Viagte [NomPass='Gandalf' & Viatge.ID = Passatger.ID] Passatger)

# Ejercicios
## El que nos dió el
Listar el número de vuelo de los vuelos que van a ElPrat el dia 26/10/2009 con una capacidad mayor a 100 plazas.

π NumVuelo (σ(Dia='26/10/2009' & NomAerOrigen='ElPrat' & Capacitat > 100) (Vol)) 

Listar el número de vuelo y aeropuerto de destino de los vuelos de las compañias españolas que salen de ElPrat.

π NumVuelo, NomAerOrigen (Vol [Vol.NomAerOrigen = 'El Prat' & Vol.NomCo = Companya.NomCo & Companya.Pais = 'Espanya'] Companya)
## De vuelos


> A partir de aquí no entra en el temario

# Operación unión
Partiendo de dos relaciones R y S , obtiene una neuva relación formada por todas las tuplas de R  y de S.

![](https://i.imgur.com/sGcwpwt.png)

# Operación intersección
Partiendo de dos relaciones R y S, obtiene uan nueva relación formada por todas las tuplas que están en R y en S.

![](https://i.imgur.com/AoXBWvR.png)

# Operación diferencia
Partiendo de dos relaciones R y S, obtiene uan nueva relación formada por todas las tuplas de R que no están S.

## Ejercicios
Listar los números de vuelo y AeroDestino de los vuelos que salen de 'Son Sant Joan' o 'El Prat'
A:= σ(NomAerOrigen = 'Son Sant Joan')(Vuelo)
B:= σ(NomAerOrigen = 'El Prat')(Vuelo)
π NumVol, NomAerDestí(AUB)

Listar el nombre de AerDestí de los vuelos  que salen de 'Son Sant Joan' y 'El Prat'

# Operacción producto cartesiana
Partiendo de dos relaciones R y S. Obtiene una nueva relacción formada por todas las tuplas que resultan de concatenar todas las tuplas de R con todas alas tuplas de S.

R x S

SELECT * 
FROM Passatget 
JOIN Viatge
ON Passatger.ID = Viatge.ID

π NumVol(Passatger[Passatger.ID = Viatge.ID AND Passatger.NumPass = "Noe"]Viatge)