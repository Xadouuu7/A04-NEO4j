---
title: Insercion de datos
layout: default
parent: Manual del usuario
nav_order: 6
---

# INSERCION DE DATOS

La cláusula ```CREATE``` se utiliza para crear nodos y relaciones en una base de datos de grafos. Para definir qué nodos y relaciones se deben crear, es necesario especificar con precisión sus características y propiedades.

## Sintaxis para nodos
```CREATE``` nos permite crear uno o mas nodos, a cada nodo se le puede asignar clave:valor. Tambien se le puede vincular a cada nodo a una variable a la que se puede hacer referencia mas adelante en consulta

```
CREATE (alex:PLAYER{name:"Alex Garcia", age: 28, number: 5, height: 1.99, weight: 95}), (warriors:TEAM{name: "Warriors"})
```
Tambien puedes añadirle varias etiquetas, por ejemplo Alex Garcia puede ser un jugador y un entrenador
```
CREATE (alex:PLAYER:COACH{name:"Alex Garcia", age: 28, number: 5, height: 1.99, weight: 95})
```

## Sintaxis para relaciones
La cláusula ```CREATE``` también puede utilizarse para crear relaciones en una base de datos de grafos. Las relaciones siempre requieren un tipo de relación y una dirección. Además, es posible asignar propiedades a las relaciones y vincularlas a variables.
```
CREATE (alex)-[:JUEGA_PARA {salario: 20000000}]->(warriors)
```

Tambien podemos crear los nodos y la relacion al mismo tiempo:
```
CREATE (alex:PLAYER{name:"Alex Garcia", age: 28, number: 5, height: 1.99, weight: 95})-[:JUEGA_PARA {salario: 20000000}]->(warriors:TEAM{name: "Warriors"})
```