---
title: Actividad 4.02 - Módulos Apache
author: Javier Uría
---

# Ejercicio - Trabajo con imágenes

> Tarea realizada por Javier Uría

[TOC]

## Servidor web

1. Arranca un contenedor que ejecute una instancia de la imagen `php:7.4-apache` , que se llame `web` y que sea accesible desde un navegador en el puerto `8000`.

   ```bash
   sudo docker pull php:7.4-apache
   sudo docker run -d --name web -p 8000:80 php:7.4-apache
   ```

   ![docker search](Ejercicio%20Docker%20-%20Trabajo%20con%20im%C3%A1genes.assets/docker%20search.PNG)

   ![docker run](Ejercicio%20Docker%20-%20Trabajo%20con%20im%C3%A1genes.assets/docker%20run.PNG)

   

2. Colocar en el directorio raíz del servicio web ( `/var/www/html` ) de dicho contenedor un fichero llamado `index.html` con mi nombre:

   ```bash
   sudo docker exec -it web bash
   echo "<h1>HOLA SOY JAVIER URIA</h1>" > index.html
   ```

   ![image-20220118202908465](Ejercicio%20Docker%20-%20Trabajo%20con%20im%C3%A1genes.assets/image-20220118202908465.png)

   ![image-20220118205338786](Ejercicio%20Docker%20-%20Trabajo%20con%20im%C3%A1genes.assets/image-20220118205338786.png)

   

3. Colocar en ese mismo directorio raíz un archivo llamado `mes.php` que muestre el nombre del mes actual. Ver la salida del script en el navegador

   ```bash
   echo "<?php echo date('ls jS \de F Y h:i:s A'); ?>" > mes.php
   ```

   ![image-20220118203844367](Ejercicio%20Docker%20-%20Trabajo%20con%20im%C3%A1genes.assets/image-20220118203844367.png)

   ![creacion mes-php](Ejercicio%20Docker%20-%20Trabajo%20con%20im%C3%A1genes.assets/creacion%20mes-php.PNG)

   ![image-20220118205303441](Ejercicio%20Docker%20-%20Trabajo%20con%20im%C3%A1genes.assets/image-20220118205303441.png)

   (Aprovecho que he creado los dos ficheros para mostrar el tamaño del contenedor)

   ```bash
   sudo docker ps -a -s
   ```

   ![tamaño contenedor](Ejercicio%20Docker%20-%20Trabajo%20con%20im%C3%A1genes.assets/tama%C3%B1o%20contenedor.PNG)

   

4. Borrar el contenedor

   ```bash
   sudo docker stop web
   sudo docker rm web
   ```

   ![image-20220118205612691](Ejercicio%20Docker%20-%20Trabajo%20con%20im%C3%A1genes.assets/image-20220118205612691.png)

​	



## Servidor de base de datos

1. Arrancar un contenedor que se llame bbdd y que ejecute una instancia de la imagen mariadb para que sea accesible desde el puerto 3336.

   ```bash
   sudo docker run -d --name bbdd -p 3336:3306 mariadb
   ```

   ![image-20220120163848514](Ejercicio%20Docker%20-%20Trabajo%20con%20im%C3%A1genes.assets/image-20220120163848514.png)

   

2. Antes de arrancarlo visitar la página del contenedor en Docker Hub y establecer las variables de entorno necesarias para que:

   La contraseña de root sea root . Crear una base de datos automáticamente al arrancar que se llame prueba . Crear el usuario invitado con la contraseña invitado .

   ```bash
   sudo docker run --detach --name bbdd --env MARIADB_USER=invitado --env MARIADB_PASSWORD=invitado --env MARIADB_DATABASE=prueba --env MARIADB_ROOT_PASSWORD=root -p 3336:3306 mariadb
   ```

   ![image-20220120175726160](Ejercicio%20Docker%20-%20Trabajo%20con%20im%C3%A1genes.assets/image-20220120175726160.png)

   (Aprovecho también para sacar una captura del borrado de la imagen fallido al estar siendo usada por un contenedor)

   ```bash
   sudo docker rmi mariadb
   ```

   ![image-20220120171026169](Ejercicio%20Docker%20-%20Trabajo%20con%20im%C3%A1genes.assets/image-20220120171026169.png)

   (Captura desde un cliente de base de datos (instalado en tu ordenador) se pueda observar que hemos podido conectarnos al servidor de base de datos con el usuario creado y que se ha creado la base de datos prueba ( show databases ))

   ![image-20220120180408114](Ejercicio%20Docker%20-%20Trabajo%20con%20im%C3%A1genes.assets/image-20220120180408114.png)

   ![image-20220120180325359](Ejercicio%20Docker%20-%20Trabajo%20con%20im%C3%A1genes.assets/image-20220120180325359.png)

   

