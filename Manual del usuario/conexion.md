--- 
title: Conexion
layout: default
parent: Manual del usuario
nav_order: 4
---

# Conexion a la base de datos
Para conectarte a Neo4j desde tu aplicación o herramienta favorita, necesitarás la dirección IP y el puerto en los que está ejecutándose el servidor de Neo4j. Para llevar a cabo esta tarea, es necesario haber realizado la modificación del archivo de configuración de Neo4j, lo cual ya se completó durante la etapa de instalación. [Configurar archivo](https://xadouuu7.github.io/A04-NEO4j/Manual%20del%20usuario/instalacion.html#archivo-de-configuracion)

## MENU
- [Conexion a la base de datos](https://xadouuu7.github.io/A04-NEO4j/Manual%20del%20usuario/conexion.html#conexion-mediante-web)
- [Conexion mediante web](https://xadouuu7.github.io/A04-NEO4j/Manual%20del%20usuario/conexion.html#conexion-mediante-programa-neo4j-desktop)
- [Conexion mediante auraDB](https://xadouuu7.github.io/A04-NEO4j/Manual%20del%20usuario/conexion.html#conexion-mediante-auradb)

## Conexion mediante web
Para conectarnos a Neo4j mediante HTTP, podemos utilizar nuestro navegador web. Simplemente necesitamos ingresar la dirección IP seguida del puerto en la barra de búsqueda del navegador. El puerto predeterminado para Neo4j es 7474. Por lo tanto, la URL que insertaríamos en la barra de búsqueda sería algo así como: ```http://dirección_IP:7474```. De esta manera, podremos acceder a la interfaz web de Neo4j y comenzar a interactuar con la base de datos.
![](../imagenes/conexion/ipWeb.png)

Una vez que ingresamos la dirección IP y el puerto en la barra de búsqueda del navegador para acceder a Neo4j, se nos pedirá que introduzcamos las credenciales del usuario y la contraseña. Estas credenciales son necesarias para autenticarnos en la base de datos.
![](../imagenes/conexion/credencialesWeb.png)

Una vez que las credenciales han sido verificadas con éxito, tendremos acceso para trabajar con Neo4j. Esto nos permite utilizar todas las funcionalidades y realizar operaciones sobre la base de datos según los permisos y privilegios asignados al usuario autenticado.
![](../imagenes/conexion/credencialesExitosas.png)

## Conexion mediante Programa Neo4j Desktop
[Neo4j Desktop](https://neo4j.com/download/) es un programa que facilita la gestión y el desarrollo de proyectos basados en Neo4j. Proporciona una interfaz gráfica que permite crear y administrar múltiples bases de datos Neo4j. Además que es esto lo que nos interesa, nos permite conectarnos de manera remota para trabajar con las bases de datos desde cualquier ubicación.


## Conexion mediante auraDB