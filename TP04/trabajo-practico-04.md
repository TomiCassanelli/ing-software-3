**Alumno:** Tomas Cassanelli  
**Clave UCC:** 2102092

## Trabajo Práctico 4 - Azure Devops Pipelines

### 1- Objetivos de Aprendizaje
 - Adquirir conocimientos acerca de las herramientas de integración continua presentes en ADO.
 - Configurar este tipo de herramientas.
 - Implementar procesos de construcción automatizados simples.
 
### 2- Unidad temática que incluye este trabajo práctico
Este trabajo práctico corresponde a la unidad Nº: 3 (Libro Continuous Delivery: Cap 3)


CI (Continuous Integration), Continuous Deployment y Continuous Delivery son tres prácticas clave en la ingeniería de software que se utilizan para mejorar la calidad del software y acelerar el proceso de desarrollo. Aunque están relacionadas y a menudo se utilizan juntas, tienen diferencias clave:

**Continuous Integration (CI):**

CI es una práctica que implica la integración constante de cambios de código en un repositorio compartido por parte de varios desarrolladores.
Los desarrolladores envían regularmente su código al repositorio compartido (a menudo varias veces al día).
Cada vez que se envía código, se activan pruebas automáticas para verificar la calidad y la compatibilidad del código.
El objetivo principal de CI es detectar y resolver problemas de integración de código de manera temprana y continua, lo que evita la acumulación de errores.

**Continuous Delivery** 
En Continuous Delivery, después de que el código pasa por CI y se considera estable, se automatiza el proceso de empaquetado y preparación para la entrega.
Sin embargo, la entrega real al entorno de producción se realiza manualmente después de una revisión y aprobación humanas.

**Continuous Deployment (CD)**
Se refiere a la práctica de automatizar y acelerar el proceso de entrega de software al entorno de producción.
En Continuous Development, una vez que el código pasa por el proceso de CI y se considera estable, se automatiza la entrega del software al entorno de producción sin intervención manual adicional.
Esto implica la automatización de tareas como pruebas adicionales, empaquetado, despliegue y configuración en el entorno de producción.

En resumen, CI se centra en la integración continua de cambios de código y pruebas automáticas, mientras que Continuous Delivery y Continuous Deployment se centran en la automatización del proceso de entrega de software al entorno de producción, con Continuous Delivery deteniéndose antes de la entrega real y Continuous Deployment automatizando todo el proceso hasta la entrega al entorno de producción. 
Estas prácticas son esenciales en el desarrollo de software ágil y permiten la entrega rápida y confiable de software de alta calidad.

### 3- Consignas a desarrollar en el trabajo práctico:

 **Azure DevOps Pipelines**
  - Breve descripción de Azure DevOps Pipelines.
  - Tipos de Pipelines: Build y Deploy.
  - Diferencias entre editor clásico y YAML.
  - Agentes MS y Self-Hosted


### 4- Pasos del TP
 - 4.1 Verificar acceso a Pipelines concedido
 ![](Extras/image.png)
 ![](Extras/image-1.png)
 ![](Extras/image-2.png)
 ![](Extras/image-3.png)

 - 4.2 Agregar en pipeline YAML una tarea de Publish. 
 ![](Extras/image-4.png)
 ![](Extras/image-5.png)
 ![](Extras/image-6.png)

 - 4.3 Explicar por qué es necesario contar con una tarea de Publish en un pipeline que corre en un agente de Microsoft en la nube.

