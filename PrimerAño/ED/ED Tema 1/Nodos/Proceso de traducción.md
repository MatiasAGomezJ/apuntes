# Proceso de traducción
**La tendencia actual es hacer uso de lenguajes de alto nivel, es decir, cercanos al lenguaje humano.**

Los archivos de código fuente no contienen el lenguaje máquina que entenderá el ordenador. Por lo tanto, resultan **incomprensibles** para el **procesador**.

Para poder generar código máquina hay que hacer un proceso de **traducción** desde los mnemotécnicos (las órdenes) que contiene cada archivo a las secuencias binarias que entiende el procesador.

El proceso consta de varias partes:
- [[Compilador]]
- [[Código objeto]]
- [[Enlazador]]
	- [[Librería]]
- [[Código ejecutable]]

#### TL;DR[^1]

El **[[Código fuente]]** desarrollado por los programadores se convertirá en **código objeto** con la ayuda del **compilador**. Este ayudará a localizar los errores de sintaxis o de compilación que se encuentren en el código fuente. Con el **enlazador**, que recogerá el código objeto y las **librerías** generará el **código ejecutable**.

![](https://i.imgur.com/eu038dg.png)

[^1]: Algunos lenguajes de programacion siguen este esquema pero otros como JAVA utilizan una [[Máquina Virtual]] para transformar el código.

#ED #ProcesoTraduccion