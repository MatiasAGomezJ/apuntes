# DTD
## 0Sintaxis
### 0.1 Interno
![](https://i.imgur.com/t0u5Ibt.png)

Este es el que usaremos (probablemente) la mayoria del tiempo.
```xml
<!DOCTYPE elemento [
	<!ELEMENT sub-elemento (sub-sub-elementos)>
	<!ELEMENT sub-sub-elemento (#PCDATA)>
]>
<elemento>
	<sub-elemento>
		<sub-sub-elemento> info </sub-sub-elemento>
	</sub-elemento>
<elemento>
```
### 0.2 Externo
#### 0.2.1 Privado
![](https://i.imgur.com/o5vRIxF.png)

Archivo1.xml
```xml
<!DOCTYPE elemento SYSTEM "ruta/Archivo2.xml">
<elemento>
	<sub-elemento>
		<sub-sub-elemento> info </sub-sub-elemento>
	</sub-elemento>
<elemento>
```
Archivo2.xml
```py
<!ELEMENT sub-elemento (sub-sub-elementos)>
<!ELEMENT sub-sub-elemento (#PCDATA)>
```
#### 0.2.2 Público
![](https://i.imgur.com/UGFCSYO.png)

Archivo1.xml
```xml
<!DOCTYPE elemento SYSTEM "FPI" "ruta/Archivo2.xml">
<elemento>
	<sub-elemento>
		<sub-sub-elemento> info </sub-sub-elemento>
	</sub-elemento>
<elemento>
```
Archivo2.xml
```xml
<!ELEMENT sub-elemento (sub-sub-elementos)>
<!ELEMENT sub-sub-elemento (#PCDATA)>
```

Que es una FPI? Pues [aquí](https://es.wikipedia.org/wiki/Formal_Public_Identifier) tienes.
Dudo que lo usemos.

## 1 Declaración de elementos
El elemento puede ser:
### 1.1 EMPTY
Vacio en ingles, no puede tener contenido.
Tampoco puede tener atributos.
```xml
<!DOCTYPE elementos_vacios [
	<!ELEMENT elemento_vacio EMPTY>
]>

<elementos_vacios>
	<elemento_vacio></elemento_vacio>
	<elemento_vacio />
</elementos_vacios>
```
Los dos son maneras validas de representarlos
### 1.2 (#PCDATA)
El elemento puede contener texto.
No contienen etiquetas ni otros elementos
No se pueden utilizar los siguientes carácteres:
- "<"
- "&"
- "]]>"

```xml
<!DOCTYPE client [
	<!ELEMENT client (nom)>
	<!ELEMENT nom (#PCDATA)>
]>

<client>
	<nom> Juan </nom>
</client>
```
### 1.3 ANY 
Pot contenir atributs.
No se utiliza mucho, ja que es preferible estructurar los contenidos
```xml
<!DOCTYPE color[
  <!ELEMENT color ANY>
  <!ELEMENT color ANY>
  <!ELEMENT color ANY>
]>

<color />
<color>Això és un exemple</color>
<color>Això és <color> un exemple</color></color>
```
### 1.4 , (coma)
Significa que l'element conté una série de fills en l'ordre indicat.
```xml
<!DOCTYPE alumne [
   <!ELEMENT alumne (nom, data_matricula, modul)>
   <!ELEMENT nom (#PCDATA)>
   <!ELEMENT data_matricula (#PCDATA)>
   <!ELEMENT modul (#PCDATA)>
]>

<alumne>
   <nom>Carlos</nom>
   <data_matricula>26-09-2020</data_matricula>
   <modul>Llenguatges</modul>
</alumne>
```
### 1.5 | (OR)
Significa que l'element contè nomès un dels dos fills indicats.
```xml
<!DOCTYPE alumne [
   <!ELEMENT alumne (nom, (data_matricula | curs), modul)>
   <!ELEMENT nom (#PCDATA)>
   <!ELEMENT data_matricula (#PCDATA)>  
   <!ELEMENT curs (#PCDATA)>
   <!ELEMENT modul (#PCDATA)>
]>
  
<alumne>
   <nom>Carlos</nom>
   <data_matricula>26-09-2020</data_matricula>
   <modul>Llenguatges</modul>
</alumne>
```
### 1.6 ?
Significa que l'element pot aparèixer o no, però nomès una vegada
```xml
<!DOCTYPE pizza [  
  <!ELEMENT pizza (nom, forma?)>  
  <!ELEMENT nom (#PCDATA)>  
  <!ELEMENT forma (#PCDATA)>  
]>  
  
<!--Validació correcta-->  
<pizza>  
   <nom> Margarita </nom>  
   <forma> rodona </forma>  
</pizza>  
  
<!--Validació correcta-->
<pizza>  
   <nom> Napolitana </nom>  
</pizza>  
```
### 1.7 *
Significa que l'element pot no aparèixer o aparèixer una o més vegades.
```xml
<!DOCTYPE arcoiris [
  <!ELEMENT arcoiris (color*)>
  <!ELEMENT color (#PCDATA)>
]>

----------------------
<arcoiris>
  <color>Blau</color>
  <color>Negre</color>
  <color>Groc</color>
</arcoiris>
```
### 1.8 +
Significa que l'element ha d'apaerèixer una o més vegades (no pot no aparèixxer).
```xml
<!DOCTYPE arcoiris [
  <!ELEMENT arcoiris (color+)>
  <!ELEMENT color (#PCDATA)>
]>

<arcoiris>
  <color>Blau</color>
  <color>Negre</color>
  <color>Groc</color>
</arcoiris>
```
### 1.9 ()
Permet agrupar expressions.
```xml
<!DOCTYPE el_agrupat [  
  <!ELEMENT el_agrupat (a, (c|b))>  
  <!ELEMENT a EMPTY>  
  <!ELEMENT b EMPTY>  
  <!ELEMENT c (#PCDATA)>  
]>  
  
<!-- Validació correcta-->
<el_agrupat>
   <a/>
   <b/>
</el_agrupat>

<!-- Validació correcta-->
<el_agrupat>  
   <a/>
   <c> Rosa </c>    
</el_agrupat>
```
## 2 Declaració d'atributs
Se declara de la siguiente manera:
```xml
<!ATTLIST nom_element nom_atribut tipus_atribut valor_inicial_atribut>
```
Cuando quieres definir varios atributos dentro del mismo elemento:
```xml
<!ATTLIST nom_element nom_atribut1 tipus_atribut1 valor_inicial_atribut1>  
<!ATTLIST nom_element nom_atribut2 tipus_atribut2 valor_inicial_atribut2>  
  
<!ATTLIST nom_element  
  nom_atribut1 tipus_atribut1 valor_inicial_atribut1  
  nom_atribut2 tipus_atribut2 valor_inicial_atribut2  
>
```

Tipus d'atributs:
#