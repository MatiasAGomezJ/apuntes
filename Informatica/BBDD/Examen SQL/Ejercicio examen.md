3- Dado el siguiente modelo relacional de una BBDD, realiza las siguientes consultas en SQL.
![](https://i.imgur.com/8q8lnu1.png)

3.1 Mostrar los vuelos que operan entre los dias 09/10/2021 y 20/10/2021.
```sql
SELECT NumVol
FROM Vol 
ON Data BETWEEN "09-10-2021" AND "20-10-2021";
```

3.2 Mostrar los vuelos que ha reservado Gandalf.
```sql
SELECT NumVol
FROM Viatge
JOIN Passatger
ON Viatge.ID = Passatger.ID AND Passatger.NomPA = "Gandalf";
```
3.3 Contar el número de vuelos que aterrizan o despegan desde ESP.
```sql
SELECT COUNT(NumVol)
FROM Vol
JOIN Aeroport
ON Aeroport.Pais = "ESP" AND ((Vol.NomAerOrigen = Aeroport.NomAeroport) OR (Vol.NomAerDestí = Aeroport.NomAeroport))
```
3.4 Mostrar las reservas ( número de vuelo, aeropuerto de salida y llegada ) de Anakin.
```sql
SELECT Vol.NumVol, Vol.NomAerOrigen, Vol.NomAerDestí
FROM  Vol
JOIN Viatge JOIN Passatger
ON Vol.NumVol = Viatge.NumVol AND Viatge.ID = Passatger.ID AND Passatger.NomPa = "Anakin";
```
3.5 Mostrar el nombre de pasajeros que salen de ESP. ( Evitar valores repetidos! )
```sql
SELECT DISTINCT Passatger.NomPa
FROM Passatger
JOIN Viatge JOIN  Vol JOIN Aeroport
ON Passatger.ID = Viatge.ID AND Viatge.ID = Vol.NumVol AND Vol.NomAerOrigen = Aeroport.NomAeroport AND Aeroport.Pais = "ESP"
```
3.6 Calcular el número de plazas que ha reservado Yoda.
```sql
SELECT SUM(Viatge.Places) 
AS nº_places
FROM Viatge
JOIN Passatger
ON Viatge.ID = Passatger.ID AND Passatger.NomPa = "Yoda"
```
3.7 Mostrar las compañias sin vuelas programados.
```sql
SELECT Companyia.Nomco
FROM Companyia 
LEFT JOIN Vol
ON companyia.Nomco = Vol.NomCo AND Vol.NumVol IS NULL
```
3.8 Mostrar la lista de compañias y la suma de las plazas de sus vuelo sin reservas.
```sql
SELECT Vol.Nomco, SUM(Viatge.Capacitat)
AS NºPlazas
FROM Vol
LEFT JOIN Viatge
ON Vol.NumVol = Viatge.NumVol AND Viatge.ID is NULL
GROUP BY vol.NomCo
```
![](https://i.imgur.com/8q8lnu1.png)

**BONUS**: Mostrar de las compañias españolas que despegan desde El Prat, la cantidad de vuelos, suma de plazas y suma de plazas reservadas.
```sql
SELECT vol.NomCo, COUNT(vol.NumVol) AS 'numVols', SUM(vol.Capacitat) AS 'Capacitat', SUM(r_reserva.Places) AS 'placesReservades'
FROM vol
JOIN Viatge JOIN Companyia
ON Vol.NumVol = Viatge.NumVol AND Vol.NomCo = Companyia.NomCo AND Companyia.Pais = "ESP" AND Vol.NomAerOrigen = "El Prat"
GROUP BY companyia.NomCo
```
30- Mostrar el nombre del pasajero, numero de vuelo, dia de vuelo, nombre del aeropuerto de despegue, país desde el cual despega el avión, compañía del vuelo y país de la compañía de los vuelos que tienen lugar el mes de octubre del año 2009, que no son de compañía francesa, española ni inglesa, que tienen una capacidad de vuelo entre 100 y 150 pasajeros y despegan desde aeropuertos que empiezan por "S".
```sql
SELECT NomPa, Viatge.NumVol, Viatge.Data, Vol.NomAerOrigen, Aeroport.Pais, Vol.NomCo, Companyia.Pais
FROM Vol
JOIN Viatge
ON Vol.NumVol = Viatge.NumVol
JOIN Passatger
Viatge.ID = Passatger.ID
JOIN Aeroport
ON Vol.NomAerOrigen = Aeroport.NomAeroport
JOIN Companyia
ON Vol.NomCo = Companyia.NomCo
WHERE (Vol.Data BETWEEN "2009-10-01" AND "2009-10-31") AND (Companyia.Pais NOT IN ("França", "Espanya", "Regne Unit")) AND (Vol.Capacitat BETWEEN 100 AND 150) AND Vol.NomAerOrigen LIKE "S%"
```
31- Seleccionar las compañias que tienen más de 2 vuelos, ordenados de forma descendente.
```sql
SELECT NomCo
FROM Vol
HAVING COUNT(NumVol) > 2
ORDER BY NomCo DESC;
```