# Práctico 1 Parte 1 - ML en Producción

En este práctico abordaremos algunos conceptos básicos sobre: 

- Docker
- Ejemplo descargar imagenes


# Docker

Docker es una plataforma de virtualización de contenedores que permite a los desarrolladores crear, implementar y ejecutar aplicaciones de manera aislada en un entorno seguro y reproducible.


### Descarga e instala Docker en tu sistema operativo. 

Puedes descargar Docker Desktop para Windows o Mac desde la página oficial de Docker: https://www.docker.com/products/docker-desktop. Para sistemas Linux, sigue las instrucciones de instalación específicas para tu distribución.

Familiarízate con los conceptos básicos de Docker, como imágenes, contenedores y volúmenes. Puedes consultar la documentación oficial de Docker para obtener más información: https://docs.docker.com/get-started/

### Para crear una imagen de Docker, necesitarás seguir los siguientes pasos:

1. Crea un archivo **Dockerfile** que describa cómo construir la imagen. 

  El archivo Dockerfile es un archivo de texto que contiene una serie de instrucciones que Docker utiliza para construir la imagen. 

  El Dockerfile debe incluir información sobre la base de la imagen, los comandos necesarios para instalar las **dependencias** de la aplicación y cualquier otra configuración necesaria.

  ⚠ **Ubica el archivo Dockerfile en el directorio raíz de tu proyecto.**


2. Ejecuta el comando **docker build** para construir la imagen. 
El comando docker build toma como argumento la ruta al directorio que contiene el archivo Dockerfile. Ejemplo: `docker build -t scraper .`

3. Ejecuta el comando **docker run** y especifica la imagen que deseas utilizar. 

  Crea una carpeta llamada imagenes.
  Ejemplo: `docker run --name scraper -v "$(pwd)/imagenes:/app/imagenes" scraper python scraper.py`

Puedes usar el dashboard para ver tus contenedores, imagenes y volumenes 

- docker run: Este comando se utiliza para ejecutar un contenedor de Docker. Docker es una plataforma de contenedores que permite empaquetar aplicaciones y sus dependencias en un entorno aislado.

- --name scraper: Esto establece un nombre para el contenedor que se está creando. En este caso, el contenedor se llamará "scraper".

- -v "$(pwd)/imagenes:/app/imagenes": Este es un argumento de Docker que se utiliza para montar un volumen. Un volumen en Docker es un mecanismo que permite compartir datos entre el sistema host y el contenedor. En este caso, se está montando un volumen llamado "imagenes". A continuación, se explica en detalle:

- $(pwd)/imagenes: $(pwd) es una expansión de comandos en la que se obtiene la ruta actual del directorio de trabajo en el sistema host. Esto se utiliza para crear una ruta absoluta al directorio "imagenes" en el sistema host.

- :/app/imagenes: Esto indica la ruta dentro del contenedor donde se montará el volumen. En este caso, se montará en el directorio "/app/imagenes" dentro del contenedor.
scraper: Este es el nombre de la imagen de Docker que se utilizará para crear el contenedor. Las imágenes de Docker son plantillas que contienen un sistema de archivos y configuración para crear contenedores.

- python scraper.py: Esto es el comando que se ejecutará dentro del contenedor. En este caso, se está ejecutando un script de Python llamado "scraper.py" utilizando el intérprete de Python.


### Además del Dockerfile, para ejecutar un contenedor Docker para una aplicación Python necesitarás lo siguiente:


1. **Tu código fuente**: Deberás tener el código fuente de tu aplicación disponible para incluirlo en la imagen de Docker. Asegúrate de incluir cualquier archivo o dependencia necesaria para ejecutar la aplicación.

2. **Dependencias:** Asegúrate de tener un archivo de requisitos (como `requirements.txt`) que enumere todas las dependencias de Python que necesita tu aplicación. El archivo debe incluir todas las bibliotecas y módulos que necesitas para ejecutar tu aplicación.

3. **Comando de inicio:** Deberás especificar el comando de inicio que Docker utilizará para ejecutar tu aplicación. Para una aplicación Python, el comando de inicio suele ser algo así como python app.py.

4. **Puerto de escucha:** Si tu aplicación escucha en un puerto específico, asegúrate de exponer ese puerto al contenedor Docker. Puedes hacer esto utilizando el argumento -p del comando docker run. Por ejemplo, docker run -p 8080:8080 nombre_de_la_imagen expondrá el puerto 8080 del contenedor al puerto 8080 del host. Sino, por defecto se asigna el puerto 3000

# Dependencias de Python

Las dependencias de Python son módulos o bibliotecas que una aplicación de Python utiliza para su correcto funcionamiento. 

En Python, las dependencias se administran mediante el administrador de paquetes pip. 


Pip es una herramienta de línea de comandos que se utiliza para descargar e instalar paquetes de Python desde el Python Package Index (PyPI), que es un repositorio de paquetes de software de Python. 

Pip permite a los desarrolladores de Python definir las dependencias de su aplicación en un archivo de requisitos (`requirements.txt`), que enumera todas las bibliotecas y módulos necesarios para ejecutar la aplicación.

Las dependencias son importantes porque permiten a los desarrolladores de Python reutilizar el código existente en sus propias aplicaciones, lo que acelera el proceso de desarrollo y reduce los errores. 


### Dentro del requirements.txt

Bibliotecas de Python: Se enumeran las bibliotecas de terceros que se utilizan en la aplicación, junto con sus versiones específicas (si no se encuentra la versión especificada el sistema se encargara de tomar la versión). 

Por ejemplo, `requests==2.26.0` especifica la biblioteca Requests en la versión 2.26.0. y `requests`, no especifica la versión. 
