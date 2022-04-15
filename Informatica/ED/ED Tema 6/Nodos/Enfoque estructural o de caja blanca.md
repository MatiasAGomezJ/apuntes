# Enfoque estructural o de caja blanca
Las pruebas de **caja blanca** se centran en la implementación de los programas para escoger los casos de prueba. Lo ideal sería buscar casos de prueba que recorrieran todos los caminos posibles del flujo de control del programa. Estas pruebas **se centran en la estructura interna del programa, <ins>analizando todos los caminos de ejecución</ins>**.

Las pruebas se llevarán a cabo con datos que garanticen que han tenido lugar todas las posibles combinaciones. Para decidir qué valores tendrán que tomar estos datos es necesario saber cómo se ha desarrollado el código, buscando que no quede ningún rincón sin revisar. <ins>Al menos se pasa una vez por cada camino del programa</ins>.

![](https://i.imgur.com/2GV34BG.png)