**Alumno:** Tomas Cassanelli  
**Clave UCC:** 2102092

## Trabajo Práctico 6 - Pruebas Unitarias

### 1- Objetivos de Aprendizaje
 - Adquirir conocimientos sobre conceptos referidos a pruebas unitarias (unit tests).
 - Generar y ejecutar pruebas unitarias utilizando frameworks disponibles.

### 2- Unidad temática que incluye este trabajo práctico
Este trabajo práctico corresponde a la unidad Nº: 5 (Libro Ingeniería de Software: Cap 8)

### 3- Consignas a desarrollar en el trabajo práctico:

### 4- Desarrollo:
#### Prerequisitos:
- Node.js
- Angular CLI
- .NET Core 8 SDK

#### 4.1 Creación de una BD SQL Server para nuestra App
A\. Crear una BD Azure SQL Database.
![](Extras/image.png)
![](Extras/image-1.png)
![](Extras/image-2.png)


#### 4.2 Obtener nuestra App
A\. Clonar el repo https://github.com/ingsoft3ucc/Angular_WebAPINetCore8_CRUD_Sample.git
![](Extras/image-3.png)

B\. Seguir las instrucciones del README.md del repo clonado prestando atención a la modificación de la cadena de conexión en el appSettings.json para que apunte a la BD creada en 4.1 
![](Extras/image-4.png)

C\. Navegar a http://localhost:7150/swagger/index.html y probar uno de los controladores para verificar el correcto funcionamiento de la API.
   ```bash
   dotnet run --urls "http://localhost:7150"
   ```
![](Extras/image-5.png)

D\. Navegar a http://localhost:4200 y verificar el correcto funcionamiento de nuestro front-end Angular
   ```bash
  ng serve -o 
   ```
![](Extras/image-6.png)

E\. Una vez verificado el correcto funcionamiento de la Aplicación procederemos a crear un proyecto de pruebas unitarias para nuestra API.

#### 4.3 Crear Pruebas Unitarias para nuestra API
A\. En el directorio raiz de nuestro repo crear un nuevo proyecto de pruebas unitarias para nuestra API 
```bash
dotnet new xunit -n EmployeeCrudApi.Tests
```
![](Extras/image-7.png)

B\. Instalar dependencias necesarias

Primero, instala las siguientes bibliotecas mediante NuGet:
- **Moq**
- **xUnit** 
- **Microsoft.EntityFrameworkCore.InMemory**

```bash
cd EmployeeCrudApi.Tests 
dotnet add package Moq
dotnet add package xunit
dotnet add package Microsoft.EntityFrameworkCore.InMemory
```

C\. Editar archivo UnitTest1.cs reemplazando su contenido.
![](Extras/image-8.png)

D\. Renombrar archivo UnitTest1.cs por EmployeeControllerUnitTests.cs
![](Extras/image-9.png)

E\. Editar el archivo EmployeeCrudApi.Tests/EmployeeCrudApi.Tests.csproj para agregar una referencia a nuestro proyecto de EmployeeCrudApi reemplazando su contenido por
![](Extras/image-10.png)

F\. Ejecutar los siguientes comandos para ejecutar nuestras pruebas y verificar que se hayan ejecutado correctamente.
![](Extras/image-11.png)

G\. Verificar que no estamos usando una dependencia externa como la base de datos.

H\. Modificar la cadena de conexión en el archivo appsettings.json para que use un usuario o password incorrecto y recompilar el proyecto EmployeeCrudApi
![](Extras/image-12.png)
![](Extras/image-13.png)

I\. Verificar que nuestro proyecto ya no tiene acceso a la BD navegando a http://localhost:7150/swagger/index.html y probando uno de los controladores:
![](Extras/image-14.png)

J\. En la carpeta de nuestro proyecto EmployeeCrudApi.Tests volver a correr las pruebas
![](Extras/image-15.png)

Se verifica la ejecucion de las pruebas inclusive sin tener acceso a la BD, lo que confirma que es efectivamente un conjunto de pruebas unitarias que no requieren de una dependencia externa para funcionar.

K\. Modificar la cadena de conexión en el archivo appsettings.json para que use el usuario y password correcto y recompilar el proyecto EmployeeCrudApi
![](Extras/image-16.png)
![](Extras/image-17.png)

L\. Verificar que nuestro proyecto vuelve a tener acceso a la BD navegando a http://localhost:7150/swagger/index.html y probando uno de los controladores:
![](Extras/image-18.png)

#### 4.4 Creamos pruebas unitarias para nuestro front de Angular:

