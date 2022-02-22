# 1. Definició i classificació dels llenguatges de marques. Les marques.
**IMPORTANT**:
llenguatges de marques: són aquells que combinen dins un docu ment, la informació ( text ) amb marques.

El llenguatge de marques especifica les marques possibles ( etiquetes, elements, etc. ) y les seves funcions

Els documents que es creen amb el llmm avantatge facilitat de creació i lectura. gràcies als:
- **estàndards d’emmagatzematge** definits i públics
- la **incorporació de metadades**
- la **definició de l’estructura de les dades**.

ASCII, UTF-8, etc. ) s’aconsegueix que puguin ser transportats i llegits en qualsevol lloc

llmm s’aprofitaran d'estar basats en el format de text.
avantatge: podran ser oberts i creats amb els programes d’edició de text estàndard

- –el Web– està basat totalment en els llmm
- programes d’ordinador habitualment utilitzen llmm
### Les marques
marques: sèrie de codis que s’incorporen als documents que determinen el que y com es mostrará el que hi ha adins.
`<marca> </marca>`
# 2. Nom de les dues Organitzacions desenvolupadores
Organització Internacional per a l'Estandarització (ISO, International Organization for Standardization)

W3C (World Wide Web Consortium)
# 3. Etiquetes, elements i atributs dels llenguatges de marques. Que són i exemples.
tres termes emprats per tots els llenguatges de marques, parts d'un document
- **Elements**: estructures mitjançant les quals s'organitzarà el contingut del document. Consten de:
	-  l'etiqueta d'**inici**
	-  l'etiqueta de **fi**
	-  i de tot allò que es troba entre les dues.
		-  Alguns elements no tenen contingut: elements buits i no han de dur cap etiqueta.
- **Etiqueta o tag**: text que va entre (<) i (>). Existeixen etiquetes d'inici (ex. `<nom>`) i etiquetes de fi (ex. `</ nom>`).
- **Atribut**: És un parell nom-valor dins de l'etiqueta d'inici d'un element i indiquen  propietats que poden portar associades els elements.
# 4. Elements en línia i elements en bloc de HTML. Diferències.
element de **línia**: aquell que ocupa l'espai mínim necessari horitzontal.
Un element de **bloc**:  s'inicia sempre en una nova línia i s'amplia tota l'amplada disponible.
P.ej:

Linia | Bloc
:--:|:--:
a | address
br | aside
i | div
img | footer
cite | header
q | p
## a. Elements en línia: img, a, button.
img: una imatge
- src, alt

a:  un hiperenllaç
- href

button:  un botó
- onclick
## b. Elements en bloc: llistes(ul/ol), títols (hi), p, elements semàntics.(Es tracta de saber que aquests element són d'un tipus o d'un altre, no fa falta la sintaxi).
llistes(ul/ol): una llista
- ul: desordenada
- ol: ordenada

h1-6: titol
p: paragraf
semantics: com un div, solament encaixa algo
# 5. Estructura d'un document HTML (html, head, body). Ordre dels elements i perquè serveixen.
<!**DOCTYPE** html> sirver para determinar el modo de visualización
<**html**></**html**> Son las etiquetas principales en la que dentro estará todo los datos de la pagina.
<**head**></**head**> contiene informacion sobre el documento: titulo, palabras clave para su busqueda, y otros metadatos
<**body**></**body**>  contiene el contenido que se mostrará del documento
```html
<!DOCTYPE html>
<html>
	<head>
		...
	</head>
	<body>
		...
	</body>
</html>
```
# 6. Com s'insereixen els comentaris a HTML i a CSS.
**HTML**:
- linea : `<!-- Comentario -->`
- bloc:
```hmtl
<!--
	<p> Esto no se muestra </p>
-->
```
**CSS**:
- linea : `/* Comentario */`
- bloc:
```css
/* 
Todo esto es
p {
	color: red;
}
un comentario
*/
```
# 7. Sintaxi d’un CSS.
```css
* { /* Selector */
	background-color: green; /* declaracio1; */
	color: red;				 /* propiedad2: valor2; */
}

body {
	background-color: blue;
	text-align: center;
}

main {
	margin: 10px;
}
.
.
.
/* declaracioni == propiedadi: valori */
```
# 8. Tipus de selectors (etiqueta, classes, ids, combinadors, pseudoclasses, pseudoelements).
Selectors bàsics:
- Selector universal: _*****_ { color: red; }
- Selectors de tipus o etiqueta: _**h1**_ { color: red; }
- Selectors de classe: ***.***abc { color: red; } o  p***.***abc { color: red; }
( El **primero**, todas las etiquetas de clase `abc`. En el **segundo**, todos los `p` con clase `abc` )
- Selectors Id: ***#***miid { color: red; }
- Selector descendent: ***h1 p*** { color: red; } (todos los `p` dentro de `h1`)
- Combinació de selectors:  h1#abc p.xyz { color: red; }
(Todos los `p` de clase `xyz` dentro del `h1` de id `abc`)

Selectors d'atributs: _**[title ~= carabeza]**_ { color: red; } (Todos los elementos con el atributo `title="carabeza"`)
Selectors combinadors:
- Combinador de germans adjacents: adjacent:  _**h1 + p**_ { color: red; } (el segon element segueix directament al primer i tots dos tenen el mateix element pare)
- Combinador general de germans: no adjacent:  _**h1 + p**_ { color: red; }(el segon element segueix al primer (no necessàriament de forma immediata), i els dos tenen el mateix pare.)
- Combinador de fills: _**body > p**_ { color: red; } elements que són fills directes del primer element

Pseudoclasses( hacen referencia a todo el elemento ): _**a:active**_ { color: red; }
Pseudoelements ( hacen referencia a una parte del elemento ): _**body p::first-line**_ { color: red; }

**NOTA**: se pueden poner varios separados por comas ( , )
# 9. Caixes. Tipus de posicionaments, propietats més importants per ubicar-les correctament.
Display:
- block: convierte el elemento en bloque
- inline: convierte el element en linea
- inline-block: mezcla entre bloque y linea
- none: oculta un elemento
- list-item: se comporta como una lista

Position
- static: lo natural
- relative:  relative to its normal position
- absolute: relative to the nearest positioned ancestor
- fixed: relative to the viewer, which means it always stays in the same place even if the page is scrolled
- sticky: positioned based on the user's scroll position

Propiedades:
- **margin, margin-top, margin-right, margin-bottom i margin-left**: agregan margen
- **padding, padding-top, padding-right, padding-bottom i padding-left**: agregan margen interno
- **top, bottom, left i right**
- **Propietat float**: permite al elemento colocarse en el sitio indicado dentro del padre.
- **Propietat clear**: despues de un float utilizamos un clear para mover a los elemtos abajo del elemto con float, sino se quedaria en la misma linea.
- **Propietat z-index**: permite mover elementos en el eje z ( profundidad )