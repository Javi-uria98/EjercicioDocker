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
docker run -d --name sql_mariadb -v data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=root -p 81:3306 -network redbd mariadb
```

Comprobamos que está en ejecución:

```bash
docker ps -a
```

![](Ejercicio%20-%20redes.assets/0300.png)

## Tarea 3.

Pantallazos donde se vea el contenedor creado y en ejecución.

Creamos un contenedor con `Adminer` que se pueda conectar al contenedor de la BD.

```bash
docker run -d --rm --network redbd -e PMA_ARBIRARY=1 -p 80:80 adminer
```

Comprobamos que está en ejecución:

```bash
docker ps
```

![](Ejercicio%20-%20redes.assets/0301.png)

Pantallazo donde se vea el acceso a la BD a través de la interfaz web de `Adminer`.

Pantallazo donde se entre a la consola del servidor web en modo texto y se compruebe que se ha creado la BD.

## Tarea 4:

Comprobar que el contenedor `Adminer` puede conectar con el contenedor *`mysql`* abriendo un navegador web y accediendo a la URL: http://localhost:8080.

Borrar los contenedores, la red y los volúmenes utilizados.

Primero paramos el contenedor en ejecución y luego lo eliminamos. (Aquí podríamos optar por eliminar el contenedor y su volumen al mismo tiempo con la opción: `docker rm -v sql_mariadb`)

```bash
docker stop sql_mariadb
docker rm sql_mariadb
```

Seguidamente eliminaremos el volumen. Podremos ver la lista de volúmenes existentes y elegir el que pertenece al contenedor.

```bash
docker volume ls
docker rm data
```



Eliminaremos la red bridge creada:

```bash
docker network rm redbd
```

![](Ejercicio%20-%20redes.assets/0400.png)

