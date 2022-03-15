# DTD
## 1 Sintaxis
### 1.1 Interno
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
### 1.2 Externo
#### 1.2.1 Privado
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
#### 1.2.2 Público
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

## 2 Declaración de elementos
El elemento puede ser:
### 2.1 EMPTY
Vacio en ingles
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
### 2.2 (#PCDATA)
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
### 2.3 ANY 
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