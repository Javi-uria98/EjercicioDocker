> Tarea realizada por Manuel Macho Calvín



[TOC]



# Ejercicio - redes

## Tarea 1:

Crear una red bridge `redbd`.

```bash
docker network create redbd
docker network inspect redbd
```

![](Ejercicio%20-%20redes.assets/001.PNG)



## Tarea 2:

Crea un contenedor con una imagen de `mariaDB` que estará en la red `redbd` . Este contenedor se ejecutará en segundo plano, y será accesible a través del puerto 3306. (Es necesario definir la contraseña del usuario `root` y un volumen de datos persistente).

Pantallazos donde se vea el contenedor creado y en ejecución.

Primero creamos el contenedor:

```bash
docker run -d --name contenedor_mariadb -v mivolumen:/usr/local/apache2/htdocs -p 3036:80 --network redbd -e MYSQL_ROOT_PASSWORD=laboral1 mariadb
```

![](Ejercicio%20-%20redes.assets/002.PNG)

Comprobamos que está en ejecución:

```bash
docker ps -a
```

![](Ejercicio%20-%20redes.assets/003.PNG)

## Tarea 3.

Crear un contenedor con `Adminer` que se pueda conectar al contenedor de la BD.

Pantallazos donde se vea el contenedor creado y en ejecución.

Pantallazo donde se vea el acceso a la BD a través de la interfaz web de `Adminer`.

Pantallazo donde se entre a la consola del servidor web en modo texto y se compruebe que se ha creado la BD.

## Tarea 4:

Comprobar que el contenedor `Adminer` puede conectar con el contenedor *`mysql`* abriendo un navegador web y accediendo a la URL: http://localhost:8080.

Borrar los contenedores la red y los volúmenes utilizados.

