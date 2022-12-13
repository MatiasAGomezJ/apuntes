# Cookies
4KB de tamaño
Se guardan hasta que alcanze su su fecha de caducidad
Sre envian como cabeceras:
```http
Set-Cookie: fontSize=3; expires=Tuesday, 6-Jan-2016 17:50; path=/; domain=.ejemplo.com; HttpSecure; httpOnly
```
1. name. R
2. value. O
3. expires. O
4. path. O
5. domain. O
6. secure. O
7. HttpOnly. O

Es recomendable proporcionar al menos: name, value, exipres y path.
La fecha de *expires* tiene que estar en formato UNIX.
Para crear una cookie
```php
setcookie(“fontSize”, 3, time() + 60 *60 * 24 * 365, “/”, “.ejemplo.com”, false, true);
```

Las cookies recibidas en el servidor se guardan el la variable superglobal `$_COOKIE`. Aquí estan guardadas todas las cookies enviadas por el navegador en la petición actual.

# Sesiones
SID, único.
php envia una cookie con el SID
Cuando el navegador solicita una url, envia la cookie llamada PHPSESSID al servidor, permitiendo recuperar lso datos de la sesión.
Para crear una sesión utilizaremos: `session_start();`
Al igual que `setcookie()`, debe ser llamada antes de enviar nada al navegador.
La sesiones se guardan en `$_SESSION`.
Las cookies y las sesiones se guardan temporalmente en el servidor, la ubicacion de dicha ubicacion esta guardada en la directiva **session.save_path**.

La sesion se pierde cuando se sale del navegador ya que el campo de expire esta a 0. Se puede destruir manualmente con `sesion_destroy()`.

**Conclusión**: para eliminar una sesión tanto en el servidor como en el navegador, además, debemos destruir la cookie de sesión. 
```php
if (isset ($_COOKIE[session_name()] )) { 
	setcookie( session_name(), “”, time()-3600, ”/”);
	unset($_COOKIE[session_name()]);
}
session_unset(); // o bien $_SESSION = array();
session_destroy();
```
NOTA: session_name() devuelve el nombre de la cookie de sesión (el predeterminado es PHPSESSID).