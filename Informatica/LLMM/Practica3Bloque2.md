# Pràctica 3 Bloc 2

1. Si tenim el següent codi JS, Afegeix "try ... catch" per fer el maneig d'errors.
```js
var a = 4;
t = a + b;
alert(t);
```

2.  Si tenim la següent funció, afegeix una excepció "throw", per controlar que la funció accepti només les dues primeres vocals.

```js
function demanarAE() {
	let lletra = prompt("Introdueix una una vocal (només A o B): ");
	if (lletra.toLowerCase() == "a") {
		alert ("Perfecte, has triat la A");
	}
	if lletra.toLowerCase() == "e") {
		alert ("Perfecte has triat la E");
	}
 }
 ```

3. Si tenim la següent funció (comprovar()), Explica que quin és el funcionament del control d'errors.

```js
function comprovar() {
	var num = document.getElementById("x").value;
	try {
		if (num == "") {
			throw "No s'ha introduït cap número";
		}
		if (isNaN(num)) {
			throw "La dada introduïda no és un número";
		}
		num = Number(num);
		if (num > 10) {
			throw "el número introduït és massa gran";
		}
		if (num < 5) { 
			throw "el número introduït és massa petit";
		}
	} catch (err) {
		alert("Error: " + err + ".");
	} finally {
		document.getElementById("x").value = " ";
	}
}
```

4. Crea una pàgina web que contengui un formulari amb els següents camps d'informació i després valida el formulari des de Javascript (també pots incloure atributs html, per exemple required).
	-   Nom, que sigui obligatori amb atribut autofocus.
	-   Correu electrònic, que sigui obligatori.
	-   Telèfon, amb un control de tipus «tel». El telèfon ha de tenir 9 dígits.
	-   Una contrasenya obligatòria, que tengui una longitud mínima de 6 caràcters i màxima de 10. Ha d'acabar amb dos números
	-   Un botó d'enviament.

5. Crea una pàgina web que contengui un formulari amb els següents inputs i després has de fer la validació des de Javascript (pots utilitzar atributs d'HTML per ajudar a la validació).
	-   Un nom que tengui com a màxim 10 caràcters de llargària i que comenci amb una lletra majúscula.
	-   Un número de telèfon de 9 números exactes.
	-   Una adreça de correu electrònic:
    	-   nomusuari: Sense restriccions.
    	-   @domini.xxx: on xxx pot ser de dues, tres o quatre lletres.
	-   Ha de demanar la ciutat i el país (Aquests dos camps poden quedar en blanc).
	-   També ha de demanar un número de targeta de crèdit, amb el següent patró: 5555-4444-3333-2222
	-   El formulari ha de tenir un botó d'enviament per correu i un botó que permeti esborrar les dades del formulari.