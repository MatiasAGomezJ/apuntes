# XsD
## Pa utizarlo
Hay que añadir en la raiz del xml lo sigiuente:
1. `xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"`.
2. `xsi:noNamespaceSchemaLocation="AAAA.xsd"` donde `AAAA.xsd` es el nombre donde estará el esquema. ( Tambien puede ser una URL).

### Ejemplo 1:
Sin XSD:
```xml
<cicle>	
  <nom>1r ASIX</nom>
  <modul>LLMM</modul>
</cicle>
```
Con XSD:
```xml
<cicle xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"	xsi:noNamespaceSchemaLocation="esquema_cicle.xsd">	
  <nom>1r ASIX</nom>
  <modul>LLMM</modul>
</cicle>
```
L'arxiu "esquema_cicle.xsd" contendrà la definició de l'esquema.
```xml
<?xml version="1.0" encoding="UTF-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema"> 
  <xs:element name="cicle">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="nom" type="xs:string" minOccurs="0" maxOccurs="unbounded"/> 
        <xs:element name="modul" type="xs:string" minOccurs="0" maxOccurs="unbounded"/>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
</xs:schema>
```
### Ejemplo 2
Archivo XML:
```xml
<persona  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  xsi:schemaLocation="humans.xsd">
  <nom>Joan</nom>
  <direccio>C/Sol</direccio>
</persona>
```
Esquema XSD:
```xml
<?xml version="1.0" encoding="UTF-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema"> 
  <xs:element name="persona">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="nom" type="xs:string" minOccurs="0" maxOccurs="unbounded"/> 
        <xs:element name="direccio" type="xs:string" minOccurs="0" maxOccurs="unbounded"/>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
</xs:schema>
```  

## 1. Definir un fitxer XML d'esquema
- Ha de començar amb l'etiqueta d'XML. 
-  Després, l'etiqueta `<schema>`, és l'element arrel.

Todo archivo `.xsd` **SIEMPRE** tiene estas líneas:
```xml
<?xml version="1.0" encoding="UTF-8" ?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
	·
	·
	·
</xs:schema>
```

## 2. Declarar elements ( Lo tocho de los apuntes )
Un elemento puede ser simple o complejo (esto se ve mas adelante) pero **TODOS** se escribren de la misma manera.
```xml
<xs:element
  name="nomElement"
  type="xs:integer"
  minOccurs="num_min"
  maxOccurs="num_max"
  fixed="valorElement"
  default="valorXdefecte" >
</xs:element>  
```
També ho podem escriure: 
```xml
<xs:element
  name="nomElement"
  type="xs:integer"
  minOccurs="num_min"
  maxOccurs="num_max"
  fixed="valorElement"
  default="valorXdefecte" /> 
```
> Se pueden escribir en una línea pero lo he puesto en diferentes para que se pueda leer.


Donde:  
- **name**: És el nom de l'element. 
- **type**: Defineix el tipus d'element. Poden ser per exemple:  
    xs:boolean  
    xs:date  
    xs:decimal  
    xs:integer  
    xs:string  
- **minOccurs i maxOccurs** (opcionals): Indiquen el mínim i màxim (respectivament) d'ocurrències de l'element. 
	- Valores **minOccurs**: De 0 a ♾. Por defecto 1.
	- Valores **maxOccurs**: De 1 a ♾. Si queremos infinitos pondremos **unbounded**.
- **fixed** (opcional): Especifica un valor fix per l'element.  
- **default** (opcional): Especifica un valor per defecte per l'element.  
  
> Nota:
> Els valors **fixed** i **default** dels elements només s'afegeixen al document XML si l'element està present.
> Els elements amb un valor **fixed**, poden estar buits. Si no són buits el seu contingut ha de coincidir amb el definit a l'atribut **fixed**.
### 2.1. Elements simples
Són elements que només poden contenir text, no poden contenir altres elements ni **atributs**.

