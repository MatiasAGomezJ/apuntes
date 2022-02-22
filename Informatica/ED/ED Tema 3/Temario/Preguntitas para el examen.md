º# Apuntes Examen Diciembre ED
1. 1P. Identificar partes interesadas
2. 3P. Identificar requisitos funcionales de las partes interesadas (2-3 por cada una d ellas)
3. 6P Elige dos:
	1. 3P Diagramas de casos de uso
	2. 3P Diagramas de secuencia
	3. 3P Teoria
		1. 1,5P Fases general del ciclo del desarrollo del software y/o metodologias usadas ( igual hay que explicarlas)
		2. 1,5P Diagramas de comportamiento (definición, clasificación)
## 1P Primer Ejercicio: Identificar partes interesadas
- Cliente - RF_Cliente_XX
- Técnico - RF_Técnico_XX
- Director - RF_Director_XX

## 3P Segundo Ejercicio: Identificar requisitos funcionales de las partes interesadas (2-3 por cada una d ellas)

### Cliente - RF_Cliente_01
- **RF_Cliente_01:** Realiza consulta
    - Especificar urgencia
    - Especificar ubicacion
    - Proporcionar datos
- **RF_Cliente_02:** Evaluacion servicio
    - Evaluacion del tecnico
    - Evaluacion materiales
    - Revisar horas operarios
- **RF_Cliente_03:** Consultar estado servicio
    - Fecha inicio de reparacion
    - Fecha estimada de finalizacion
    - Identificacion tecnicos
    - Hora llegada tecnicos

### Técnico - RF_Técnico_01

- **RF_TÈCNIC_01:** Visualizar servicio asignado
    - Descripción servicio
    - Datos clientes (ubicación, ...)- Descripción servicio
    - Datos clientes (ubicación, ...)
- **RF_TÈCNIC_02:** Solicitar material necesario del almacén
    - Solicitar ingresar material almacén
    - Solicitar retirar material almacén
    - Solicitar más material
- **RF_TÈCNIC_03:** Reportar incidencia
    - Falta material, ...

### Director - RF_Director_01

- **RF_DIRECTOR_01:** Visualizar servicio
    - Descripción servicio
    - Datos clientes (ubicación, ...)
- **RF_DIRECTOR_02:** Buscar técnico adecuado
    - Ver la disponibilidad de los técnicos
    - Mandar al técnico
- **RF_DIRECTOR_03** Pagar al técnico
    - Pagar al técnico

## 6P Tercer Ejercicio
Escoger dos de ellos:
- Diagramas de casos de uso
- Diagramas de secuencia
- Teoria
### 3P Diagramas de casos de uso
![](https://i.imgur.com/FopqRg3.png)
![](https://i.imgur.com/Yg0y9l7.png)
### 3P Diagramas de secuencia
![](https://i.imgur.com/RLa7wv3.png)
### 3P Teoria
#### 1.5P Fases general del ciclo del desarrollo del software y/o metodologias usadas ( igual hay que explicarlas)
Fases:
- Analisis: Fase en la cual el usuario especifica los requisitos para un producto completo.
- Diseño: Se estudian las posibles formas de implementar el software, asi como la estructura del mismo.
- Implementacion: Se construye el software en base a los requistos establecidos en la fase de analisis y con las herramientas vistas en la fase de diseño.
- Pruebas: Fase en la cual se buscan e intentan arreglar los fallos exitentes en el software
- Despliegue: Fase en la cual se entrega una version ya funcional del producto al clinete/usario.
- Mantenimiento: Una vez entregado el producto, pueden surgir problemas, los cuales se arreglaran con el tiempo.

Metodologioas:
- Cascada
- Prototipado
- Espiral
- Scrum
- Incremental
#### 1.5P Diagramas de comportamiento (definición, clasificación)
**Los diagramas de comportamiento representan el comportamiento dinámico del sistema que se está moldeando. Es decir, indican las acciones y procesos que se llevarán a cabo entre los elementos del sistema**

Describen el comportamiento de clasificadores o de sus instancias, desde distintos puntos de vista:

- Por un lado, representan o bien componentes ejecutantes o bien comportamientos emergentes.
- Por otra, se destaca uno de estos aspectos u otro: interacciones con el exterior, o las situaciones por las que pasa una instancia durante su existencia, o la secuencia temporal de las distintas partes de un comportamiento...

![](https://i.imgur.com/O7QyY9Z.png)
### Diagrama de actividades
**Diagrama de actividades** es lo que descompone un comportamiento en actividades y representa los flujos de ejecución y de información entre estas actividades.
### Diagrama de casas de uso
**Diagrama de casos de uso**. Este diagrama identifica los distintos comportamientos de un sistema desde el punto de vista de sus interacciones con el mundo exterior y describe determinadas relaciones entre estos comportamientos.
### Diagrama de estados
**Diagrama de estados** (en inglés State Machine Diagram). Este diagrama muestra los posibles cambios de una situación a otra de las instancias del clasificador de contexto e indica las causas y comportamientos que ponen en marcha estos cambios.
### Diagramas de interacción
Los otros cuatro diagramas están agrupados en los **diagramas de interacción**. Esta agrupación contiene diagramas que representan un comportamiento emergente mediante mensajes entre las instancias de clasificadores de una estructura interna o colaboración y puede especificar restricciones temporales relativas a estos mensajes.
#### Diagrama de comunicaciones
**Diagrama de comunicaciones**, que representa los mensajes sobre los conectores de una estructura interna o colaboración.
#### Diagrama de secuencia
**Diagrama de secuencia**, que pone énfasis en el orden temporal de los mensajes.
#### Diagrama de tiempo
**Diagrama de tiempo**, que representa una posible secuencia temporal de cambios de estado de una instancia o de diversas instancias que interactúan de acuerdo con los diagramas de estados respectivos.
#### Diagrama global de interacción
**Diagrama global de interacción**, que es un diagrama resumido que combina notaciones de los diagramas de secuencias y de los de actividades.