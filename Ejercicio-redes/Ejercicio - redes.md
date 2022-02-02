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
docker run -d --name sql_mariadb -v /home/usuario/data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=root -p 3306:3306 -network redbd mariadb
```

Comprobamos que está en ejecución:

```bash
docker ps 
```

![](Ejercicio%20-%20redes.assets/sql_mariadb.png)

## Tarea 3.

Pantallazos donde se vea el contenedor creado y en ejecución.

Creamos un contenedor con `Adminer` que se pueda conectar al contenedor de la BD.

```bash
docker run -d --name c_adminer -p 8080:8080 --network redbd adminer
```

Comprobamos que está en ejecución:

```bash
docker ps
```

![](Ejercicio%20-%20redes.assets/c_adminer.png)



## Tarea 4:

Comprobar que el contenedor `Adminer` puede conectar con el contenedor *`mysql`* abriendo un navegador web y accediendo a la URL: http://localhost:8080.

Pantallazo donde se vea el acceso a la BD a través de la interfaz web de `Adminer`.

![](Ejercicio%20-%20redes.assets/acceso_BD_adminer.png)



Accedemos a la BD del servidor en nuestro caso `sql_mariadb`

![](Ejercicio%20-%20redes.assets/conexion_sql_mariadb.png)

Pantallazo donde se entre a la consola del servidor web en modo texto y se compruebe que se ha creado la BD.

![](Ejercicio%20-%20redes.assets/creacion_BD_adminer.png)





Borrar los contenedores, la red y los volúmenes utilizados.

Primero paramos los contenedores en ejecución y luego lo eliminamos. (Aquí podríamos optar por eliminar el contenedor y su volumen al mismo tiempo con la opción: `docker rm -v sql_mariadb`)

```bash
docker stop sql_mariadb
docker stop c_adminer
```

Seguidamente eliminaremos los contenedores

```bash
docker -v rm sql_mariadb
docker rm c_adminer
```



Eliminaremos la red bridge creada:

```bash
docker network rm redbd
```



![](Ejercicio%20-%20redes.assets/eliminacion_datos.png)

