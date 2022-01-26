---
title: Ejercicio - Creación de imagen con Dockerfile
author: Javier Uría
---

# Ejercicio - Creación de imagen con Dockerfile

> Tarea realizada por Javier Uría

[TOC]

## Crear imagen con un servidor web que sirva un sitio web

En primer lugar, creo el directorio "contexto" donde alojaré tanto el sitio web como el archivo Dockerfile:

![creacion Dockerfile](Ejercicio%20Docker%20-%20Trabajo%20con%20im%C3%A1genes.assets/creacion%20Dockerfile.PNG)

![sitio web](Ejercicio%20Docker%20-%20Trabajo%20con%20im%C3%A1genes.assets/sitio%20web.PNG)



Después, creo una nueva imagen a partir de ese dockerfile, utilizando un repositorio propio de DockerHub.

![creacion imagen](Ejercicio%20Docker%20-%20Trabajo%20con%20im%C3%A1genes.assets/creacion%20imagen-16432130004511.PNG)

![imagen creada](Ejercicio%20Docker%20-%20Trabajo%20con%20im%C3%A1genes.assets/imagen%20creada.PNG)



Una vez creada la imagen, me logueo en mi DockerHub y la subo al repositorio.

![subida de imagen a dockerhub](Ejercicio%20Docker%20-%20Trabajo%20con%20im%C3%A1genes.assets/subida%20de%20imagen%20a%20dockerhub.PNG)

![imagen subida](Ejercicio%20Docker%20-%20Trabajo%20con%20im%C3%A1genes.assets/imagen%20subida-16432131611702.PNG)



Por último, creo un contenedor con dicha imagen (que como yo ya la tengo no me hace falta descargarla del DockerHub) y accedo al contenedor desde el navegador para ver el sitio web.

![correr contenedor con imagen](Ejercicio%20Docker%20-%20Trabajo%20con%20im%C3%A1genes.assets/correr%20contenedor%20con%20imagen.PNG)

![acceso desde navegador](Ejercicio%20Docker%20-%20Trabajo%20con%20im%C3%A1genes.assets/acceso%20desde%20navegador.PNG)



Y, como prueba final, le pido a Manuel que, desde su equipo y máquina virtual, se baje mi imagen de mi repositorio, cree un contenedor con ella y compruebe que a el también le funciona.

![docker pull Manuel](Ejercicio%20Docker%20-%20Creacion%20de%20imagen%20con%20Dockerfile.assets/docker%20pull%20Manuel.png)

![docker run Manuel](Ejercicio%20Docker%20-%20Creacion%20de%20imagen%20con%20Dockerfile.assets/docker%20run%20Manuel.png)

![navegador Manuel](Ejercicio%20Docker%20-%20Creacion%20de%20imagen%20con%20Dockerfile.assets/navegador%20Manuel-16432224191751.png)
