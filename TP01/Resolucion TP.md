**Alumno:** Tomas Cassanelli  
**Clave UCC:** 2102092

## Trabajo Practico N°1 - Git Básico
---

### 1) Instalar Git
  - Bajar e instalar el cliente git
  ![](Extras/image1.png)
---

### 2) Crear un repositorio local y agregar archivos
  - Crear un repositorio local en un nuevo directorio.
  ![](Extras/image2.png)

  - Agregar un archivo Readme.md, agregar algunas líneas con texto a dicho archivo.
  ![](Extras/image3.png)

  - Crear un commit y proveer un mensaje descriptivo.
  ![](Extras/image4.png)
---

### 3) Configuración del Editor Predeterminado.
---

### 4) Creación de Repos 01 -> Crearlo en GitHub, clonarlo localmente y subir cambios.
  - Crear una cuenta en https://github.com -> https://github.com/TomiCassanelli

  - Crear un nuevo repositorio en dicha página con el Readme.md por defecto.
    ![](Extras/image5.png)
    
  - Clonar el repo remoto en un nuevo directorio local.
  ![](Extras/image6.png)

  - Editar archivo Readme.md agregando algunas lineas de texto.
  ![](Extras/image7.png)

  - Editar (o crear si no existe) el archivo .gitignore agregando los archivos *.bak
  ![](Extras/image8.png)

  - Crear un commit y proveer un mensaje descriptivo.
  ![](Extras/image9.png)

  - Intentar un push al repo remoto.
  ![](Extras/image10.png)

  - En caso de ser necesario configurar las claves SSH requeridas y reintentar el push.
---

### 5) Creación de Repos 02 -> Crearlo localmente y subirlo a GitHub
  - Crear un repo local
  ![](Extras/image11.png) 

  - Agregar archivo Readme.md con algunas lineas de texto
  - Crear archivo .gitignore  
  ![](Extras/image12.png) 
  ![](Extras/image13.png) 

  - Crear un commit y proveer un mensaje descriptivo
  ![](Extras/image15.png) 
  
  - Crear repo remoto en GitHub
  ![](Extras/image16.png) 

  - Asociar repo local con remoto y Subir cambios.
  ![](Extras/image14.png)
---

### 6) Ramas
  - Crear una nueva rama
  ![](Extras/image17.png)

  - Cambiarse a esa rama
  ![](Extras/image18.png)
  
  - Hacer un cambio en el archivo Readme.md y hacer commit
  ![](Extras/image19.png)

  - Revisar la diferencia entre ramas
  ![](Extras/image20.png)
---

### 7) Merges
  - Hacer un merge FF
  ![](Extras/image21.png)

  - Borrar la rama creada
  ![](Extras/image22.png)

  - Ver el log de commits
  ![](Extras/image23.png)

  - Repetir el ejercicio 6 para poder hacer un merge con No-FF
  ![](Extras/image24.png)
  ![](Extras/image25.png)
---

### 8) Resolución de Conflictos
  - Crear una nueva rama conflictBranch
  ![](Extras/image26.png)

  - Realizar una modificación en la linea 1 del Readme.md desde main y commitear
  ![](Extras/image27.png)
  ![](Extras/image28.png)

  - En la conflictBranch modificar la misma línea del Readme.md y commitear
  ![](Extras/image29.png)
  ![](Extras/image30.png)

  - Ver las diferencias con git difftool main conflictBranch
  ![](Extras/image31.png)
  ![](Extras/image32.png)

  - Cambiarse a la rama main e intentar mergear con la rama conflictBranch
  ![](Extras/image33.png)
  ![](Extras/image34.png)

  - Resolver el conflicto con git mergetool
  ![](Extras/image35.png)
  ![](Extras/image36.png)

  - Agregar .orig al .gitignore
  ![](Extras/image37.png)

  - Hacer commit y push
  ![](Extras/image38.png)
---

### 9) Familiarizarse con el concepto de Pull Request
  - Explicar que es un pull request.

Una PR es un pedido para que los cambios que se hicieron en una rama, se unan al proyecto principal. Entonces, una vez que se trabajó haciendo mejoras o correcciones, se realiza una PR para informar a otros miembros que está listo para ser añadido a la rama principal. Se revisa, y si esta todo en condiciones, esta PR se acepta y se fusionan.

  - Crear un branch local y agregar cambios a dicho branch. 
  ![](Extras/image39.png)

  - Subir el cambio a dicho branch y crear un pull request.
  ![](Extras/image40.png)

  - Completar el proceso de revisión en github y mergear el PR al branch master.
  ![](Extras/image41.png)
  ![](Extras/image42.png)
---

### 10) Algunos ejercicios online
  - Entrar a la página https://learngitbranching.js.org/
  - Completar los ejercicios **Introduction Sequence**
  - Opcional - Completar el resto de los ejercicios para ser un experto en Git!!!
  ![](Extras/image43.png)
---