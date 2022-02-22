# INTRODUCCIÓ ALS LLENGUATGES DE MARQUES
## 1. Introducció als llenguatges de marques
**ordinador**: màquina electrònica que rep i processa dades per convertir-les en informació útil
**dades**:  són representacions d'aspectes del món real i se solen recollir amb el objectiu de traballar amb elles
### Característiques de les dades
**A qui van dirigides**: les dades tindran una forma o una altra en funció del destinatari:
1. A les persones: estructura concreta, formats determinats
2. Als programes: no necessiten informació sobre com s’han de representar, serà necessari que siguin fàcilment identificables, quedi clar de quin tipus són y que signifiquen

**La possibilitat de reutilitzar**: mportant qu les dades puguin ser reutilitzades fàcilment

**Que es puguin compartir**: necessari emmagatzemar-les correctament
### Emmagatzematge de dades en ordinadors
informació sempre es representa mitjançant uns i zeros, binari.
a llavors es necessari un proces de conversió

En els ordinadors les dades s’organitzen de dues maneres:
###### Dades binàries
manera natural d’emmagatzenament en ordinadors

característiques:
- optimitzades per ocupar només l’espai necessari
- Els ordinadors les llegeixen fàcilment.
- Poden tenir estructura
- És relativament fàcil afegir-hi metadades
- disponibles immediatament per fer càlculs numèrics

Si un programa vol emprar les dades binàries directament, necessitarà conèixer la mida en bits i com s'emmagatzema la informació.

**PROBLEMA**:
estan pensades per ser llegides per màquines
###### Dades de text
els humans ja ho entenem

**AMPLICACIO**, component mes petit:
- Binari ▶▶ bit
- Text ▶▶ caràcter

fitxers de text emmagatzemen la informació lletra per lletra.

Per a un ordinador no hiha gaire diferenia entre text o binari, ja que el text esta emmagazemat en binari.

**AMPLIACIO**: es necesari que existeixi un estandard on s’associa un valor numèric a cada un dels caràcters
## 1.1. Definició i classificació dels llenguatges de marques
**IMPORTANT**:
llenguatges de marques: són aquells que combinen dins un docu ment, la informació ( text ) amb marques.

El llenguatge de marques especifica les marques possibles ( etiquetes, elements, etc. ) y les seves funcions

Els documents que es creen amb el llmm avantatge facilitat de creació i lectura. gràcies als **estàndards d’emmagatzematge** definits i públics, a la **incorporació de metadades** i a la **definició de l’estructura de les dades**.

ASCII, UTF-8, etc. ) s’aconsegueix que puguin ser transportats i llegits en qualsevol lloc

llmm s’aprofitaran d'estar basats en el format de text.
avantatge: podran ser oberts i creats amb els programes d’edició de text estàndard

- –el Web– està basat totalment en els llmm
- programes d’ordinador habitualment utilitzen llmm
### Les marques
marques: sèrie de codis que s’incorporen als documents que determinen que es mostrará el que hi ha adins
`<marca> </marca>`
### Aparició i evolució dels llenguatges de marques
paso de la historia bro
directo a las misiones
### Característiques dels llenguatges de marques
**Característiques**:
- text pla
- utilitzen metadades.
- fàcils d’interpretar i processar
- fàcils de crear i representar dades diverses
- aplicacions d’Internet i programes ho fan servir

**Avantatges**:
- Es poden interpretar directament
- independents de la plataforma
- fàcils de crear i de modificar
- el proces de les dades es facil degut a l'estructura.
### Classificació dels llenguatges de marques
1. Llenguatges descriptius o semàntics: Orientats a descriure l’estructura de les dades que conté.
Es descriu quina estructura té el document ignorant com serà representada
**XML**

![](https://i.imgur.com/oTDujzi.png)

2. Llenguatges procedimentals i de presentació: Orientats a especificar com s’ha de representar la informació. 
S'indica com s’ha de fer la presentació de les dades
**HTML**

![](https://i.imgur.com/KxmIZS7.png)

**AMPLIACIO**:
regles de com se estructuren les marques, si no es seguiex es pot arribar a crear malinterpretacions. necesari fer-ho correctament

### Utilització de llenguatges de marques en entorns web
pàgina web, composta per **informació**, **hiperenllaços**, **dades d'estil** per especificar com ha de visualitzar-se, **aplicacions embegudes** per fer-la interactiva.

El contingut de la pàgina pot ser:
- Predeterminat, Estatica
- Generat al moment, Dinamica

**W3C** establir directives amb l'objectiu de:
- normalitzar el disseny
- facilitar i simplificar la visualització i interpretació del contingut.
## 1.2. Organitzacions desenvolupadores
s'han encarregat:
- Organització Internacional per a l'Estandardització (ISO, International Organization for Standardization)
- W3C (World Wide Web Consortium)

Como ya he dit, paso de la historia
##  1.3. Etiquetes, elements i atributs dels llenguatges de marques
tres termes emprats per tots els llenguatges de marques, parts d'un document
- Elements: estructures mitjançant les quals s'organitzarà el contingut del document. Consten de:
	-  l'etiqueta d'inici
	-  l'etiqueta de fi
	-  i de tot allò que es troba entre les dues.
		-  Alguns elements no tenen contingut: elements buits i no han de dur cap etiqueta.
- Etiqueta o tag: text que va entre (<) i (>). Existeixen etiquetes d'inici (ex. `<nom>`) i etiquetes de fi (ex. `</ nom>`).
- Atribut: És un parell nom-valor dins de l'etiqueta d'inici d'un element i indiquen  propietats que poden portar associades els elements.
### Exemples
Exemple amb codi HTML:
```html
<html>
	<head>
		<title>Document</title>
	</head>
	<body>
		<h1>Exemple</h1>
	</body>
</html>
```
On tenim:
- Un element pare `<html>`, que té 2 elements fills `<head>`, `<body>`. L'element `<head>` té un element fill `<title>` sense fills. L'element fill `<body>` que té un element fill `<h1>`.
- Les etiquetes que són totes les paraules que estan entre els símbols < >.
- No hi ha atributs en aquest exemple.

Exemple amb codi XML:
```xml
<adreça>
	<client>
		<nom> Maria </nom>
		<llinatges> Más López </llinatges>
		<carrer> Dels tarongers, 12 </carrer>
		<provincia ciutat="Palma de Mallorca"> Illes Balears</provincia>
		<codi_postal> 07002 </codi_postal>
	</client>
</adreça>
```
On tenim:
- Un element pare `<adreça>`, que conté 1 element fill `<client>`. L'element `<client>` té 5 elements fills: `<nom>`, `<llinatges>`, `<carrer>`, `<provincia>` i `<codi_postal>`.
- Les etiquetes que són totes les paraules que estan entre els símbols < >.
- Un atribut, que està dins l'element `<provincia>` i que és ciutat.