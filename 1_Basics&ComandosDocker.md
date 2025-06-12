# Docker Basics & Commands

## ¿Qué es Docker?

Docker es una herramienta de contenerización (una forma de virtualización a nivel de sistema operativo) que permite empaquetar aplicaciones y sus dependencias en "imágenes" ligeras y portátiles. Estas imágenes se pueden ejecutar en cualquier lugar donde Docker esté instalado, lo que facilita la implementación y escalado de aplicaciones en diferentes entornos (nube, cloud, etc.).

> ¡Fin del "pero en mi PC funciona"! 😄

## Compatibilidad

Docker sólo corre en Linux, pero se puede trabajar en Windows a través de WSL2 (Windows Subsystem for Linux 2), que se instala con Docker Desktop o una VM Linux. En Mac, Docker Desktop también utiliza una VM para ejecutar contenedores.

## Conceptos básicos

- **Dockerfile**: Archivo de texto plano que contiene instrucciones para construir una imagen de Docker y automatizar el proceso de creación de imágenes
- **Imagen**: Versión compilada de un dockerfile, contiene todo lo necesario para ejecutar una aplicación
- **Contenedor**: Instancia en ejecución de una imagen de Docker
- **Docker Hub**: Repositorio oficial de imágenes de Docker
- **Docker Daemon**: Proceso que gestiona los contenedores de Docker en segundo plano
- **Cliente Docker**: CLI para interactuar con el daemon de Docker... sí, docker trabaja bajo el modelo cliente-servidor donde el cliente es la CLI y el servidor es el daemon.

## Hola Mundo en Docker

### Ejecutar servidor Apache

```bash
docker run -d -p 8080:80 --name webserver httpd:latest
```

> **Nota:** Docker desktop debe estar instalado y corriendo si ejecutas este comando en Windows o Mac. En Linux, asegúrate de tener Docker instalado y el daemon corriendo.

### Parámetros del comando

- `docker run`: Comando para ejecutar un contenedor, si la imagen de este contenedor no existe localmente, Docker la descargará de Docker Hub
- `-d`: Ejecuta el contenedor en segundo plano (detached mode)
- `-p`: Mapea el puerto 8080 del host al puerto 80 del contenedor
- `--name`: Asigna un nombre al contenedor
- `httpd:latest`: Imagen oficial de Apache (última versión)

Listo, ahora puedes acceder al servidor Apache en tu navegador en `http://localhost:8080`. Así de fácil ¡sin tener que instalar y configurar Apache en tu máquina o en una máquina virtual!

### Otros comandos de gestión

```bash
# Ver contenedores en ejecución
docker ps

# Ver todos los contenedores (incluso detenidos)
docker ps -a
```

```bash
# Para detener un contenedor
docker stop <nombre_contenedor>

# Para eliminar un contenedor
docker rm <nombre_contenedor>

# Para eliminar una imagen
docker rmi <nombre_imagen>
```

```bash
# Para ver los logs de un contenedor
docker logs <nombre_contenedor>

# Para acceder a la CLI de un contenedor en ejecución
docker exec -it <nombre_contenedor> /bin/bash
```

```bash
# Para construir/compilar una imagen a partir de un Dockerfile
docker build -t <nombre_imagen> .

# Para ejecutar un contenedor a partir de una imagen
docker run -d -p 8080:80 --name <nombre_contenedor> <nombre_imagen>
```

```bash
# Para ver el estado de Docker
docker info

# para ver la ayuda de un comando
docker <comando> --help
```
