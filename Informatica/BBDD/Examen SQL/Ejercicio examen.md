3- Dado el siguiente modelo relacional de una BBDD, realiza las siguientes consultas en SQL.
![](https://i.imgur.com/8q8lnu1.png)

3.1 Mostrar los vuelos que operan entre los dias 09/10/2021 y 20/10/2021.
SELECT NumVol
FROM Vol 
ON Data BETWEEN "09-10-2021" AND "20-10-2021";

3.2 Mostrar los vuelos que ha reservado Gandalf.
SELECT NumVol
FROM Viatge
JOIN Passatger
ON Viatge.ID = Passatger.ID AND Passatger.NomPA = "Gandalf";

3.3 Contar el número de vuelos que aterrizan o despegan desde ESP.
SELECT COUNT(NumVol)
FROM Vol
JOIN Aeroport
ON Aeroport.Pais = "ESP" AND ((Vol.NomAerOrigen = Aeroport.NomAeroport) OR (Vol.NomAerDestí = Aeroport.NomAeroport))

3.4 Mostrar las reservas ( número de vuelo, aeropuerto de salida y llegada ) de Anakin.
SELECT Vol.NumVol, Vol.NomAerOrigen, Vol.NomAerDestí
FROM  Vol
JOIN Viatge JOIN Passatger
ON Vol.NumVol = Viatge.NumVol AND Viatge.ID = Passatger.ID AND Passatger.NomPa = "Anakin";

3.5 Mostrar el nombre de pasajeros que salen de ESP. ( Evitar valores repetidos! )
SELECT DISTINCT Passatger.NomPa
FROM Passatger
JOIN Viatge JOIN  Vol JOIN Aeroport
ON Passatger.ID = Viatge.ID AND Viatge.ID = Vol.NumVol AND Vol.NomAerOrigen = Aeroport.NomAeroport AND Aeroport.Pais = "ESP"


3.6 Calcular el número de plazas que ha reservado Yoda.
SELECT SUM(Viatge.Places) 
AS nº_places
FROM Viatge
JOIN Passatger
ON Viatge.ID = Passatger.ID AND Passatger.NomPa = "Yoda"

3.7 Mostrar las compañias sin vuelas programados.
SELECT Companyia.Nomco
FROM Companyia 
LEFT JOIN Vol
ON companyia.Nomco = Vol.NomCo AND Vol.NumVol IS NULL

3.8 Mostrar la lista de compañias y la suma de las plazas de sus vuelo sin reservas.
SELECT Vol.Nomco, SUM(Viatge.Capacitat)
AS NºPlazas
FROM Vol
LEFT JOIN Viatge
ON Vol.NumVol = Viatge.NumVol AND Viatge.ID is NULL


![](https://i.imgur.com/8q8lnu1.png)

**BONUS**: Mosrar de las compañias españolas que despegan desde El Prat, la cantidad de vuelos, suma de plazas y suma de plazas reservadas.
