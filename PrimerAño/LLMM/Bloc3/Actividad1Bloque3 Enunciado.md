1- Escriu un document XML (ciutats.xml) que emmagatzemi la següent informació.

Nota: el continent al que pertany un país s'ha de representar mitjançant un atribut, la resta de informació, no.

(No és necessari de crear el DTD per validar-ho, però si comprovar que estigui ben format)

|    Nom     |   País   | Continent |
| :--------: | :------: | :-------: |
| Nova Delhi |  India   |   Àsia    |
|   Lisboa   | Portugal |  Europa   |
|  El Cairo  |  Egipte  |  Àfrica   |

2- Escriu un document XML (historics.xml) que emmagatzemi la següent informació.

Nota: La descripció de cada fet històric, s'ha de representar mitjançant un atribut, la resta de informació no.

(No és necessari de crear el DTD per validar-ho, però si comprovar que estigui ben format)

|      Descripció Data      | Dia | Mes | Any  |
| :-----------------------: | :-: | :-: | :--: |
| IMB posa al mercat el PC. | 12  |  8  | 1981 |
|     Se funda Google.      |  4  |  9  | 1998 |
|    Se funda Facebook.     |  4  |  2  | 2004 |

3- Crear un document XML anomenat "ticket.xml" que mostri la següent informació:
Dades dels ticket:

-   codi (que ha de ser un atribut del ticket).
-   Data i hora.
-   Preu Total. Aquest preu es calcularà a partir de:
    -   Preu sense IVA.
    -   % IVA.
    -   Preu amb IVA.
-   Forma de pagament. Que ha de indicar:
    -   Tipus de pagament (efectiu/targeta).
    -   Número de la targeta (en cas de que sigui pagament amb targeta).
    -   Nom del client.

4- Comprova amb XML Copy Editor, si el següent document XML "numeros.xml" està be format i si és vàlid.

Explica quins són els errors i mostra el codi corregit.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE numeros [
    <!ELEMENT numeros (#PCDATA)>
]>
<numeros>
    <numero>10</numero>
</numeros>
```

5- Comprova amb XML Copy Editor, si el següent document XML "aficions.xml", està be format i si és vàlid.

Explica quins són els errors i mostra el codi corregit.

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

6- Comprova amb XML Copy Editor, si el següent document XML "directors_cine.xml" està be format i si és vàlid.

Explica quins són els errors i mostra el codi corregit. (pots fer captures)

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
        <nom>Francis</nombre>
        <llinatge>Ford Coppola</llinatge>
        <data_naixement>7 d'abril de 1939</data_naixement>
    </director>
</directors_cine>
<director>
    <nom>Federico</nombre>
    <llinatge>Fellini</llinatge>
    <data_naixement>20 de gener del 1920 </data_naixement>
</director>
</directors_cine>
```

7- Els següent document XML "begudes.xml", està be format, però no és vàlid, realitza els canvis necessaris sense modificar la DTD interna.

Explica quins són els errors i mostra el codi corregit.

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

8- El següent document XML "productes.xml" està ben format, però no és vàlid. Realitza els canvis necessaris per que sigui vàlid sense modificar la DTD interna.

Indica quins són els errors i mostra el codi corregit.

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

9- El següent document XML "art.xml" està ben format, però no és vàlid. Realitza els canvis necessaris per que sigui vàlid sense modificar la DTD interna.

Indica quins són els errors i mostra el codi corregit.

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
