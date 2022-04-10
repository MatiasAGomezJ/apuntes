# XsD
## Pa utizarlo
Hay que añadir en la raiz del xml lo sigiuente
1. `xmlns:xsi="<http://www.w3.org/2001/XMLSchema-instance>"`
2. `xsi:noNamespaceSchemaLocation="AAAA.xsd"` donde `AAAA.xsd` es el nombre donde estará el esquema. ( Tambien puede ser una URL)

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
<cicle xmlns:xsi="<http://www.w3.org/2001/XMLSchema-instance>"	xsi:noNamespaceSchemaLocation="esquema_cicle.xsd">	
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
<xs:element name="nomElement"  type="xs:integer"  minOccurs="num_min"  maxOccurs="num_max"  fixed="valorElement"   default="valorXdefecte">  
</xs:element>  
```
També ho podem escriure: 
```xml
<xs:element name="nomElement"  type="xs:integer"  minOccurs="num_min"  maxOccurs="num_max"  fixed="valorElement"   default="valorXdefecte"/>
```
Donde:  
- **name**: És el nom de l'element. 
- **type**: Defineix el tipus d'element. Poden ser per exemple:  
    - xs:boolean  
    xs:date  
    xs:decimal  
    xs:integer  
    xs:string  
- **minOccurs i maxOccurs** (opcionals): Indiquen el mínim i màxim (respectivament) d'ocurrències de l'element. 
	- Valores **minOccurs**: De 0 a ♾. Por defecto 1.
	- Valores **maxOccurs**: De 1 a ♾. Si queremos infinitos pondremos **unbounded**
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


##### Restriccions
###### Rango de numeros
###### Digits
###### Lista de valores
###### Longitud
###### Plantilla de carácteres
###### Restricciones a los espacios en blanco
### 2.2. Elements complexos
### 2.3. Declarar d'atributs