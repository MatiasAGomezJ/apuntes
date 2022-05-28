# De Entidad-Relacion a relacional
##  Primero & Segundo
Escoger una clave principal para cada entidad/relacion/tabla:
- Soci(nom_soci, nacionalitat, ***# id_legal***, adreça, telefon, compte_corrent)
- Embarcació(nom_embarcacio, ***# matricula***, material, eslora,  manega, calat, any, tipus)
- Motor(tipus_motor, marca, potencia, ***# matricula***)
- Vela(tipus_vela, quantitat_veles, ***# matricula***)
- Amarrarrament(***# nom_amarrament***,  grandaria, geoposicio)
- Tipus_amarrament(***# tipus_amarrament***, cost_anual, mida_maxima_embarcacio)
- Propietat(data_inici_propietat, data_fi_propietat, ***# id_propietat***)
- Conscessio(data_inici_concessio, data_fi_concessio, ***# id_concessio***)
- Localitzacio(data_inici_localitzacio, data_fi_localitzacio, ***# id_localitzacio***)

## Tercero
Cada una de las relaciones del modelo relacional se convierte en una tabla/relacion del modelo relacional, con sus atributos mas las claves de las entidades que relaciona.
- R_Soci_Propietat(id_legal, id_propietat)
- R_Soci_Concessio(id_legal, id_concessio)
- R_Embarcacio_Propietat(matricula, id_propietat)
- R_Embarcacio_Localitzacio(matricula, id_localitzacio)
- R_Amarrament_Concessio(nom_amarrament, id_concessio)
- R_Amarrament_Localitzacio(nom_amarrament, id_localitzacio)
- R_Amarrament_Tipus_amarrament(nom_amarrament, tipus_amarrament)

## Cuarto
Se elige una clave principal para cada una de las nuevas relaciones/tablas.
- Si se tiene una relacion:
	- 0/1 .. 1 -0/1 ..  1 se elige cualquiera
	- 0/1 .. `*` - 0/1 .. 1 se elige la PK del `*`
	- 0//1 .. * - 0/1 .. * se elige como PK de las dos PK juntas

- R_Soci_Propietat(id_legal, ***# id_propietat***)
- R_Soci_Concessio(id_legal, ***# id_concessio***)
- R_Embarcacio_Propietat(matricula, ***# id_propietat***)
- R_Embarcacio_Localitzacio(matricula, ***# id_localitzacio***)
- R_Amarrament_Concessio(nom_amarrament, ***# id_concessio***)
- R_Amarrament_Localitzacio(nom_amarrament, ***# id_localitzacio***)
- R_Amarrament_Tipus_amarrament(***# nom_amarrament***, tipus_amarrament)

# Quinto
Fusionar, si es posible diferentes tablas del modelo relacional.
- Soci(nom_soci, nacionalitat, ***# id_legal***, adreça, telefon, compte_corrent)
- Embarcació(nom_embarcacio, ***# matricula***, material, eslora,  manega, calat, any, tipus)
- Motor(tipus_motor, marca, potencia, ***# matricula***)
- Vela(tipus_vela, quantitat_veles, ***# matricula***)
- Amarrarrament(***# nom_amarrament***,  grandaria, geoposicio, tipus_amarrament)
- Tipus_amarrament(***# tipus_amarrament***, cost_anual, mida_maxima_embarcacio)
- Propietat(data_inici_propietat, data_fi_propietat, ***# id_propietat***, id_legal, matricula)
- Conscessio(data_inici_concessio, data_fi_concessio, ***# id_concessio***, id_legal, nom_amarrament)
- Localitzacio(data_inici_localitzacio, data_fi_localitzacio, ***# id_localitzacio***, matricula, nom_amarrament)

![](https://i.imgur.com/zPCEVkI.png)