A\. Nos posicionamos en nuestro proyecto de front, en el directorio EmployeeCrudAngular/src/app y editamos el archivo app.component.spec.ts reemplazando su contenido por:
![](Extras/image-19.png)

B\. Creamos el archivo employee.service.spec.ts reemplazando su contenido por:
![](Extras/image-20.png)

C\. Editamos el archivo employee.component.spec.ts ubicado en la carpeta **employee** reemplazando su contenido por:
![](Extras/image-21.png)

D\. Editamos el archivo addemployee.component.spec.ts ubicado en la carpeta **addemployee** reemplazando su contenido por:
![](Extras/image-22.png)

E\. En el directorio raiz de nuestro proyecto EmployeeCrudAngular ejecutamos el comando 
```bash
ng test
```
F\. Vemos que se abre una ventana de Karma con Jasmine en la que nos indica que los tests se ejecutaron correctamente
![](Extras/image-23.png)

G\. Vemos que los tests se ejecutaron correctamente:
![](Extras/image-24.png)

H\. Verificamos que no esté corriendo nuestra API navegando a http://localhost:7150/swagger/index.html y recibiendo esta salida:
![](Extras/image-25.png)

I\. Los puntos F y G nos indican que se han ejecutado correctamente las pruebas inclusive sin tener acceso a la API, lo que confirma que es efectivamente un conjunto de pruebas unitarias que no requieres de una dependencia externa para funcionar.

#### 4.5 Agregamos generación de reporte XML de nuestras pruebas de front.
Para cuando integremos nuestras pruebas en un pipeline de Build, vamos a necesitar el resultado devuelto por nuestras pruebas para reportarlas junto a las pruebas de back que se reportan automaticamente. 
![image](https://github.com/user-attachments/assets/12c430fd-13e7-4370-8c2a-a2f2756bd33f)


Haremos los siguientes pasos para prepararnos:
A\. Instalamos dependencia karma-junit-reporter
![](Extras/image-26.png)

B\. En el directorio raiz de nuestro proyecto (al mismo nivel que el archivo angular.json) creamos un archivo karma.conf.js con el siguiente contenido
![](Extras/image-27.png)

C\. Ejecutamos nuestros test de la siguiente manera:
![](Extras/image-28.png)

D\. Verificamos que se creo un archivo test-result.xml en el directorio test-results que está al mismo nivel que el directorio src
![](Extras/image-29.png)
![](Extras/image-30.png)

#### 4.6 Modificamos el código de nuestra API y creamos nuevas pruebas unitarias:

A\. Realizar al menos 5 de las siguientes modificaciones sugeridas al código de la API:
![](Extras/image-31.png)

B\. Crear las pruebas unitarias necesarias para validar las modificaciones realizadas en el código
![](Extras/image-32.png)
![](Extras/image-34.png)
![](Extras/image-35.png)
![](Extras/image-36.png)
![](Extras/image-37.png)

Si ejecutamos los casos optimos en cada uno de estos tests obtendriamos error, dado a que fueron generados para chequear errores:
![](Extras/image-38.png)

Si ejecutamos los casos erroneos en cada uno de estos tests obtendriamos aprobado, dado a que fueron generados para chequear eso:
![](Extras/image-39.png)

#### 4.7 Modificamos el código de nuestro Front y creamos nuevas pruebas unitarias:
![](Extras/image-42.png)
 
A\. Realizar en el código del front las mismas modificaciones hechas a la API. 
![](Extras/image-43.png)

B\. Las validaciones deben ser realizadas en el front sin llegar a la API, y deben ser mostradas en un toast como por ejemplo https://stackblitz.com/edit/angular12-toastr?file=src%2Fapp%2Fapp.component.ts o https://stackblitz.com/edit/angular-error-toast?file=src%2Fapp%2Fcore%2Frxjsops.ts
![](Extras/image-44.png)
![](Extras/image-45.png)
![](Extras/image-46.png)
![](Extras/image-47.png)
![](Extras/image-48.png)
![](Extras/image-49.png)

C\. Crear las pruebas unitarias necesarias en el front para validar las modificaciones realizadas en el código del front.
![](Extras/image-51.png)
![](Extras/image-50.png)
![](Extras/image-52.png)

### 6-  Presentación del trabajo práctico.
- Subir un doc al repo con las capturas de pantalla de los pasos realizados
- Subir el proyecto a un repo para poder evaluar, revisar y ejecutar el código y las pruebas unitarias

### 7-  Criterio de Calificación
Los pasos 4.1 al 4.5 representan un 60% de la nota total, los pasos 4.6 y subsiguientes representan el 40% restante.




