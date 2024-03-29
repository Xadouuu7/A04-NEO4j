---
title: Consulta de datos
layout: default
parent: Manual del usuario
nav_order: 5
---

# CONSULTA DE DATOS
En esta sección, exploraremos las sentencias básicas de Cypher, el lenguaje utilizado por Neo4j, para consultar en bases de datos de grafos. Aunque similar a SQL en algunos aspectos, Cypher presenta diferencias significativas que es importante comprender.

## SIMILITUDES Y DIFERENCIAS ENTRE SQL Y CYPHER
### Similitudes
SQL y Cypher comparten algunas similitudes, como el uso de cláusulas como ```WHERE``` y ```ORDER BY```. Sin embargo, también tienen diferencias fundamentales.

### Diferencias


#### **Orden de querys**
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

#### **Querys mas breves**
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

## Consultas simples

### Creacion de un modelo de datos
El siguiente grafos sera utilizado para los ejemplos de abajo:
![](../imagenes/consulta/dataModel.png)

Para poder recrearlo necesitaremos seguir la insercion en una base de datos Neo4j vacia:

```
CREATE
(russell:PLAYER{name:"Russell Westbrook", age: 33, number: 0, height: 1.91, weight: 91}),
(lebron:PLAYER{name:"LeBron James", age: 36, number: 6, height: 2.06, weight: 113}),
(anthony:PLAYER{name:"Anthony Davis", age: 28, number: 23, height: 2.08, weight: 115}),

(frank:COACH{name: "Frank Vogel"}),
(bryan:COACH{name: "bryan Jenkins"}),
(jason:COACH{name: "Jason Kidd"}),

(lakers:TEAM{name:"LA Lakers"}),
(memphis:TEAM{name:"Memphis Grizzlies"}),
(mavericks:TEAM{name:"Dallas Mavericks"}),

(lebron)-[:TEAMMATES]-> (russell),
(lebron)<-[:TEAMMATES]- (russell),

(frank)-[:COACHES]->(lakers),
(bryan)-[:COACHES]->(memphis),

(lebron)-[:PLAYS_FOR {salary: 40000000}]-> (lakers),
(russell)-[:PLAYS_FOR {salary: 33000000}]-> (lakers),

(lebron)-[:PLAYED_AGAINST {minutes: 38, points: 32, assists: 6, rebounds: 6, turnovers: 2}]-> (memphis),
(russell)-[:PLAYED_AGAINST {minutes: 29, points: 16, assists: 12, rebounds: 11, turnovers: 16}]-> (memphis),
```

### Sintaxis Cypher
| Clausula               | Explicacion                                                                      |
|:-----------------------|:---------------------------------------------------------------------------------|
| MATCH                  | Aquesta cláusula s’utilitza per trobar un patró específic en el graf.            |
| RETURN                 | Aquesta especifica quina part del patró de graf trobat (MATCH) volem retornar.   |
| LIMIT                  | Amb això el que podem fer es limitar el total de resultats que retornarà         |
| WHERE                  | Podem filtrar resultats utilitzant aquesta clàusula                              |
| ORDER BY               | Amb aquesta podrem ordenar els resultats que ens mostrarà el return              |
| DISTINCT               | Aquesta clàusula ens ajudarà a treure els resultats repetits.                    |
| -nodo[:relación]->nodo | Se utilitza per trobar relacions entre nodes, podem especificar la relacio       |

### Ejemplos de consultas

