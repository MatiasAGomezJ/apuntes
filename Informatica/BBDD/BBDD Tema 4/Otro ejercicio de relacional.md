Asociativas:
Tendran dos opciones como clave principal
- La original o artificial que hemos creado.
- Las dos claves de las entidades que es asociativa, habrá que explicar que se pueden ser las DOS y que son foreign keys. En este habrá que borrar la clave artificial. (Si no era artificial no se puede hacer esta opción).

Herencia:
La tres es mas ineficiente que la dos para {M;XOR}

# Ejercicio 1
![](https://i.imgur.com/9PKfC85.jpg)
## Paso 1 & 2
- A(**a1**, a2, a3)
- B(b1, **b2**, b3)
- C(c1, c2, **id_c**)
- D(d1, d2, **id_d**)
- E(e1, e2, **e3**)
- F(f1, f2, f3, **e3**)
- G(g1, g2, g3, **e3**)
- H(h1, h2, h3, **e3**)
## Paso 3
- R_A_B(a1, b2)
- R_B_D(b2, id_d)
- R_D_E(id_d, e3)
## Paso 4
- R_A_B(**a1, b2**)
- R_B_D(**b2**, id_d)
- R_D_E(**id_d**, e3)
## Paso 5
- A(**a1**, a2, a3)
- B(b1, **b2**, b3)
- C(c1, c2, **id_c**, a1, b2) o C(c1, c2, **a1, b2**)
- D(d1, d2, **id_d**)
### Herencia Opcion 1
- E(e1, e2, **e3**)
- F(f1, f2, f3, **e3**)
- G(g1, g2, g3, **e3**)
- H(h1, h2, h3, **e3**)
### Herencia Opcion 4
- E(e1, e2, **e3**, BF, f1, f2, f3, BG, g1, g2, g3, BH, h1, h2, h3)
# Ejercicio 2
![](https://i.imgur.com/odFMh24.png)
## Paso 1 & 2
- A(**a1**, a2)
- B(b1, **b2**)
- C(**c1**, c2, c3)
- D(**d1**, d2, d3)
- E(e1, e2, **d1**)
- F(e1, e2, **d1**)
## Paso 3
- R_A_B(a1, b2)
- R_B_C(b2, c1)
- R_C_D(c1, d1)
- R_A_E(a1, d1)
## Paso 4
- R_A_B(a1, **b2**)
- R_B_C(**b2, c1**)
- R_C_D(**c1, d1**)
- R_A_E(**a1**, d1)
## Paso 5
- A(**a1**, a2, *d1*)
- B(b1, **b2**, *a1*)
- C(**c1**, c2, c3)
- D(**d1**, d2, d3)
- E(e1, e2, **d1**)
- F(e1, e2, **d1**)
- R_B_C(**b2, c1**)
- R_C_D(**c1, d1**)