Els tipus de dades poden ser:
-   **Tipus de dades primitius:** string, boolean, decimal, float, double, data-hora (duration, dateTime, time, date, gYearMonth, etc.), hexBinary, anyURI, etc.
-   **Tipus de dades no primitius:**  normalizedString, token, language, IDREF, Name, integer, long, etc.

Ejemplo:
```xml
XSD:  
<xs:element name="titol" type="xs:string"/>  
<xs:element name="capitols" type="xs:integer"/>  
  
XML:
<titol>La dama de las camelias</titol>  
<capitols>10</capitols>
```
#### Restriccions
Les restriccions s'utilitzen per definir els valors que són vàlids als elements i atributs XML. 
```xml
<xs:simpleType name=”nom”>
  <xs:restriction base="tipus">
    ...definicions de les restriccions...
  <xs:restriction>
</xs:simpleType>
```
En los ejemplo de las siguientes restricciones se supone que se ha escrito dentro del ejemplo de arriba.
##### Rango de numeros
S'utilitza en els tipus de dades numèriques i data/hora.

Paraules clau: **minInclusive**, **maxInclusive**, **minExclusive**, **maxExclusive**. Defineixen el mínim i màxim dels números permesos, depenent si es volen incloure els límits.
```xml
<xs:restriction base="xs:integer">
  <xs:minInclusive value="0"/>
  <xs:maxInclusive value="100"/>
</xs:restriction>
```
##### Digits
S'utilitza en tots els tipus de dades.

Paraula clau: **totalDigits** que defineix el número màxim de dígits permesos.
```xml
<xs:restriction base="xs:integer">
  <xs:totalDigits value="9"/>
</xs:restriction>
```
##### Lista de valores
S'utilitza en tots els tipus de dades.

Paraula clau: **enumeration** que defineix una llista de valors permesos a l'element.
```xml
<xs:restriction base="xs:string">
  <xs:enumeration value="Vermell"/>
  <xs:enumeration value="Verd"/>
  <xs:enumeration value="Grog"/>
  <xs:enumeration value="Blau"/>
</xs:restriction>
```
##### Longitud
S'utilitza en tipus de dates de text.
Paraula clau: **length**, **minLength**, **maxLength** que defineixen el número exacte de caràcters permesos, o el mínim i màxim d'ells.
```xml
<xs:restriction base="xs:string">
  <xs:length value="25"/>
</xs:restriction>
```
```xml
<xs:restriction base="xs:string">
  <xs:minLength value="1"/>
  <xs:maxLength value="25"/>
</xs:restriction>
```
##### Plantilla de carácteres
S'utilitza en tipus de dades de text.
Paraula clau: **pattern**	 que especifica un patró o expressió regular que ha de complir el contingut de l'element.
```xml
<xs:restriction base="xs:string">
  <xs:pattern value="[A-Z][A-Za-z][A-Za-z]"/>
</xs:restriction>
```
```xml
<xs:restriction base="xs:string">  
  <xs:pattern value="Home|Dona"/>  
</xs:restriction>
```
Basicamenta se escribe una expresión regular dentro del atributo.
##### Restricciones a los espacios en blanco
Especifica com s'ha de tractar els possibles espais en blanc, les tabulacions, els salts de línia i els retorns de carro que puguin aparèixer.
Paraula clau: **whiteSpace**.
```xml
<xs:restriction base="xs:string">  
  <xs:whiteSpace value="preserve"/>  
</xs:restriction>
```
Donde:  
**preserve**: Les dades no se modifiquen, queden tal i com estan escrits.  
**replace**: Els tabuladors, salts de línia i retorn de carro són substituïts per espais.  
**collapse**: Fa el mateix que "replace", però a més substitueix espais múltiples per un només.
### 2.2. Elements complexos
Un element complex és el que pot contenir altres elements i/o atributs.

