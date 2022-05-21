# Git submodules
En esta práctica veremos como configurar **GitHub Pages** y utilizar submodulos en un repositorio de GitHub. Haremos uso el framework HTML Revealjs para testear la página.

## Configuración de GitHub Pages
Primero de todo tendremos que tener creado un repositorio en GitHub. En esta práctica no se explicará el como ya que no consiste en ello. Con el repo creado nos iremos a la configuración de este y buscaremos la opción `Pages`.

![](https://i.imgur.com/nvmU9Jj.png)

Aquí especificaremos que el código que utilize estará en `master` y guardaremos.

![](https://i.imgur.com/mR3BNV3.png)

Cuando le demos a guarda se recargará la página y nos indicará en que URL estará nuestra página. Tambien nos permitirá modificar el nombre del dominio.

![](https://i.imgur.com/NXUAUnc.png)

Cuando entremos veremos que no hay nada mas que el contenido del documento `README.md`.

![](https://i.imgur.com/KCa9u5u.png)

## Configuracion de submodulos con revealjs
A través e la terminal nos clonaremos el repo, entreremos en el y con el siguiente comando crearemos submodulo. El comando será parecido a un `git clone` y generará una carpeta con el contenido del repo. El segundo comando inicializará el submodulo.

```bash
git submodule add https://github.com/hakimel/reveal.js revealjs
git submodule update --init --recursive
```

![](https://i.imgur.com/MWfVudz.png)

Para comprobar que se ha inicializado correctamente podemos entrar en la carpeta que se ha creado y realizar `git log`, el cual debería mostrar el historial de commits del repo original.

![](https://i.imgur.com/32HuCbl.png)

![](https://i.imgur.com/QCcCKiG.png)

Saldremos de la carpeta y copiaremos el archivo `index.html` a la carpeta raíz de nuestro repo.

![](https://i.imgur.com/CEw1CEk.png)

Y modificaremos las rutas de los recursos que utiliza.

![](https://i.imgur.com/VsGVqAT.png)

![](https://i.imgur.com/I9eSnQr.png)

Para acabar subiremos los cambios a remoto.

## Final
Ahora en el repo podremos ver en la derecha una apartado que pone `GitHub Pages`. Si le damos nos llevará a otra página donde estará el link a la página que habiamos configurado anteriormente.

![](https://i.imgur.com/gAnbarJ.png)

![](https://i.imgur.com/j8NAryZ.png)

Si le damos clic a `View deployment` se abrirá nuestra página con el contenido del árchivo `index.html`.

![](https://i.imgur.com/pbSVh5J.png)