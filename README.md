<kbd><img src="./img/contenedores.jpg" style="border:1px solid grey"></kbd>

# Docker

## Índice

1. [Introducción](#1-introducción)
2. [Conceptos Fundamentales](#2-conceptos-fundamentales)
3. [Instalaciones](#3-instalaciones)
4. [Flujo de Trabajo en Docker](#4-flujo-de-trabajo-en-docker)
5. [Comandos Esenciales](#5-comandos-esenciales)
6. [Recursos Adicionales](#11-recursos-adicionales)

---

## 1. Introducción

<kbd><img src="https://jorgebenitezlopez.com/github/docker-facebook.png" style="border:1px solid grey"></kbd>

[Docker (WEB)](https://www.docker.com/) 🌐: Develop faster. Run anywhere. Accelerate how you build, share, and run applications

> ¿Qué es Docker? 👉 un conjunto de herramientas, servicios y entornos que permiten desarrollar, ejecutar o gestionar aplicaciones.

🚀 Docker permite **empaquetar aplicaciones con todas sus dependencias**, como librerías y versiones de lenguajes, en contenedores ligeros. Esto asegura que la aplicación **funcione igual en cualquier entorno**, evitando problemas de compatibilidad entre desarrollo y producción.

👨‍💻 El creador de Docker, Solomon Hykes, quería resolver justamente ese problema: que el código funcionara de la misma forma en desarrollo y en producción. Aunque los contenedores ya existían en Linux, **Docker los hizo simples y accesibles para todos**. Su popularidad creció rápidamente, pero la empresa tuvo dificultades para monetizar y en 2020 vendió parte de su negocio.

💻 Antes de Docker, las máquinas virtuales (VMs) eran la opción para aislar aplicaciones. Las VMs emulan un sistema operativo completo, lo que las hace más pesadas y lentas. Además, ocupan más espacio y consumen más recursos que Docker, lo que dificulta la escalabilidad y el rendimiento.

<kbd>
  <img src="./img/memedocker.png" style='width: 70%; display: block; margin: 0 auto;border:1px solid grey'">
</kbd>

🚨 ¿Entendemos para qué sirve? ¿Qué puede pasar en el caso de no usar? ¿Qué se usaba antes? 🚨

## 2. Conceptos fundamentales

<kbd><img src="./img/conceptosdocker.png" style="border:1px solid grey"></kbd>

📖 **Dockerfile**: Es como una receta que especifica, paso a paso, cómo preparar un entorno en el que se ejecutará una aplicación.

🖼️ **Imágenes**: Una imagen es una plantilla que contiene todo lo necesario para ejecutar un contenedor: el código de la aplicación, el entorno de ejecución, las dependencias, etc. Las imágenes pueden ser compartidas a través de repositorios como **[Docker Hub](https://hub.docker.com/)**. Las imágenes se crean a partir de un Dockerfile y se pueden ejecutar como contenedores.
>[!NOTE]
> Una imagen de Docker no es magia, son archivos en tu disco que contienen:
>
>- Sistema base + Dependencias y librerías + Tu código + Metadatos


📦 **Contenedores**: Un contenedor es una instancia en ejecución de una imagen. Es el entorno aislado en el que se ejecuta la aplicación. Cada contenedor tiene su propio sistema de archivos, procesos, redes y espacio de CPU/memoria. Piensa en el contenedor como una "caja" donde vive y se ejecuta la aplicación, separada del resto del sistema.

> [!NOTE]
> El contenedor es la imagen en ejecución, levantada, activa.
> 
> Una imagen se convierte en contenedor cuando Docker la levanta y la hace funcionar.

 📜 **Docker Compose**: Docker Compose es una herramienta que permite definir y ejecutar aplicaciones multicontenedor. Se utiliza un archivo `docker-compose.yml` para configurar los servicios de una aplicación, como bases de datos, servidores, etc., y luego se ejecutan con un solo comando.
 
  💾 **Volúmenes** : Los volúmenes en Docker se utilizan para persistir datos más allá del ciclo de vida de los contenedores, los cuales son efímeros y pueden ser eliminados fácilmente. Los volúmenes permiten que los datos persistan incluso después de que el contenedor haya sido destruido. Además, también se pueden utilizar para mapear código entre el sistema anfitrión y el contenedor, lo que facilita la edición en tiempo real dentro del contenedor.
  
  > [!NOTE]
  > Un volumen es un directorio en el sistema de archivos del host que Docker administra
  
 ### ¿Todavía con dudas? quizás estas métaforas te puedan ayudar...

> ### 🥣 Metáfora Cocina  
> Es habitual que se confundan los términos de imágen y contenedor e incluso usarse únicamente el término contenedor para hacer referencia a ambos. Pero la realidad es que nunca se puede construir un contenedor o descargar uno, ya que los contenedores solo existen durante el tiempo de ejecución. Las imágenes, por otro lado, son archivos inmutables: no puedes editar una imagen después de haberla creado. 
>
> La `imagen` es un plato pre-cocinado y congelado.
>
> El `contenedor` es el delicioso manjar.


  > ### 🧙‍♂️ Cápsula del tiempo
  > 
  > Docker es como una cápsula del tiempo que congela tu aplicación con todo lo necesario para que siempre funcione igual, aquí o en cualquier otro sitio.
  >
  >  - Guarda no solo tu código, sino también el sistema operativo base, librerías, runtimes y dependencias.
  > - Esa “foto” (la imagen) siempre se comportará igual, sin importar si pasan meses o años.
  > - Cuando corres el contenedor, básicamente “revives” ese mismo entorno exacto en el que funcionaba tu proyecto.
  >
  > 👉 La diferencia con una máquina virtual es que Docker no “congela” un ordenador entero con su kernel, sino que empaqueta solo lo necesario para tu app 💁‍♂️mucho más ligero y portátil.


🚨 🚨 ¿Sabemos qué es una imagen, un contenedor, un volumen y lo que hace el docker compose? 🚨 🚨

## 3. Instalaciones

### Instalar Docker en varios sistemas operativos

- **[Docker Desktop](https://www.docker.com/products/docker-desktop/)** (para Windows y macOS)
  - Es una interfaz gráfica (o aplicación local) que facilita la creación, ejecución y gestión de contenedores en tu computadora.Es una plataforma todo-en-uno que incluye:
    
    - `Docker Engine`: El motor que permite construir y correr contenedores localmente
    - `Docker Compose`: Una herramienta para definir y correr aplicaciones multi-contenedor mediante un archivo docker-compose.yml
    - `Máquina virtual`: En macOS y Windows, Docker Desktop utiliza una VM (máquina virtual) para ejecutar Linux, ya que Docker depende del kernel de Linux
      
  - Entre las funciones de Docker Desktop está construir imágenes Docker desde un Dockerfile y ejecutar y gestionar contenedores localmente.
    <kbd><img src="https://jorgebenitezlopez.com/github/docker-container.png" style="border:1px solid grey"></kbd>

- **Docker CLI** (para Linux)
  - En Linux, Docker se instala directamente como una herramienta de línea de comandos (CLI) que se gestiona desde el terminal.
  - Los comandos permiten construir imágenes, ejecutar contenedores y gestionar el ecosistema de manera directa.
  - Instrucciones para instalar en:[Ubuntu](https://docs.docker.com/engine/install/ubuntu/), [CentOS](https://docs.docker.com/engine/install/centos/), [Debian](https://docs.docker.com/engine/install/debian/)
    <kbd><img src="./img/terminaldocker.png" style="border:1px solid grey"></kbd>

- **[Docker Hub](https://hub.docker.com/)** (para la nube)
  - Es el repositorio oficial donde se almacenan y comparten imágenes de Docker.Los usuarios pueden descargar imágenes públicas o almacenar las suyas propias.Es un recurso clave para obtener imágenes oficiales de sistemas operativos, aplicaciones y servicios.Su función es similar a un repositorio de código como GitHub o GitLab.
  - Docker Hub nos permite:
    - Almacenar y compartir imágenes Docker públicamente o de manera privada (2 con la cuenta privada)
    - Distribuir tus imágenes a otras personas o sistemas (en un entorno de producción, CI/CD, etc.)
    - Descargar imágenes preconstruidas de aplicaciones populares (Nginx, Redis, MongoDB, Node.js, etc.), que puedes usar como base para tus propios contenedores

<kbd><img src="https://jorgebenitezlopez.com/github/dockerhub.png" style="border:1px solid grey"></kbd>

### <a href="/PROBLEMAS_PROCESADORES.md" target="_blank">¿Tienes problemas con los procesadores?</a>


## 4. Flujo de trabajo en docker

<p>
  <img src="./img/flujodocker.png" style="width: 100%">
</p>

Son 3 pasos: 

>1. **Disponer de un Dockerfile**  
>2. **Construir la imagen**  a partir del dockerfile con `docker build`
>3. **Levantar un contenedor**  de la imagen creada con `docker run` 

El flujo de trabajo en Docker sigue varios pasos clave que van desde la creación de una imagen hasta la ejecución de un contenedor. A continuación, te explicamos el proceso paso a paso, además de algunos conceptos relacionados con la configuración de variables y el ciclo de vida de los contenedores.

### 4.1. Creación del Dockerfile

Se puede hacer con `docker init` te detecta el code que tienes

Ejemplo básico de un Dockerfile:

      FROM python:3.8-slim # Instalamos una imagen
      COPY . /app # Copiamos un directorio
      WORKDIR /app # Creamos un directorio
      RUN pip install -r requirements.txt # Instalamos
      CMD ["python", "app.py"] # Ejecutamos

### 4.1. Construcción de la Imagen

      docker build -t mi-aplicacion:latest .

### 4.2 Configurar variables en el Dockerfile de forma sencilla

Durante la ejecución de un contenedor, puedes pasar variables de entorno para personalizar la configuración sin modificar el código. Puedes definir variables directamente en el Dockerfile o pasar valores al momento de ejecutar el contenedor.

      # En el dockerfile
      ENV API_KEY=myapikey

      # O pasarla en momento de ejecución
      docker run -e API_KEY=myapikey mi-aplicacion

📌 Importante diferenciar entre ARG y ENV. ARG define variables que se pasan en tiempo de construcción. ENV define variables que se usan en tiempo de ejecución dentro del contenedor.

    ARG BUILD_ENV=development
    ENV APP_ENV=${BUILD_ENV}
    RUN echo "Building for environment: ${APP_ENV}``

### 4.3 Ejecutar un contenedor

      docker run -d --name mi-contenedor -p 8080:80 mi-aplicacion

Este comando ejecuta el contenedor en segundo plano (-d), asigna el nombre mi-contenedor, y mapea el puerto 80 del contenedor al puerto 8080 del host (-p 8080:80).

### 4.4 Ejecutar varios contenedores a la vez

En Docker Compose, un servicio es una definición que describe un contenedor que deseas ejecutar. Cada servicio corresponde a un contenedor, y en el archivo docker-compose.yaml, puedes definir varios servicios para que trabajen juntos como parte de una aplicación más grande

Cuando ejecutas `docker-compose up` o `docker compose up --build` (Fuerza la reconstrucción de las imágenes antes de levantar los contenedores), Docker Compose realiza las siguientes tareas: Crea y ejecuta los contenedores para cada servicio, Asigna una red. Monta volúmenes y expone puertos.

Ejemplo de Docker compose:

    services:
      app:
        image: mi-aplicacion:latest
          - "8080:8080"
        depends_on:
          - db  # 'app' depende del servicio 'db'
      db:
        image: postgres:13  # Este servicio es la base de datos
        environment:
          - POSTGRES_USER=user
          - POSTGRES_PASSWORD=secret
          - POSTGRES_DB=mi_bd

📌 Importante recordar que docker-compose puede acceder al .env

🚨 🚨 ¿Podemos explicar el flujo de trabajo con Docker? ¿Diferenciamos entre ARG y ENV? ¿Entendemos la función de docker-compose? 🚨 🚨

## 5. Comandos esenciales

- **`docker --version`**: Verifica la versión de Docker instalada.
- **`docker pull <imagen>`**: Descarga una imagen de Docker del repositorio de Docker Hub.
- **`docker push <imagen>`**: Sube una imagen a un registro (registry).
- **`docker images`**: Lista todas las imágenes descargadas en tu máquina.
- **`docker run <imagen>`**: Ejecuta un contenedor a partir de una imagen.
- **`docker ps`**: Muestra todos los contenedores en ejecución.
- **`docker ps -a`**: Muestra todos los contenedores, incluso los que no están en ejecución.
- **`docker stop <id-contenedor>`**: Detiene un contenedor en ejecución.
- **`docker start <id-contenedor>`**: Inicia un contenedor que ha sido detenido.
- **`docker rm <id-contenedor>`**: Elimina un contenedor detenido.
- **`docker rmi <imagen>`**: Elimina una imagen de Docker.
- **`docker build -t <nombre>:<tag> <directorio>`**: Construye una imagen a partir de un Dockerfile.
- **`docker exec -it <id-contenedor> <comando>`**: Ejecuta un comando dentro de un contenedor en ejecución.
- **`docker logs <id-contenedor>`**: Muestra los logs de un contenedor.
- **`docker-compose up`**: Inicia los contenedores definidos en un archivo `docker-compose.yml`.
- **`docker-compose down`**: Detiene y elimina los contenedores definidos en `docker-compose.yml`.
- **`docker inspect <id-contenedor>`**: Muestra detalles de un contenedor o una imagen.
- **`docker stats`**: Muestra el uso de recursos de los contenedores en ejecución.
- **`docker prune`**: Elimina imágenes no utilizadas.

🚨 🚨 ¿Me suenan los comandos esenciales? 🚨 🚨

## 6. Subir a docker hub

- Haces login con `docker login`
- Subes tu imagen a Docker hub etiquetada correctamente. Ejemplo: `docker tag nombre-de-tag:latest tu-username/nombre-de-imagen:latest`
- [Trabajar con etiquetas](https://www.returngis.net/2019/02/publicar-tu-imagen-en-docker-hub/)

<kbd><img src="./img/renderdocker.png" style="border:1px solid grey"></kbd>

## 7. Recursos Adicionales

- Ejemplo de node en /node_docker
- Ejemplo con Python en /python_docker
- [Introduction to Docker (PDF)](https://jorgebenitezlopez.com/tiddlywiki/pro/Introduction-to-docker-dark.pdf)
- [Curso práctico de Docker y Kubernetes](https://www.freecodecamp.org/news/learn-docker-and-kubernetes-hands-on-course/)

**[⬆ back to top](#índice)**