**La tarea de Publish en un pipeline en la nube es esencial para guardar y compartir los resultados generados. Esto asegura que no se pierdan cuando el agente se apague, permite su reutilización en otros procesos, y facilita el control y registro de las versiones.**

 - 4.4 Descargar el resultado del pipeline y correr localmente el software compilado.
  ![](Extras/image-7.png)
  ![](Extras/image28.png)
  ![](Extras/image29.png)

 **dotnet SimpleWebAPI.dll   -> Diapo 7, instalar Dotnet, angular y node**
 - 4.5 Habilitar el editor clásico de pipelines. Explicar las diferencias claves entre este tipo de editor y el editor YAML.
 ![](Extras/image-8.png)
 ![](Extras/image-9.png)

 - 4.6 Crear un nuevo pipeline con el editor clásico. Descargar el resultado del pipeline y correr localmente el software compilado.
 ![](Extras/image-10.png)
 ![](Extras/image-11.png)
 ![](Extras/image-12.png)
 ![](Extras/image-30.png)
 ![](Extras/image-31.png)

 - 4.7 Configurar CI en ambos pipelines (YAML y Classic Editor). Mostrar resultados de la ejecución automática de ambos pipelines al hacer un commit en la rama main.
 ![](Extras/image-13.png)
 ![](Extras/image-14.png)
 
 - 4.8 Explicar la diferencia entre un agente MS y un agente Self-Hosted. Qué ventajas y desventajas hay entre ambos? Cuándo es conveniente y/o necesario usar un Self-Hosted Agent?
 **Agente MS: Es un agente proporcionado por Microsoft que corre en la nube. Es fácil de configurar y Microsoft se encarga de su mantenimiento y escalabilidad.**
 **Agente Self-Hosted: Es un agente que configuras y mantienes en tu propia infraestructura, ya sea en servidores locales o en la nube. Es conveniente usar un agente Self-Hosted cuando necesitas un control total del entorno, tienes requisitos específicos de hardware/software**

 - 4.8 Crear un Pool de Agentes y un Agente Self-Hosted
  ![](Extras/image-15.png)
  ![](Extras/image-16.png)
  ![](Extras/image-17.png)
  ![](Extras/image-18.png)
  ![](Extras/image-19.png)

 - 4.9 Instalar y correr un agente en nuestra máquina local.
  ![](Extras/image-20.png)
  ![](Extras/image-21.png)
  ![](Extras/image-22.png)

 - 4.10 Crear un pipeline que use el agente Self-Hosted alojado en nuestra máquina local.
  ![](Extras/image-23.png)
  ![](Extras/image-24.png)

 - 4.11 Buscar el resultado del pipeline y correr localmente el software compilado.
  ![](Extras/image-25.png)
  ![](Extras/image-26.png)
  ![](Extras/image-27.png)

 - 4.12 Crear un nuevo proyecto en ADO clonado desde un repo que contenga una aplicación en Angular como por ejemplo https://github.com/ingsoft3ucc/angular-demo-project.git
  ![](Extras/image-32.png)
  ![](Extras/image-33.png)

 - 4.13 Configurar un pipeline de build para un proyecto de tipo Angular como el clonado.
  ![](Extras/image-34.png)
  ![](Extras/image-35.png)

 - 4.14 Habilitar CI para el pipeline.
  ![](Extras/image-36.png)

 - 4.15 Hacer un cambio a un archivo del proyecto (algún cambio en el HTML que se renderiza por ejemplo) y verificar que se ejecute automáticamente el pipeline.
  ![](Extras/image-37.png)
  ![](Extras/image-38.png)
  ![](Extras/image-39.png)

 - 4.16 Descargar el resultado del pipeline y correr en un servidor web local el sitio construido.
  ![](Extras/image-40.png)
  ![](Extras/image-41.png)

 - 4.17 Mostrar el antes y el después del cambio.
  ![](Extras/image-42.png)
  ![](Extras/image-43.png)

### 5- Presentación del trabajo práctico.
Subir un doc al repo con las capturas de pantalla de los pasos realizados y colocar en el excel de repos (https://docs.google.com/spreadsheets/d/1mZKJ8FH390QHjwkABokh3Ys6kMOFZGzZJ3-kg5ziELc/edit?gid=0#gid=0) la url del proyecto de AzureDevops.

### 6- Criterio de Calificación
Los pasos 4.1 al 4.11 representan un 60% de la nota total, los pasos 4.12 al 4.17 representan el 40% restante
