# DTD
## 0Sintaxis
### 0.1 Interno
![](https://i.imgur.com/t0u5Ibt.png)

Este es el que usaremos (probablemente) la mayoria del tiempo.
```xml
<!DOCTYPE elemento [
	<!ELEMENT elemento (sub-elementos)>
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
```xml
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
### El elemento puede ser:
#### 1.1 EMPTY
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
#### 1.2 \#PCDATA
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
#### 1.3 ANY 
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

### Sintaxis
#### 1.4 , (coma)
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
#### 1.5 | (OR)
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
#### 1.6 ?
Significa que l'element pot aparèixer o no, però nomès una vegada
```xml
<!DOCTYPE pizza [  
  <!ELEMENT pizza (nom, forma?)>  
  <!ELEMENT nom (#PCDATA)>  
  <!ELEMENT forma (#PCDATA)>  
]>  
  
<!-- Validació correcta -->  
<pizza>  
   <nom> Margarita </nom>  
   <forma> rodona </forma>  
</pizza>  
  
<!-- Validació correcta -->
<pizza>  
   <nom> Napolitana </nom>  
</pizza>  
```
#### 1.7 *
Significa que l'element pot no aparèixer o aparèixer una o més vegades.
```xml
<!DOCTYPE arcoiris [
  <!ELEMENT arcoiris (color*)>
  <!ELEMENT color (#PCDATA)>
]>

<!---------------------->
<arcoiris>
  <color>Blau</color>
  <color>Negre</color>
  <color>Groc</color>
</arcoiris>
```
#### 1.8 +
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
#### 1.9 ()
Permet agrupar expressions.
```xml
<!DOCTYPE el_agrupat [  
  <!ELEMENT el_agrupat (a, (c|b))>  
  <!ELEMENT a EMPTY>  
  <!ELEMENT b EMPTY>  
  <!ELEMENT c (#PCDATA)>  
]>  
  
<!-- Validació correcta -->
<el_agrupat>
   <a/>
   <b/>
</el_agrupat>

<!-- Validació correcta -->
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
  
<!-- O -->

<!ATTLIST nom_element  
  nom_atribut1 tipus_atribut1 valor_inicial_atribut1  
  nom_atribut2 tipus_atribut2 valor_inicial_atribut2  
>
```

### 2.1 Tipus d'atributs:
#### 2.1.1 CDATA
L'atribut conté caràcters.
```xml
<!DOCTYPE element_x [  
  <!ELEMENT element_x EMPTY>  
  <!ATTLIST element_x color CDATA>  
]>  
  
<!-- Validació correcte -->
<element_x color="vermell" />  
```
#### 2.1.2 NMTOKEN
L'atribut només conté pot contenir lletres, dígits i els caràcters punt, guió, subratllat i el dos punts.
```xml
<!DOCTYPE element_x [  
  <!ELEMENT element_x EMPTY>  
  <!ATTLIST element_ color NMTOKEN #REQUIRED>  
]>  
  
<!-- Validació correcta -->  
<element_x color="blau_turquesa" />  

<!-- ERROR: hi ha un espai en blanc -->
<element_x color="blau turquesa" />
```
#### 2.1.3 NMTOKENS
L'atribut és com NMTOKEN acceptant també espais en blanc.
```xml
<!DOCTYPE element_x [  
  <!ELEMENT element_x EMPTY>  
  <!ATTLIST element_x color NMTOKENS #REQUIRED>  
]>  
  
<!-- Validació correcta -->  
<element_x color="1" />  
  
<!-- Validació correcta -->  
<element_x color="blau turquesa" />  
  
<!-- ERROR: hi ha un asterisc i NMTOKEN no admet asteriscs -->
<element_ color="2*2" />
```
### 2.2 Tipos de valores:
#### 2.2.1 Valores por defecto
##### De una lista:
La llista ha d'anar entre parèntesi, separats els elements per una barra vertical "|".
```xml
<!DOCTYPE arcoiris [  
  <!ELEMENT arcoiris EMPTY>  
  <!ATTLIST arcoiris color (blau|blanc|vermell) #REQUIRED>  
]>

<!-- Validació correcta -->
<arcoiris color="blau" />

<!-- ERROR: "verd" no està a la llista de valors -->
<arcoiris color="verd" />
```
##### Solo uno:
Si volem establir un element per defecte, es posa entre cometes.
```xml
<!-- No hay ejemplo sorry -->
```
#### 2.2.2 ID
El valor de l'atribut (no el nom) ha de ser únic i no es pot repetir a altres elements o atributs. No pot contenir espais en blanc.
```xml
<!DOCTYPE biblioteca [  
  <!ELEMENT biblioteca (llibre*)>  
  <!ELEMENT llibre (#PCDATA) >  
  <!ATTLIST llibre codi ID #REQUIRED>  
]>  
<!-- Validació correcta --> 
<biblioteca>  
  <llibre codi="Lli1">Poema de Mio Cid</llibre>  
  <llibre codi="Lli2">Cien años de Soledad</llibre>  
</biblioteca>  
 
<!-- ERROR: no es pot repetir un atribut de tipus ID -->  
<biblioteca>  
  <llibre codi="Lli1">Poema de Mio Cid</llibre>  
  <llibre codi="Lli1">Cien años de Soledad</llibre>
</biblioteca>
```
#### 2.2.3 IDREF
El valor de l'atribut ha de coincidir amb el valor de l'atribut ID d'un altre element.
```xml
<!DOCTYPE biblioteca [  
  <!ELEMENT biblioteca ((llibre|prestec)*)>  
  <!ELEMENT llibre (#PCDATA) >  
  <!ATTLIST llibre codi ID #REQUIRED>  
  <!ELEMENT prestec (#PCDATA) >  
  <!ATTLIST prestec codi_prestec IDREF #REQUIRED>  
]>  
  
<!-- Validació correcta -->  
<biblioteca>  
  <llibre codi="Lli1">Poema de Mio Cid</llibre>  
  <prestec codi_prestec="Lli1">Pepe Mir</prestec>  
</biblioteca>  

<!-- ERROR: el valor "Lli2" no és ID de cap element -->
<biblioteca>  
  <llibre codi="Lli1">Poema de Mio Cid</llibre>  
  <prestec codi_prestec="Lli2">Pepe Mir</prestec>  
</biblioteca>  
```
#### 2.2.4 IDREFS
El valor de l'atribut és una sèrie de valors separats per espais que coincideixen amb el valor de l'atribut ID d'altres elements.
```xml
<!DOCTYPE biblioteca [  
  <!ELEMENT biblioteca ((llibre|prestec)*)>  
  <!ELEMENT llibre (#PCDATA) >  
  <!ATTLIST llibre codi ID #REQUIRED>  
  <!ELEMENT prestec (#PCDATA) >  
  <!ATTLIST prestec codi_prestec IDREFS #REQUIRED>  
]>  
  
<!-- Validació correcta -->  
<biblioteca>  
  <llibre codi="Lli1">Poema de Mio Cid</llibre>  
  <llibre codi="Lli2">Cien años de Soledad</llibre>  
  <prestec codi_prestec="Lli1 Lli2">Pepe Mir</prestec>  
</biblioteca>  

<!-- ERROR: el valor "Lli3" no és ID de cap element -->  
<biblioteca>  
  <llibre codi="Lli1">Poema de Mio Cid</llibre>  
  <llibre codi="Lli2">Cien años de Soledad</llibre>  
  <prestec codi_prestec="Lli3"> Pep Matas</prestec>
<biblioteca>  
```
### 2.3 Sub-tipos de valores:
Se escriben despues del tipo de valor, creo.
#### 2.3.1 \#REQUIRED
L'atribut és obligatori, encara que no s'especifica cap valor predeterminat.
```xml
<!DOCTYPE obligatori [  
  <!ELEMENT obligatori EMPTY>  
  <!ATTLIST obligatori color CDATA #REQUIRED>  
]>  
  
<!-- Validació correcta -->  
<obligatori color="" />  
  
<!-- Validació correcta -->
<obligatori color="grog" />  

<!-- ERROR: falta l'atribut "color" -->
<obligatori />
```
#### 2.3.2 \#IMPLIED
L'atribut no és obligatori i no s'especifica cap valor predeterminat.
```xml
<!DOCTYPE no_obligatori [  
  <!ELEMENT no_obligatori EMPTY>  
  <!ATTLIST no_obligatori color CDATA #IMPLIED>  
]>  
  
<!-- Validació correcta -->  
<no_obligatori />  
  
<!-- Validació correcta -->  
<no_obligatori color="" />  
  
<!-- Validació correcta -->
<no_obligatori color="grog" />  
```
#### 2.3.3 \#FIXED
L'atribut té un valor fix.
```xml
<!DOCTYPE fixat [  
  <!ELEMENT fixat EMPTY>  
  <!ATTLIST fixat color CDATA #FIXED "verd">  
]>  
<!-- ERROR: l'atribut "color" no té el valor "verd" -->
<fixat color="" />

<!-- ERROR: l'atribut "color" no té el valor "verd" -->
<exemple color="grog" />
```
## 3 Declaració d'entitats
Una entidad es como una variable, guarda informacion y se puede acceder a partir de su nombre.
```xml
<!ENTITY nom_entitat "text">
```
Ejemplo:
```xml
<!DOCTYPE texts [  
   <!ELEMENT cites (text+)>  
   <!ELEMENT text (#PCDATA)>
   <!ENTITY escriptor "Miguel de Cervantes">  
   <!ENTITY obra "El Quijote">
]>

<texts>  
   <cites>  
      <text>&obra; va ser escrita per &escriptor; </text>  
      <text>&escriptor; era espanyol</text>  
   </cites>  
   <cites>  
      <text> Si buscas la perfección nunca estarás contento. &obra;</text>  
      <text>&escriptor;. Escriptor rus (1828-1910)</text>  
   </cites>  
</texts>
```

Quan un analitzador XML troba una referència "&nom_entitat;", reportarà un text de recanvi a l'aplicació en el lloc de la referència. Pots fer la prova: Guarda el codi en un document XML i visualitza el resultat en una navegador

Para más información clica [aquí](https://aulavirtual.caib.es/c07015884/mod/book/view.php?id=9426&chapterid=2453#:~:text=3%2D%20Declaraci%C3%B3%20d%27entitats).

Recomiendo leerlo por lo menos una vez.