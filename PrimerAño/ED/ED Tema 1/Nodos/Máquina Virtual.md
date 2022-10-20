# Máquina virtual
El concepto de **Máquina virtual** surge con el objetivo de facilitar el desarrollo de compiladores que generan código para **diferentes procesadores**.

La compilación consta de dos fases:
- La primera parte del código fuente en un lenguaje intermedio obteniendo un programa equivalente con un menor nivel de abstracción que el original y que no puede ser directamente ejecutado.
- La segunda fase traduce el lenguaje intermedio a un [[Lenguaje máquina]].

El objetivo es que elcódigo de la  **primera fase**, el código intermedio, sea **común para cualquier procesador**, y que el código generado en la  **segunda fase** sea el  **específico para cada procesador **.

La traducción del lenguaje intermedio al lenguaje máquina no se suele hacer mediante un [[Compilador]] sino mediante un intérprete.

![](https://i.imgur.com/wlgBHZq.png)
![](https://i.imgur.com/3XO7gha.png)

La máquina virtual Java se sitúa en un **nivel superior al hardware** sobre el que se desea ejecutar la aplicación y actúa como un puente entre el código a ejecutar y el sistema. La JVM será la encargada, al ejecutar la aplicación, de convertir el código de bytes a código nativo de la plataforma física.

![](https://i.imgur.com/Cy28Xdg.png)

**Ventaja**: la portabilidad de la aplicación a diferentes plataformas con el único requerimiento de disponer de la JVM para el sistema correspondiente


## Notas / Cosas que me ha especificado el profe
Una maquina virtual es utilizada porque sino es necesario crear el codigo objeto para cada S.O.

Al usar la M.V. podemos crearlo el codigo objeto sin problemas y despues usar un interprete ( la maquina virtual ) para cada S.O.

#ED #ProcesoTraduccion 