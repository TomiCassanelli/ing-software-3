## Trabajo Práctico 8 - Implementación de Contenedores en Azure y Automatización con Azure CLI

### 1- Objetivos de Aprendizaje

Al finalizar esta sesión, los estudiantes serán capaces de:

1. **Seleccionar el servicio de contenedores más adecuado para diferentes escenarios de despliegue en la nube.**
2. **Configurar y utilizar Azure Container Registry (ACR) para almacenar imágenes Docker de manera segura.**
3. **Automatizar la creación y gestión de recursos en Azure mediante scripts y comandos de Azure CLI.**
4. **Utilizar variables y secretos de manera eficiente y segura en los pipelines de Azure DevOps.**
5. **Desarrollar y ejecutar un pipeline CI/CD completo que incluya la construcción y despliegue de contenedores en Azure.**

### 2- Unidad temática que incluye este trabajo práctico
Este trabajo práctico corresponde a la unidad Nº: 2 (Libro Ingeniería de Software: Unidad 18)

### 3- Consignas a desarrollar en el trabajo práctico:
---

### 4- Desarrollo:
#### Prerequisitos:
 - Azure CLI instalado 

#### 4.1 Modificar nuestro pipeline para construir imágenes Docker de back y front y subirlas a ACR
- ##### 4.1.1 Crear archivos DockerFile para nuestros proyectos de Back y Front. En la raiz de nuestro repo crear una carpeta docker con dos subcarpetas api y front, dentro de cada una de ellas colocar los dockerfiles correspondientes para la creación de imágenes docker en función de la salida de nuestra etapa de Build y Test
![](Extras/image.png)

- DockerFile Back:
![](Extras/image-2.png)
- DockerFile Front:
![](Extras/image-1.png)

- ##### 4.1.2 Crear un recurso ACR en Azure Portal siguiendo el instructivo 5.1
![](Extras/image-3.png)

- ##### 4.1.3 Modificar nuestro pipeline en la etapa de Build y Test
- Luego de la tarea de publicación de los artefactos de Back agregar la tarea de publicación de nuestro dockerfile de back para que esté disponible en etapas posteriores:
![](Extras/image-4.png)

- Luego de la tarea de publicación de los artefactos de Front agregar la tarea de publicación de nuestro dockerfile de front para que esté disponible en etapas posteriores:
![](Extras/image-5.png)

- ##### 4.1.4 En caso de no contar en nuestro proyecto con una ServiceConnection a Azure Portal para el manejo de recursos, agregar una service connection a Azure Resource Manager como se indica en instructivo 5.2 
![](Extras/image-6.png)

- ##### 4.1.5 Agregar a nuestro pipeline variables 
![](Extras/image-7.png)

- ##### 4.1.6 Agregar a nuestro pipeline una nueva etapa que dependa de nuestra etapa de Build y Test
- Agregar tareas para generar imagen Docker de Back
![](Extras/image-8.png)
![](Extras/image-9.png)

- ##### 4.1.7 - Ejecutar el pipeline y en Azure Portal acceder a la opción Repositorios de nuestro recurso Azure Container Registry. Verificar que exista una imagen con el nombre especificado en la variable backImageName asignada en nuestro pipeline
![](Extras/image-10.png)
![](Extras/image-11.png)

- ##### 4.1.8 - Agregar tareas para generar imagen Docker de Front (DESAFIO)
- ###### 4.1.8.1 A la etapa creada en 4.1.6 Agregar tareas para generar imagen Docker de Front
![](Extras/image-12.png)
![](Extras/image-13.png)
![](Extras/image-14.png)
![](Extras/image-15.png)

- ##### 4.1.9 - Agregar a nuestro pipeline una nueva etapa que dependa de nuestra etapa de Construcción de Imagenes Docker y subida a ACR

- ###### 4.1.9.1 Agregar variables a nuestro pipeline:
![](Extras/image-16.png)

- ###### 4.1.9.2 Agregar variable secreta cnn-string-qa desde la GUI de ADO que apunte a nuestra BD de SQL Server de QA como se indica en el instructivo 5.3
![](Extras/image-17.png)
  	    
- ###### 4.1.9.3 Agregar tareas para crear un recurso Azure Container Instances que levante un contenedor con nuestra imagen de back
![](Extras/image-18.png)

- ##### 4.1.10 - Ejecutar el pipeline y en Azure Portal acceder al recurso de Azure Container Instances creado. Copiar la url del contenedor y navegarlo desde browser. Verificar que traiga datos.
![](Extras/image-19.png)
![](Extras/image-20.png)

- ##### 4.1.11 - Agregar tareas para generar un recurso Azure Container Instances que levante un contenedor con nuestra imagen de front (DESAFIO)
- A la etapa creada en 4.1.9 Agregar tareas para generar contenedor en ACI con nuestra imagen de Front
![](Extras/image-26.png)
![](Extras/image-27.png)

- Tener en cuenta que el contenedor debe recibir como variable de entorno API_URL el valor de una variable container-url-api-qa definida en nuestro pipeline.
![](Extras/image-21.png)

- Para que el punto anterior funcione el código fuente del front debe ser modificado para que la url de la API pueda ser cambiada luego de haber sido construída la imagen. Se deja un ejemplo de las modificaciones a realizar en el repo https://github.com/ingsoft3ucc/CrudAngularConEnvironment.git
![](Extras/image-22.png)
![](Extras/image-23.png)
![](Extras/image-25.png)
![](Extras/image-30.png)
![](Extras/image-24.png)
![](Extras/image-28.png)
![](Extras/image-29.png)
![](Extras/image-33.png)

- ##### 4.1.12 - Agregar tareas para correr pruebas de integración en el entorno de QA de Back y Front creado en ACI. (DESAFIO)
![](Extras/image-32.png)
![](Extras/image-31.png)
![](Extras/image-34.png)
![](Extras/image-35.png)

- ##### 4.1.13 - Agregar etapa que dependa de la etapa de Deploy en ACI QA y genere contenedores en ACI para entorno de PROD. (DESAFIO)
![](Extras/image-36.png)
![](Extras/image-37.png)
![](Extras/image-39.png)
![](Extras/image-40.png)
![](Extras/image-38.png)
![](Extras/image-41.png)
![](Extras/image-42.png)

### 6-  Presentación del trabajo práctico.
- Subir un doc al repo de GitHub con las capturas de pantalla de los pasos realizados. Debe ser un documento (md, word, o pdf), no videos. Y el documento debe seguir los pasos indicados en el Desarrollo del TP.
- Acceso al repo de Azure Devops para revisar el trabajo realizado.

### 7-  Criterio de Calificación
Los pasos 4.1 al 4.X representan un 60% de la nota total, los pasos 4.X y subsiguientes representan el 40% restante.

### 8-  Recursos Adicionales
