Lo primero que necesitamos para no meter errores en el codigo necesitamos un ***Vocabulario***.

Saber que significa: 
- Input: inforamcion que mete el usuario
- Defect: 
- Failure: es un defecto en el codigo que se manifesta

El objetivo de los casos test es no crear defectos en el codigo

Python es iperativo porque decimos las ordenes en orden y el lenguaje lo lee en ese orden


al usar el paradigma Procedimental  no cambia como funciona el programa, cambia las variables

El debuggin es utilizar monton de casos test; cuando has encontrado un fallo poder saber de donde sale ??

*API*

Precondition

Cuando usar assert y cuando try:except 
Cuando la informacion que vas a utilzar info de cas que no has escrito usa try expect, porque puede que el archivo no este bien escrito o ni siquiera exista.
Se usa siempre que se vaya a utilizar informacion externa


Cuando quieras comprobar que una funcion reciba datos de otra que has escrito usaremos un assert, por que es un problema interno y tuyo

```python
def la_funcion_que_abre_el_fichero():
	try:
		# abre el ficher
	except e:
		# "no existe"
	else:
		# Trabajamos con la informacion del archivo
	finally:
		# cierra el archivo
```


*Programacion defensiva*


Los prcedimientos en programacion  son los que no devuelven nada