# Ejercicio 4
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE numeros [
    <!ELEMENT numeros (#PCDATA)>
]>
<numeros>
    <numero>10</numero>
</numeros>
```
En el esquema se indica que el elemento `numero` solo tiene que tener texto, no otras etiquetas.

Solucion 1:
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE numeros [
    <!ELEMENT numeros (#PCDATA)>
]>
<numeros>10</numeros>
```
Solucion 2:
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE numeros [
    <!ELEMENT numeros (numero)>
    <!ELEMENT numero (#PCDATA)>
]>
<numeros>
    <numero>10</numero>
</numeros>
```
# Ejercicio 5
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE aficions [
    <!ELEMENT aficions (afició*)>
    <!ELEMENT aficio (#PCDATA)>
]>
<aficions>
    <aficio>Llegir</aficio>
    Nadar
    <aficio>Caminar</aficio>
</aficions>
```
El elemento `aficions` solo puede tener dentro multiples elementos `aficio`, en este caso hay texto suelto.

Solucion:
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE aficions [
    <!ELEMENT aficions (afició*)>
    <!ELEMENT aficio (#PCDATA)>
]>
<aficions>
    <aficio>Llegir</aficio>
    <aficio>Nadar</aficio>
    <aficio>Caminar</aficio>
</aficions>
```
# Ejercicio 6
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE directors_cine [
    <!ELEMENT directors_cine (director*)>
    <!ELEMENT director ((nom | llinatge), data_naixement)>
    <!ELEMENT nom (#PCDATA)>
    <!ELEMENT llinatge (#PCDATA)>
    <!ELEMENT data_naixement (#PCDATA)>
]>
<directors_cine>
    <director>
        <nom>Stanley</nom>
        <llinatge>Kubrick</llinatge>
        <data_naixement>26 de juliol de 1928 </data_naixement>
    </director>
    <director>
        <nom>Francis</nombre> <!-- Se corrige la sintaxis -->
        <llinatge>Ford Coppola</llinatge>
        <data_naixement>7 d'abril de 1939</data_naixement>
    </director>
</directors_cine> <!-- Esto se quita -->
<director>
    <nom>Federico</nombre> <!-- Se corrige la sintaxis -->
    <llinatge>Fellini</llinatge>
    <data_naixement>20 de gener del 1920 </data_naixement>
</director>
</directors_cine>
```
Primero de todo, hay una etiqueta de cierre del elemento `directors_cine` en medio de los sub-elementos de `director`. Segundo, no está bien la sintaxis en algunas etiquetas de cierre. Por ultimo, dentro de director tiene que estar `nom` **O** `llinatge`, no los dos.

Solucion 1, Quitamos nombres o apellidos:
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE directors_cine [
    <!ELEMENT directors_cine (director*)>
    <!ELEMENT director ((nom | llinatge), data_naixement)>
    <!ELEMENT nom (#PCDATA)>
    <!ELEMENT llinatge (#PCDATA)>
    <!ELEMENT data_naixement (#PCDATA)>
]>
<directors_cine>
    <director>
	    <!-- Quitado elemento -->
        <llinatge>Kubrick</llinatge>
        <data_naixement>26 de juliol de 1928 </data_naixement>
    </director>
    <director>
        <nom>Francis</nom> <!-- Cambio -->
        <!-- Quitado elemento -->
        <data_naixement>7 d'abril de 1939</data_naixement>
    </director>
    <!-- Quitamos etiqueta -->
	<director>
	    <nom>Federico</nom> <!-- Cambio -->
	    <!-- Quitado elemento -->
	    <data_naixement>20 de gener del 1920 </data_naixement>
	</director>
</directors_cine>
```

Solucion 2, cambiamos el esquema para que puedan coexistir el nombre y el apellido:
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE directors_cine [
    <!ELEMENT directors_cine (director*)>
    
    <!-- Cambio estructura -->
    <!ELEMENT director (nom , llinatge, data_naixement)> 
    
    <!ELEMENT nom (#PCDATA)>
    <!ELEMENT llinatge (#PCDATA)>
    <!ELEMENT data_naixement (#PCDATA)>
]>
<directors_cine>
    <director>
        <nom>Stanley</nom>
        <llinatge>Kubrick</llinatge>
        <data_naixement>26 de juliol de 1928 </data_naixement>
    </director>
    <director>
        <nom>Francis</nom>
        <llinatge>Ford Coppola</llinatge>
        <data_naixement>7 d'abril de 1939</data_naixement>
    </director>
	<director>
	    <nom>Federico</nom>
	    <llinatge>Fellini</llinatge>
	    <data_naixement>20 de gener del 1920 </data_naixement>
	</director>
</directors_cine>
```
# Ejercicio 7
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE begudes [
    <!ELEMENT begudes (beguda)*>
    <!ELEMENT beguda ((codi | nom), preu)>
    <!ELEMENT codi (#PCDATA)>
    <!ELEMENT nom (#PCDATA)>
    <!ELEMENT preu (#PCDATA)>
]>
<begudes>
    <beguda>
        <codi>C09</codi>
        <nom>taronjada</nom>
        <preu>1,70</preu>
    </beguda>
    <beguda>
        <preu>1,05</preu>
    </beguda>
</begudes>
```
Lista:
- Sobra o el elemento `codi` o `nom` en la primera `beguda`
- Falta o el elemento `codi` o `nom` en la segunda `beguda`

Solucion:
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE begudes [
    <!ELEMENT begudes (beguda)*>
    <!ELEMENT beguda ((codi | nom), preu)>
    <!ELEMENT codi (#PCDATA)>
    <!ELEMENT nom (#PCDATA)>
    <!ELEMENT preu (#PCDATA)>
]>
<begudes>
    <beguda>
        <codi>C09</codi>
        <!-- Quitado elemento -->
        <preu>1,70</preu>
    </beguda>
    <beguda>
        <nom>taronjada</nom> <!-- Añadido elemento -->
        <preu>1,05</preu>
    </beguda>
</begudes>
```
# Ejercicio 8
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE productes [
    <!ELEMENT productes (producte)*>
    <!ELEMENT producte (identificació, nom)>
    <!ELEMENT identificació (#PCDATA | codi | id)*>
    <!ELEMENT codi (#PCDATA)>
    <!ELEMENT id (#PCDATA)>
    <!ELEMENT nom (#PCDATA)>
]>
<productes>
    <nom>martell</nom>
    <identificació>
        Són de mànec vermell i en queden 10 unitats.
        <codi>MAR264</codi>
    </identificació>
    <identificació>
        <codi>CLAU387</codi>
        <id>678984</id>
        No en queda cap al magatzem.
        <nom>clau anglesa</nom>
    </identificació>
</productes>
```
# Ejercicio 9
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE obres_art [
    <!ELEMENT obres_art (cuadro*, escultura*, foto*)>
    <!ELEMENT cuadro EMPTY>
    <!ELEMENT escultura (#PCDATA)>
    <!ELEMENT foto (#PCDATA)>
    <!ATTLIST cuadro titol ID #REQUIRED>
    <!ATTLIST cuadro autor CDATA #REQUIRED>
    <!ATTLIST escultura artista ID #REQUIRED>
    <!ATTLIST escultura material CDATA #REQUIRED>
    <!ATTLIST foto fotograf ID #REQUIRED>
    <!ATTLIST foto any CDATA #REQUIRED>
]>
<obres_art>
    <cuadro titol="Adán y Eva" autor="Alberto Durero" />
    <cuadro titol="Adán y Eva" autor="Lucas Cranach, el viejo" />
    <escultura artista="Miguel Angel" material="Marmol blanco"> David </escultura>
    <escultor artista="Rodin" material="Marmol"> El beso </escultor>
    <foto fotograf="Charles C. Ebbets" any="1932"> Almuerzo en lo alto de un rascacielos </foto>
    <foto any="1989">Plaza de Tiananmen, </foto>
</obres_art>
```
