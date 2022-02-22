Creamos una rama `$ git branch matias`
Entrar en la rama `$ git checkout matias`

### Local
`git fetch origin` (Trae los ultimos cmbies sin aplicarlos???)

`git checkout -b matias origin/matias`
`git merge matias`

### En github
`git chekout master`
`git merge --no--ff matias`
`git push origin master`

### Lo siguiente
Hecho esto para actualizar los datos en otro ordenador utilizaremos el siguiente comando
```a
	 $ git pull
```
Según entiendo esto traera todas las ramas y archivos creados y modificados de ellas