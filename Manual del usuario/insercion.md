---
title: Insercion de datos
layout: default
parent: Manual del usuario
nav_order: 6
---

# INSERCIÓ DE DADES
La clàusula ```CREATE``` s'utilitza per crear nodes i relacions en una base de dades de grafs a Neo4j. Per definir quins nodes i relacions s'han de crear, és necessari específicar amb precisió les seves característiques i propietats.

## Sintaxi pels nodes
```CREATE``` ens permet crear un o més nodes, a cada node se li pot assignar clau:valor. També se li pot vincular a cada node una variable a la que es pot fer referència més tard en la consulta.
```
CREATE (alex:PLAYER{name:"Alex Garcia", age: 28, number: 5, height: 1.99, weight: 95}), (warriors:TEAM{name: "Warriors"})
```
També pots afegir més d'una etiqueta, per exemple, l'Alex García pot ser un jugador però també un entrenador:
```
CREATE (alex:PLAYER:COACH{name:"Alex Garcia", age: 28, number: 5, height: 1.99, weight: 95})
```
## Sintaxis per les relaciones
La clàusula ```CREATE``` també pot utilitzar-se per crear relacions en una base de dades de grafs a Neo4j. Les relacions sempre requereixen un tipus de relació i una direcció. A més, és possible assignar propietats a les relacions i vincular-les a variables.
```
CREATE (alex)-[:JUEGA_PARA {salario: 20000000}]->(warriors)
```
També podem crear els nodes i les relacions al mateix temps:
```
CREATE (alex:PLAYER{name:"Alex Garcia", age: 28, number: 5, height: 1.99, weight: 95})-[:JUEGA_PARA {salario: 20000000}]->(warriors:TEAM{name: "Warriors"})
```