---
title: Consulta de datos
layout: default
parent: Manual del usuario
nav_order: 5
---

# CONSULTA DE DATOS
En esta sección, exploraremos las sentencias básicas de Cypher, el lenguaje utilizado por Neo4j para consultar, modificar, insertar y eliminar nodos y relaciones en bases de datos de grafos. Aunque similar a SQL en algunos aspectos, Cypher presenta diferencias significativas que es importante comprender.

## SIMILITUDES Y DIFERENCIAS ENTRE SQL Y CYPHER
### Similitudes
SQL y Cypher comparten algunas similitudes, como el uso de cláusulas como ```WHERE``` y ```ORDER BY```. Sin embargo, también tienen diferencias fundamentales.

### Diferencias


#### Orden de querys
Una de las diferencias clave es el orden de las consultas. En Cypher, todas las consultas terminan con la cláusula ```RETURN```, que especifica lo que el usuario desea obtener como resultado, mientras que en SQL comienzas seleccionando lo que quieres ver con un ```SELECT```. Para ilustrar esto, consideremos las siguientes dos consultas que buscan jugadores con una altura mayor a 1.91, la primera en SQL y la segunda en Cypher:

```
SELECT name
FROM player
WHERE height > 1.91;
```
```
MATCH (player:PLAYER)
WHERE player.height > 1.91
RETURN player.name
```

#### Querys mas breves
Las consultas en Cypher suelen ser más breves que sus equivalentes en SQL. Por ejemplo, considera las siguientes dos consultas que buscan los jugadores que forman parte del equipo 'LA Lakers':
```
SELECT player.name
FROM player pl
INNER JOIN plays_for plfo ON plfo.playerid = pl.playerid
INNER JOIN team te ON te.teamid = plfo.teamid
WHERE te.name = 'LA Lakers'
```
En SQL, esta consulta implica acceder a varias tablas debido a la relación muchos a muchos.
```
MATCH(player:PLAYER)-[:PLAYS_FOR]->(team:TEAM {name: 'LA Lakers'})
RETURN player.name
```
Por lo contrario en Cypher las consultas simplemente son sobre la relacion entre los nodos player y el nodo con nombre 'La Lakers'.