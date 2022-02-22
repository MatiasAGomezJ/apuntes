# Lenguajes de 2ª generación
El segundo tipo de [[Lenguaje de programación]] son los **lenguajes de segunda generación o lenguajes de ensamblador**.

Es primer lenguaje de programación que utiliza códigos **mnemotécnicos** para indicar a la máquina las operaciones que debe llevar a cabo. Estas operaciones, muy básicas, han sido diseñadas a partir del conocimiento de la estructura interna de la propia máquina.

00010100110 011 101 | SUMA A0 3 5
-- | --
Sumar 3 + 5 y guardar el resultado en un registro concreto | Sumar 3 + 5 y guardar el resultado en un registro concreto

**Cada instrucción en lenguaje ensamblador corresponde a una instrucción en lenguaje máquina**. Estos tipos de lenguajes **dependen totalmente del procesador** que utilice la máquina, por eso se dice que están orientados a las máquinas.

A partir del código escrito en lenguaje ensamblador, el programa traductor (ensamblador) lo convierte en código en un [[Lenguaje de 1ª generación]], que será interpretado por la máquina.

![](https://i.imgur.com/i6zib98.png)

En general se utiliza este tipo de lenguajes para **programar controladores (drivers) o aplicaciones de tiempo real**, ya que requiere un uso muy **eficiente** de la velocidad y de la memoria.

**Ventajas** de los lenguajes de primera y segunda generación:
- Permiten escribir programas muy optimizados que aprovechan al máximo el hardware disponible.
- Permiten al programador especificar exactamente qué instrucciones quiere que se ejecuten.

**inconvenientes**:
- Los programas escritos en lenguajes de bajo nivel **están completamente ligados al hardware** donde se ejecutarán y **no se pueden trasladar fácilmente** a otros sistemas con un hardware diferente.
- Hay que conocer a fondo la arquitectura del sistema y del procesador para escribir buenos programas.
- No permiten expresar de forma directa conceptos habituales a nivel de algoritmo.
- Son difíciles de codificar, documentar y mantener.

#ED