#### Consideracions
##### Un element complex pot estar buit
Pot no contenir ni elements ni text, **però si algun atribut**. Si no contenen atributs, es poden declarar com a **elements simples**.
```xml
XSD:
<xs:element name="autor" type="buit_tipus_cadena">  
  <xs:complexType name="buit_tipus_cadena">  
	<xs:atribute name="nom" type="xs:string"/>
  </xs:complexType>  
</xs:element>  
  
XML:  
<autor nom="Almudena Grandes"/>
```
##### Un element complex pot contenir altres elements
Ho indicam amb "mixed".
```xml
XSD:
<xs:element name="confirmacioComanda">  
  <xs:complexType mixed="true">  
    <xs:sequence>  
      <xs:element name="intro" type="xs:string"/>  
      <xs:element name="nom" type="xs:string"/>  
      <xs:element name="data" type="xs:string"/>  
      <xs:element name="comanda" type="xs:string"/>  
    <xs:sequence>  
  </xs:complexType>  
</xs:element>  
  
XML:
<confimacioComanda>  
  <intro>Per:</intro>  
  <nom>Joan Pérez</nom>  
  Confirmació amb data de <data>24-01-2020</data> que s'ha rebut la comanda <comanda>aspirador</comanda>.   
</confimacioComanda>
```
##### Formas de especifiar subelementos
Hay 3.
###### Sequence
Serveix per especificar l'**ordre en el que obligatòriament han d'aparèixer** els elements fill d'un element.
```xml
XSD:
<xs:element name="persona">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="Primer_llinatge" type="xs:string"/>  
      <xs:element name="Segon_llinatge" type="xs:string"/>  
	</xs:sequence>  
  </xs:complexType>  
</xs:element>  
  
XML:
<persona>  
  <primer_llinatge>López</primer_llinatge>  
  <segon_llinatge>Sureda</segon_llinatge>  
</persona>
```
###### Choice
Serveix per especificar que **només es permet escriure un dels element fills**.
```xml
XSD:
<xs:element name="persona">  
  <xs:complexType>  
    <xs:choice>  
      <xs:element name="nom" type="xs:string"/>  
      <xs:element name="llinatge" type="xs:string"/>  
    </xs:choice>  
  </xs:complexType>  
</xs:element>  
  
XML:
<!--Validació correcta-->
<persona>
  <nom>Aina</nom>
</persona>

<!--Validació correcta-->
<persona>  
  <llinatge>Gómez</llinatge>  
</persona>  
```
###### All
Serveix per indicar que els elements fills d'un element **poden aparèixer en qualsevol ordre**.
```xml
XSD:
<xs:element name="ciutat">
  <xs:complexType>
    <xs:all>
      <xs:element name="nom" type="xs:string"/>
      <xs:element name="pais" type="xs:string"/>
    </xs:all>
  </xs:complexType>
</xs:element>

XML:
<!--Validació correcta-->
<ciutat>
  <nom>Barcelona</nom>
  <pais>España</pais>
</ciutat>

<!--Validació correcta-->
<ciutat>
  <pais>Alemaña</pais>
  <nom>Berlín</nom>
</ciutat>
```

### 2.3. Declarar d'atributs
Solo puede tener atributos los **elementos complejos**.

S'han de declarar just abans de tancar l'etiqueta `xs:complexType`.

Poden ser opcionals i poden tenir un valor assignat per defecte.

```xml
<xs:attribute name="nom atribut" type="tipus atribut" use="valor" default="valor" fixed="valor"/>
```

Donde: 
- **name**: Indica el nom de l'atribut.
- **type**: Indica el tipus de dada que emmagatzemarà l'atribut.
- **use** (opcional): Indica si l'existència de l'atribut és opcional (optional), obligatòria (required) o prohibida (prohibited). Por defecte opcional.
- **default** (opcional): És el valor que prendrà l'element quan es processa si en el document XML no ha rebut cap valor. **Només es pot emprar amb tipus de dada de text**.
- **fixed** (opcional): Indica l'únic valor que pot contenir l'element en el document XML. **Només es pot emprar amb tipus de dades de text**.
```xml
XSD:
<xs:element name="llinatge">
  <xs:complexType>
    <xs:attribute name="nacionalitat" type="xs:string" use="required"/>   
  </xs:complexType>
</xs:element>
  
XML:
<llinatge nacionalitat="Espanyola">Servera</llinatge>
```