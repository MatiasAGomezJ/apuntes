## Pràctica 1 Bloc 1

**Requisits d'entrega:** 

-   El fitxer d'entrega ha d'estar en format zip o rar (format comprimit).

**Ha de contenir:**

-   Els arxius corresponents als projectes (codi html, [css](https://aulavirtual.caib.es/c07015884/mod/book/view.php?id=8247 "CSS"), imatges, etc.)
-   Un document en format PDF que contengui les respostes a les qüestions més teòriques.

**Qualificació:**

-   La qualificació es calcularà en funció dels criteris de la rúbrica.

### **Enunciat:**

**1- Per a cada fragment de document (XML i HTML), indica quins són els elements, les etiquetes i els atributs. Dibuixa l'arbre d'elements, i escriu les etiquetes i els atributs en llista. (Aquesta pregunta explica-la dins d'un arxiu PDF).**
```html
<noticies>  
   <noticia>  
      <lloc>Inca</lloc>  
      <data>20/09/2021</data>  
      <descripcio>I Festival de música acústica</descripcio>  
      <autor>P.B.</autor>  
   </noticia>  
   <noticia>  
      <lloc>Palma</lloc>  
      <data>10/09/2021</data>  
      <descripcio>Atracament a la plaça Major</descripcio>  
      <autor>A.A</autor>  
   </noticia>  
<noticies>
```
```html
<empleats>  
    <empleat id="1">  
        <nom>Miquel</nom>  
        <llinatge>Mesquida</llinatge>  
        <categoria>Administració</categoria>  
    </empleat>  
    <empleat id="2">  
        <nom>Mercedes</nom>  
        <llinatge>Ruíz</llinatge>  
        <categoria>Programador</categoria>  
    </empleat>  
</empleats>
```
```html
<!--DOCTYPE html-->  
<html>  
  <head>  
    <meta charset="UTF-8" />  
    <title>Aquest és el títol del head de la pàgina</title>  
  </head>  
  <body>  
    <h2>Tema de la pàgina</h2>  
    <div>  
       <h3>Un subtítol de la pàgina</h3>  
       <p>Un paràgraf de la pàgina</p>  
    </div>  
    <img src="logo.png">  
    <address>Som l'autor de la pàgina. <p>La meva adreça de correu electrònic és yyy@yyy.es<p></address>  
   </body>  
</html>
```
**2- Codifica en codi html una pàgina web (tema lliure).** **Ha de complir els següents requisits:**

- La primera pàgina s'anomenarà "index.html".
- Ha de tenir un mínim de 4 pàgines web (inclosa "index.html") de creació pròpia, enllaçades entre si, partint totes de "index.html".
- Organitza l'estructura a partir d'etiquetes semàntiques de HTML5 (`<footer>`, `<nav>`, `<article>`, `<header>`...).
- Ha de tenir títol i/o logotip (imatge). (les dues coses han de fer referència al tema triat).

- Has d'afegir àudio i un vídeo dins alguna de les pàgines.

- Has de posar com a mínim 2 enllaços externs.

- Ha d'incloure:
	- Una llista
	- Una taula
    - Algun element de citació.

- Has d'emprar encapçalaments: h1-h6.

- La pàgina ha de tenir un títol al "head", totalment descriptiu.

- Has de posar comentaris per fer la lectura i comprensió del codi més òptima.

- Empra els [CSS](https://aulavirtual.caib.es/c07015884/mod/book/view.php?id=8247 "CSS") com arxius independents enllaçats amb els arxius HTML. En quant al [CSS](https://aulavirtual.caib.es/c07015884/mod/book/view.php?id=8247 "CSS"):
	- Has d'emprar una gama de colors homogènia, per tenir una visualització correcte.
    - Enllaços de color diferents del que hi ha per defecte.
    - La grandària de la font ha de ser adequada al disseny.
    - Has d'emprar selectors d'etiqueta, de classe, i alguna pseudoclasse.

_Important:_  

-   _Les etiquetes `<title>` `</title>` i `<meta name="description" content="..."/>` són molt importants per aportar informació de cara als navegadors que visualitzaran la pàgina. Les llargàries recomanades són: Title: 8 paraules (aprox.), i Description: 24 paraules (aprox.)._
-   _Les imatges han d'ocupar el mínim possible i tenir una visualització perfecte._ 
-   _Enrecordat d'especificar la codificació de caràcters, encoding,...(UTF8)._
-   _Emprar una estructura correcta de directoris (html al document arrel, una carpeta o directori per les imatges, una carpeta pels fulls d'estil), i pensau que les rutes incloses al codi html han de ser relatives perquè funcioni)._

	-   _*Ruta absoluta: Comença amb la lletra de la unitat seguida de dos punts. Per exemple: C:\carpeta1\carpeta2\arxiu1.doc._
	-   _*Ruta relativa: S'indica la ruta a partir d'on s'està en el moment situat, no inclou el directori arrel. Per exemple, si ens trobam a C:\carpeta1 i volem accedir a l'arxiu1.doc que està a la carpeta2, seria carpeta2\arxiu1.doc._

-   _No usar JavaScript! (encara no!!, pot penalitzar inclús). Tot és HTML i [CSS](https://aulavirtual.caib.es/c07015884/mod/book/view.php?id=8247 "CSS"), tot és estàtic no hi ha cap moviment ni cap animació (encara no!!)._