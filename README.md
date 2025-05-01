# Sistema de Diagnóstico Simple con Flask y Docker

Este proyecto consiste en una aplicación web simple desarrollada con Flask que permite realizar un diagnóstico básico basado en la temperatura, la frecuencia cardíaca y la saturación de oxígeno ingresadas por el usuario.

## Estructura del Proyecto

El proyecto se organiza de la siguiente manera:

.
├── app.py
├── templates/
│   └── index.html
└── Dockerfile
└── README.md
└── requirements.txt


* `app.py`: Contiene el código del servidor Flask, incluyendo las rutas y la lógica de diagnóstico.
* `templates/index.html`: Es el frontend de la aplicación, un formulario para ingresar los signos vitales.
* `Dockerfile`: **Archivo existente que define los pasos para construir la imagen de Docker de la aplicación.**
* `README.md`: Este archivo, que proporciona información sobre el proyecto y cómo ejecutarlo.
* `requirements.txt`: **Archivo existente que lista las dependencias de Python necesarias para la aplicación.**

## Prerrequisitos

Antes de comenzar, asegúrate de tener instalado lo siguiente en tu sistema:

* **Docker**: Puedes descargarlo e instalarlo desde la [página oficial de Docker](https://www.docker.com/get-started).

## Paso a Paso: Crear la Imagen de Docker y Ejecutar la Aplicación

Sigue estos pasos para construir la imagen de Docker y ejecutar la aplicación en un contenedor:

**1. Construir la imagen de Docker:**

Abre una terminal o símbolo del sistema, navega al directorio donde guardaste los archivos (`app.py`, `templates/`, `Dockerfile`, `requirements.txt`), y ejecuta el siguiente comando para construir la imagen de Docker:

```bash
docker build -t sistema-diagnostico .
docker build: Es el comando para construir una imagen de Docker.
-t sistema-diagnostico: Asigna el nombre sistema-diagnostico a la imagen que se va a crear. Puedes elegir otro nombre si lo prefieres.
.: Indica que el contexto de la construcción (los archivos necesarios) se encuentra en el directorio actual.
Docker utilizará el Dockerfile existente para descargar la imagen base de Python, instalar las dependencias listadas en requirements.txt y copiar tu código dentro de la imagen.

2. Ejecutar el contenedor de Docker:

Una vez que la imagen se haya construido exitosamente, puedes ejecutar un contenedor basado en esa imagen con el siguiente comando:

Bash

docker run -p 5000:5000 sistema-diagnostico
docker run: Es el comando para ejecutar un contenedor a partir de una imagen.
-p 5000:5000: Realiza el mapeo de puertos. El primer 5000 se refiere al puerto en tu máquina local (host), y el segundo 5000 es el puerto dentro del contenedor donde la aplicación Flask está sirviendo la aplicación. Esto permite acceder a la aplicación desde tu navegador.
sistema-diagnostico: Es el nombre de la imagen que quieres ejecutar.
3. Acceder a la aplicación:

Una vez que el contenedor esté en ejecución, abre tu navegador web y navega a la siguiente dirección:

http://localhost:5000/
Deberías ver el formulario de captura de signos vitales de tu aplicación.

4. Detener el contenedor:

Para detener el contenedor cuando hayas terminado, puedes encontrar su ID o nombre usando el comando:

Bash

docker ps
Luego, utiliza el comando docker stop seguido del ID o el nombre del contenedor:

Bash

docker stop <ID_DEL_CONTENEDOR>
Reemplaza <ID_DEL_CONTENEDOR> con el ID real de tu contenedor.