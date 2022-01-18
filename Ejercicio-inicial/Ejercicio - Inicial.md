> Tarea realizada por Manuel Macho Calvín



# Ejercicio - inicial

[TOC]



Crear un contenedor demonio a partir de la imagen `nginx` , el contenedor se debe llamar ***servidor_web*** y se debe acceder a él utilizando el puerto 8181 del ordenador donde tengas instalado **`docker`** y podamos comprobar que el contenedor está funcionando.

------



# Tarea 1:

Pantallazo donde se vea la creación del contenedor y podamos comprobar que el contenedor está funcionando.

```bash
docker run -d --name servidor_web -p 8181:80 nginx
```

![](Ejercicio%20-%20Inicial.assets/001.png)



# Tarea 2:

 Pantallazo donde se vea el acceso al servidor web utilizando un navegador web (recuerda que tienes que acceder a la `ip` del ordenador donde tengas instalado **`docker`**)

En nuestro caso la dirección `ip` es: 172.18.0.1:8181

```bash
ip address
```

![](Ejercicio%20-%20Inicial.assets/ip-docker.png)



![](Ejercicio%20-%20Inicial.assets/002.png)



# Tarea 3:

 Pantallazo donde se vean las imágenes que tienes en tu registro local

```bash
docker images
```

![](Ejercicio%20-%20Inicial.assets/003.png)



# Tarea 4:

Pantallazo donde se vea cómo se elimina el contenedor (recuerda que antes debe estar parado el contenedor).

Paramos el contenedor primero:

```bash
docker stop servidor_web
```

![](Ejercicio%20-%20Inicial.assets/004-16424968157491.png)

Comprobamos a continuación que existe el contenedor servidor_web:

```bash
docker ps -a
```

![](Ejercicio%20-%20Inicial.assets/005-16424968370922.png)

Eliminamos el contenedor y comprobamos que ya no está:

```bash
docker rm servidor_web
```

![](Ejercicio%20-%20Inicial.assets/006.png)

```bash
docker ps -a
```

![](Ejercicio%20-%20Inicial.assets/007.png)

