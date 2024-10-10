# Git_Commnds_Explanation

## Instalación de Git y configuración Inicial

En primer lugar, para poder utilizar Git deberemos instalar la herramienta. Podemos hacerlo desde la terminal con el siguiente comando:

```bash
sudo apt install git
```

En segundo lugar configuramos las credenciales de Git:

```bash
git config --global user.name "usuario"
```

```bash
git config --global user.email "usuario@mail.com"
```

A continuación se muestra una descripción detallada de los comandos más importantes de Git, tanto los básicos como los relacionados con la gestión de ramas. Estos son esenciales para trabajar con repositorios de forma eficiente.

### **1. `git clone`**
   - **Descripción**: `git clone` se utiliza para clonar un repositorio remoto a tu máquina local. Esto significa que obtienes una copia completa del historial del proyecto y todos sus archivos en tu dispositivo.

   - **Clonar un repositorio entero**:
     ```bash
     git clone https://github.com/usuario/repo.git
     ```

     Esto descargará todo el contenido del repositorio y lo pondrá en una carpeta con el nombre del repositorio en tu máquina.

   - **Clonar una rama específica**:
     Si solo quieres clonar una rama específica de un repositorio, puedes hacerlo con el siguiente comando:
     ```bash
     git clone --branch <nombre-rama> --single-branch https://github.com/usuario/repo.git
     ```

     Por ejemplo, si quieres clonar solo la rama `develop`:
     ```bash
     git clone --branch develop --single-branch https://github.com/usuario/repo.git
     ```

     - `--branch <nombre-rama>`: Especifica la rama que deseas clonar.
     - `--single-branch`: Indica que solo quieres clonar esa rama específica y no todo el historial de las demás ramas.
     - `-b <nombre-rama>: Flag alternativa para seleccionar la rama`

---


### 1. **`git add`**
   - **Descripción**: Añade cambios (archivos modificados, añadidos o eliminados) al área de "staging" o preparación. Los archivos que añades con `git add` estarán listos para ser confirmados en el próximo commit.
   - **Uso**:
     ```bash
     git add <nombre_archivo>
     git add .
     ```
     - `git add <nombre_archivo>`: Añade un archivo específico.
     - `git add .`: Añade todos los archivos y carpetas modificados dentro del directorio actual.

### 2. **`git commit`**
   - **Descripción**: Guarda los cambios añadidos con `git add` en el historial del repositorio, creando un "snapshot" (instantánea) del proyecto. Cada commit tiene un mensaje descriptivo que explica qué cambios se han realizado.
   - **Uso**:
     ```bash
     git commit -m "Mensaje del commit"
     ```
     - `-m`: Especifica el mensaje del commit en línea.

   - Si olvidaste añadir algún archivo, puedes hacerlo y luego modificar el último commit con:
     ```bash
     git commit --amend
     ```

### 3. **`git push`**
   - **Descripción**: Envía tus commits locales al repositorio remoto (por ejemplo, GitHub). Este comando sincroniza los cambios locales con el servidor remoto.
   
   - **¿Qué es un remoto?**
     Un **remoto** es un repositorio que está almacenado en un servidor externo, como GitHub o GitLab. Este remoto se utiliza para mantener una copia del código accesible para otros colaboradores o para que puedas acceder a él desde diferentes dispositivos.

     Cuando clonas un repositorio de un servidor como GitHub, el repositorio remoto se nombra por defecto como `origin`, aunque puedes tener varios remotos y darles diferentes nombres.
     
     Para ver los remotos que tienes configurados, puedes usar:
     ```bash
     git remote -v
     ```

   - **Uso de `git push`**:
     ```bash
     git push <remoto> <rama>
     git push origin main
     ```

     En este caso:
     - `origin`: Es el nombre del remoto que estás usando.
     - `main`: Es la rama que estás empujando al remoto.
   
   - Si es la primera vez que haces un `push` en una nueva rama, puedes usar el comando con la opción `-u`:
     ```bash
     git push -u origin main
     ```

     La opción `-u` establece el seguimiento (upstream) para esa rama. Esto significa que la próxima vez que uses `git push` o `git pull`, no necesitarás especificar el remoto ni la rama, ya que Git sabrá a dónde enviar o desde dónde obtener los cambios.

### 4. **`git pull`**
   - **Descripción**: Descarga los cambios más recientes del repositorio remoto y los fusiona con tu copia local. Es una combinación de `git fetch` (traer los cambios) y `git merge` (fusionarlos en tu rama actual).
   - **Uso**:
     ```bash
     git pull origin <rama>
     ```

   - Esto asegurará que tu copia local esté sincronizada con la remota antes de hacer más cambios.

### 5. **`git checkout`**
   - **Descripción**: Te permite cambiar de una rama a otra o restaurar versiones antiguas de archivos. En el caso de crear y moverse a una nueva rama, se usa con `-b`.
   - **Usos**:
     - Cambiar a una rama existente:
       ```bash
       git checkout <rama>
       ```
     - Crear una nueva rama y cambiar a ella:
       ```bash
       git checkout -b <nueva-rama>
       ```

### 6. **`git branch`**
   - **Descripción**: Lista, crea o elimina ramas en el repositorio.
   - **Uso**:
     - Listar todas las ramas locales:
       ```bash
       git branch
       ```
     - Crear una nueva rama:
       ```bash
       git branch <nueva-rama>
       ```
     - Eliminar una rama (si ya no la necesitas):
       ```bash
       git branch -d <rama>
       ```
     - Ver las ramas remotas:
       ```bash
       git branch -r
       ```

### 7. **`git merge`**
   - **Descripción**: Fusiona los cambios de una rama en otra. Generalmente, después de desarrollar en una rama (por ejemplo, `feature`), puedes fusionar esos cambios en `develop` o `main`.
   - **Uso**:
     ```bash
     git checkout <rama-donde-fusionar>
     git merge <rama-que-deseas-fusionar>
     ```
     Por ejemplo:
     ```bash
     git checkout develop
     git merge feature/nueva-funcionalidad
     ```

   - Si hay conflictos (cuando los mismos archivos se modificaron en ambas ramas), Git te pedirá que los resuelvas manualmente.

### 8. **`git fetch`**
   - **Descripción**: Trae los cambios del repositorio remoto sin fusionarlos automáticamente. Solo actualiza la información local sobre el estado del repositorio remoto.
   - **Uso**:
     ```bash
     git fetch <remoto>
     ```

### 9. **`git status`**
   - **Descripción**: Muestra el estado del repositorio, incluyendo qué archivos han sido modificados, cuáles están listos para commit (staged) y cuáles no.
   - **Uso**:
     ```bash
     git status
     ```

### 10. **`git log`**
   - **Descripción**: Muestra el historial de commits del proyecto. Puedes ver los mensajes de commit, quién realizó los cambios y cuándo.
   - **Uso**:
     ```bash
     git log
     ```

   - Para un log más compacto y visual:
     ```bash
     git log --oneline --graph
     ```

### 11. **`Cambiar de usuario`**
   - **Descripción**: Permite cambiar entre los distintos usuarios que se encuentran en el contenedor. 
      - **Uso**:
     ```bash
     su - usuario
     ```
    
### 12. **`Actualizar contraseña del usuario`**
   - **Descripción**: Permite cambiar entre la contraseña del usuario que se encuentran en el contenedor. 
      - **Uso**:
     ```bash
     sudo passwd usuario
     ```
