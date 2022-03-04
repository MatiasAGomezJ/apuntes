# Pràctica 3 Bloc 2

1- Si tenim el següent codi JS, Afegeix "try ... catch" per fer el maneig d'errors.
```js
var a = 4;
t = a + b;
alert(t);
```
Solucion:
```js
var a = 4;

try {
    t = a + b;
    alert(t);
} catch (error) {
    alert("Ha habido un error.\n" + error)
}
```
2- Si tenim la següent funció, afegeix una excepció "throw", per controlar que la funció accepti només les dues primeres vocals.

```js
	function demanarAE() {
		let lletra = prompt("Introdueix una una vocal (només A o B): ");
		if (lletra.toLowerCase() == "a") {
			alert ("Perfecte, has triat la A");
		}
		if (lletra.toLowerCase() == "e") {
			alert ("Perfecte has triat la E");
		}
	}
```
Solucion:
```js
function demanarAE() {
    let lletra = prompt("Introdueix una una vocal (només A o B): ");
    try {
        if (lletra.toLowerCase() == "a") {
            alert("Perfecte, has triat la A");
        } else if (lletra.toLowerCase() == "e") {
            alert("Perfecte has triat la E");
        } else {
            throw "El valor pasado no es una A ni una E";
        }
    } catch (error) {
        alert("Ha habido un error.\n" + error);
    }
}
```
3- Si tenim la següent funció (comprovar()), Explica que quin és el funcionament del control d'errors.

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
Solucion:
1. Primero de todo el programa accede a una caja de texto y guarda el valor que habia escrito.
2. Despues entra en el try...catch y empieza comprobando si el variable esta vacia, si lo está, devuelve un error con el mensaje `No s'ha introduït cap número`. 
3. A continuacion conprueba si tiene como valor `NaN` y si es así devuelve un error con el mensaje `La dada introduïda no és un número`. 
4. Lo siguiente que hace es pasar la variable a una variable de tipo numero.
5. Despues comprueba si el numero es mayor que 10  y devuelve error con el mensaje `el número introduït és massa gran`.
6.  Luego hace lo mismo si el numero es menor que 5.
Si cualquiera de esto throws saltarán todo el codigo posterior a ellos dentro del try no se ejecutaria y pasaria directamente al catch.
7. Dentro del catch simplemente hay un alert que muestra el error por pantalla.
8.	Para finalizar hay un `finally` que ejecuta el codigo que esté dentro de este, lo de dentro del bloque se ejecutará independientemente e si ha habido algún erorr o no. 

4- Crea una pàgina web que contengui un formulari amb els següents camps d'informació i després valida el formulari des de Javascript (també pots incloure atributs html, per exemple required).
-   Nom, que sigui obligatori amb atribut autofocus.
-   Correu electrònic, que sigui obligatori.
-   Telèfon, amb un control de tipus «tel». El telèfon ha de tenir 9 dígits.
-   Una contrasenya obligatòria, que tengui una longitud mínima de 6 caràcters i màxima de 10. Ha d'acabar amb dos números
-   Un botó d'enviament.

5- Crea una pàgina web que contengui un formulari amb els següents inputs i després has de fer la validació des de Javascript (pots utilitzar atributs d'HTML per ajudar a la validació).
-   Un nom que tengui com a màxim 10 caràcters de llargària i que comenci amb una lletra majúscula.
-   Un número de telèfon de 9 números exactes.
-   Una adreça de correu electrònic:
	-   nomusuari: Sense restriccions.
    -   @domini.xxx: on xxx pot ser de dues, tres o quatre lletres.
-   Ha de demanar la ciutat i el país (Aquests dos camps poden quedar en blanc).
-   També ha de demanar un número de targeta de crèdit, amb el següent patró: 5555-4444-3333-2222
-   El formulari ha de tenir un botó d'enviament per correu i un botó que permeti esborrar les dades del formulari.