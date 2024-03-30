---
title: Manipulacion de datos
layout: default
parent: Manual del usuario
nav_order: 7
---

# MANIPULACION DE DATOS

## SET
Para manipular los datos se usa la clausula ```SET```, se utiliza para actualizar etiquetas en nodos, relaciones y propiedades en los nodos
The SET clause is used to update labels on nodes and properties on nodes and relationships.

Los ejemplos utilizan este grafo:
![](../imagenes/manipulacion/modeloFoto.png)
```
CREATE (alex:PLAYER{name:"Alex Garcia", age: 28, number: 5, height: 1.99, weight: 95})-[:JUEGA_PARA {salario: 20000000}]->(warriors:TEAM{name: "Warriors"})
```
### Establecer un propiedades
Queremos cambiar la edad de Alex Garcia a 29 y la altura
```
MATCH(n:PLAYER {name:"Alex Garcia"})
SET n.age = 29, n.height = 1.99
RETURN n.name, n.age
```
Queremos cambiar el salario de Alex Garcia en Warriors 
```
MATCH(n:PLAYER {name:"Alex Garcia"}) -[r:JUEGA_PARA]-> (m:TEAM {name: "Warriors"})
SET r.salario = 1273189031
RETURN n.name, r.salario, m.name
```
### Actualizar una propiedades
Queremos el tipo de variable a edad pase a String:
```
MATCH(n:PLAYER {name:"Alex Garcia"})
SET n.age = ToString(n.age)
RETURN n.name, n.age
```

## DELETE
Para eliminar un solo nodo
```
MATCH(n:PLAYER {name:"Alex Garcia"})
DELETE n
```
Eliminar solo las relaciones
```

MATCH(n:PLAYER {name:"Alex Garcia"}) -[r:JUEGA_PARA]-> (m:TEAM {name: "Warriors"})
DELETE r
```

Eliminar un nodo y todas sus relaciones
```
MATCH(n:PLAYER {name:"Alex Garcia"})
DETACH DELETE n
```

Eliminar todos los nodos y las relaciones
```
MATCH (n) DETACH DELETE n
```

## REMOVE
La clausula ```REMOVE``` se utiliza para remover propiedades de los nodos y las relaciones

### Eliminar una propiedad
Neo4j no se permite almacenar '''null''' en propiedades, si no existe ningun valor la propiedad no estara presente. Por lo tanto una clausula ```REMOVE``` se utiliza para eliminar un valor una propiedad

Se puede eliminar uno o varias etiquetas a la vez
```
MATCH(n:PLAYER {name:"Alex Garcia"})
REMOVE n.age, n.height
RETURN n.name, n.age
```