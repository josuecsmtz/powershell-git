# **💻 PowerShell y Git: Sus usos y comandos básicos**

![Asignatura](https://img.shields.io/badge/Asignatura-Metodolog%C3%ADa%20de%20la%20Programaci%C3%B3n-orange)
![Fecha](https://img.shields.io/badge/Fecha-08--09--2025-yellow)


---
## 📖 Contenido

* [¿Qué es PowerShell? - Comandos básicos](#-qué-es-powershell---comandos-básicos)
    - [`cd` - Cambiar directorio](#cd-change-directory)
    - [`ls` - Listar contenido](#ls-list)
    - [`mkdir` - Crear directorios](#mkdir-make-directory)
    - [`clear` - Limpiar terminal](#clear)
    - [`pwd` - Mostrar ruta](#pwd-print-working-directory)
    - [`cat` - Mostrar contenido de archivos](#cat-alias-de-get-content-de-concatenate)
    - [`cp` - Copiar archivos](#cp-copy)
    - [`mv` - Mover o renombrar archivos](#mv-move)
* [¿Qué es Git? - Comandos básicos](#️-qué-es-git---comandos-básicos)
    - [`init` - Inicializar repositorio](#init)
    - [`config` - Configuración de usuario](#config)
    - [`add` - Añadir archivos al staging](#add)
    - [`commit` - Confirmar cambios](#commit)
    - [`status` - Estado del repositorio](#status)
    - [`log` - Historial de commits](#log)
    - [`diff` - Diferencias entre archivos/commits](#diff)
    - [`branch` - Ramas](#branch)
    - [`checkout` - Cambiar o restaurar archivos/ramas](#checkout)
    - [`merge` - Fusionar ramas](#merge)
    - [`clone` - Clonar repositorios](#clone)
    - [`push` - Enviar commits al remoto](#push)
    - [`pull` - Traer cambios del remoto](#pull)
    - [`fetch` - Descargar cambios sin fusionar](#fetch)
*  [Funcionamiento de Git - Creación de un repositorio a partir PowerShell](#️-funcionamiento-de-git---creación-de-un-repositorio-a-partir-powershell)

---

## ❓ ¿Qué es PowerShell? - Comandos básicos

<div style="text-align: center;">
  <img src="https://upload.wikimedia.org/wikipedia/commons/2/2f/PowerShell_5.0_icon.png" alt="Logo de PowerShell" width="200">
</div>

*PowerShell* es interfaz que permite al usuario interactuar con el sistema operativo, automatizar tareas y manipular archivos y carpetas mediante instrucciones y scripts.

Los siguientes son algunos de sus comandos básicos:

- [cd](#cd-change-directory)
- [ls](#ls-list)
- [mkdir](#mkdir-make-directory)
- [clear](#clear)
- [pwd](#pwd-print-working-directory)
- [cat](#cat-alias-de-get-content-de-concatenate)
- [cp](#cp-copy)
- [mv](#mv-move)

---

### `cd` (change directory): 

Cambia la ruta o el directorio actual. Para usarlo se escribe `cd` seguido del *nombre de la carpeta* o ruta. 
    
```bash
# Acceder a carpeta de documentos estando en el directorio correcto
cd .\Documents\ 
# Acceder mediante la ruta
cd \Users\USERNAME\Documents\
```

 Para retroceder en una ruta se agrega un `..` después del comando. Usando `../..` se puede retroceder varias rutas a la vez.
    
Para retroceder a la carpeta de usuario usar `cd ~`.

<div style="background-color:#eaf7ff; padding:10px; border-left:10px solid #1e90ff; margin-bottom:15px;">
💡 Tip: Para autocompletar comandos y rutas se puede usar la tecla <code>Tab</code>.
</div>

---

### `ls` (list): 

Muestra el contenido del directorio actual. También tiene argumentos opcionales para mostrar contenido en específico.

```bash
# Mostrar archivos y carpetas del directorio actual
ls

# Mostrar solo archivos
ls -File

# Mostrar solo carpetas
ls -Directory

# Mostrar solo archivos .txt
ls *.txt
```

---

### `mkdir` (make directory): 

Crea uno o más directorios nuevos en el sistema de archivo.
    
```bash
# Crear un directorio llamado "tarea" en la ruta actual
mkdir tarea
# Crear varios directorios a la vez en la ruta actual
mkdir tarea1, tarea2
```

<div style="background-color:#eaf7ff; padding:10px; border-left:10px solid #1e90ff; margin-bottom:15px;">
💡 Tip: Sí el nombre de la carpeta tiene espacios, escribir el nombre entre comillas. Ej: <code>mkdir "tarea de Charly"</code>
</div>

También se puede crear un directorio en cualquier ubicación del sistema de archivos especificando una ruta absoluta o relativa. 

```bash
# Crear carpeta en Documents usando ruta absoluta
mkdir C:\Users\USERNAME\Documents\tarea
# Crear carpeta en Documents usando ruta relativa (suponiendo que ya estamos en C:\Users\USERNAME)
mkdir Documents\tarea
```

<div style="background-color:#eaf7ff; padding:10px; border-left:5px solid #1e90ff; margin-bottom:15px;">
💡 Tip: Para crear carpetas en lugares específicos, puedes usar símbolos especiales:  
- <code>.</code> = carpeta actual  
- <code>..</code> = carpeta padre (un nivel arriba). 

Ejemplo:  
<code>mkdir .\tarea</code> → crea la carpeta dentro de la carpeta actual.  
<code>mkdir ..\tarea2</code> → crea la carpeta en la carpeta padre.
</div>

---

### `clear`: 

Limpia la terminal del PowerShell.

```bash
# Limpiar toda la consola
clear
```

---

### `pwd` (print working directory):  

Muestra la ruta completa del directorio en el que te encuentras actualmente. 

```bash
# Mostrar la ruta completa del directorio actual
pwd
```

---

### `cat` (alias de Get-Content, de "concatenate"): 

Muestra el contenido de uno o varios archivos en la terminal.

```bash
# Ver el contenido de un archivo de texto llamado "hOLI"
cat "hOLI.txt"
# Ver el contenido de varios archivos juntos
cat archivo1.txt, archivo2.txt
```

<div style="background-color:#eaf7ff; padding:10px; border-left:5px solid #1e90ff; margin-bottom:15px;">
💡 Tip: También puede combinar archivos o redirigir su contenido, pero para esto es más recomendable usar <code>Out-File</code> o <code>Set-Content</code>.
</div>

---

### `cp` (copy): 
Copia y duplica archivos o carpetas seleccionadas a una carpeta de destino.

```bash
# Copiar el archivo "hOLI.txt" a otra carpeta
cp hOLI.txt C:\Users\USERNAME\Documents
# Copiar varios archivos de texto a la vez
cp *.txt C:\Users\USERNAME\Documents
```
Para copiar carpetas completas agregar `-Recurse` al final de la línea de código.

<div style="background-color:#eaf7ff; padding:10px; border-left:5px solid #1e90ff; margin-bottom:15px;">
💡 Tip: Sí no se incluye el <code>-Recurse</code> la carpeta se copiará vacía.
</div>

---

### `mv` (move): 
Mover o renombrar archivos o carpetas.

```bash
# Mover archivo a otra carpeta
mv hOLI.txt C:\Users\USERNAME\Documents\tarea

# Renombrar archivo
mv hOLI.txt hOLIIIIII.txt

# Mover carpeta completa con contenido
mv "tarea de Charly" C:\Users\USERNAME\Documents -Recurse
```

---
## 🛠️ ¿Qué es Git? - Comandos básicos

<div style="text-align: center;">
  <img src="https://www.innerzaurus.com/wp-content/uploads/2020/08/Logo-de-Git.png" alt="Logo de Git" width="200">
</div>


Git es un sistema de control de versiones que permite registrar y guardar un historial de cambios en archivos y proyectos a lo largo del tiempo dentro de un repositorio, manteniendo un registro completo de todas las modificaciones. Esto facilita la colaboración entre varios desarrolladores, el seguimiento de cambios, la recuperación de versiones anteriores, entre otros beneficios.

Algunos de sus comandos principales son:

- [init](#init)
- [config](#config)
- [add](#add)
- [commit](#commit)
- [status](#status)
- [log](#log)
- [diff](#diff)
- [branch](#branch)
- [checkout](#checkout)
- [merge](#merge)
- [clone](#clone)
- [push](#push)
- [pull](#pull)
- [fetch](#fetch)

<div style="background-color:#eaf7ff; padding:10px; border-left:10px solid #1e90ff; margin-bottom:15px;">
💡 <strong>Tip:</strong> Todos los siguientes comandos deben iniciarse con el subcomando <code>git</code>, ya que es el programa que ejecuta cada instrucción.
</div>

---

### `init`:

Inicializa un nuevo repositorio de Git en el directorio actual, transformándolo en un proyecto versionado. Este comando crea un subdirectorio oculto llamado .git que contiene toda la configuración, el historial de cambios (commits) y los metadatos necesarios para el control de versiones del proyecto. 

#### Ejemplo:

Crear un nuevo repositorio Git en la carpeta que queremos versionar (por ejemplo, estando en la ruta C:/Users/USERNAME/Documents/Tarea de Charly). (Para saber como acceder a un directorio consultar el [comando cd](#cd-change-directory))

```bash
git init

# Salida típica:
# Initialized empty Git repository in C:/Users/USERNAME/Documents/Tarea de Charly/.git/
```

<div style="background-color:#eaf7ff; padding:10px; border-left:5px solid #1e90ff; margin-bottom:15px;"> 💡 Tip: Aunque, una vez ejecutado el comando <code>init</code>, Git ya esté inicializado en el proyecto, no guarda versiones automáticamente. Para registrar cambios en el historial es necesario hacerlo manualmente, mediante otros comandos que se verán en la lista. </div>

---

### `config`:

Configura opciones del proyecto o del usuario que Git utilizará en los commits y otras operaciones. Esto incluye nombre, correo electrónico y otras preferencias del repositorio. Es importante establecer estas configuraciones antes de hacer los primeros commits, para que la información quede registrada correctamente en el historial.

#### Ejemplo:

```bash
# Configurar el nombre del usuario
git config --global user.name "nombre"

# Configurar el correo electrónico del usuario
git config --global user.email "ejemplo@correo.com"

# Ver todas las configuraciones actuales
git config --list
```

<div style="background-color:#eaf7ff; padding:10px; border-left:5px solid #1e90ff; margin-bottom:15px;"> 💡 Tip: <strong>--global</strong> aplica la configuración a todos los repositorios del usuario. Para configuraciones específicas de un proyecto, omitir <code>--global</code> y se aplicará solo al repositorio actual. </div>

---

### `add`:

Mueve los cambios del directorio de trabajo al "área de preparación" (staging area) para que sean incluidos en la próxima confirmación (git commit). Sirve para seleccionar y preparar los archivos que se guardarán en el historial del proyecto, ya que el comando git commit solo opera sobre los cambios presentes en esta área. Necesita y contempla algunos argumentos.

#### Ejemplo:

```bash
# Añadir un archivo específico
git add archivo.txt

# Añadir todos los cambios en el proyecto
git add .

# Añadir todos los cambios incluyendo eliminaciones
git add -A

# Añadir solo los cambios en archivos ya existentes
git add -u
```

---

### `commit`:

Registra de manera permanente en el historial de Git los cambios que se encuentran en el staging area (zona de preparación). Cada commit incluye un identificador único (hash), la fecha, el autor y un mensaje que describe el cambio realizado. Esto permite mantener un registro claro y organizado de la evolución del proyecto. Antes de ejecutar git commit, se utiliza el comando git add para pasar o "preparar" los cambios en el proyecto que se almacenarán en una confirmación. 

#### Ejemplo:

Suponiendo que el proyecto se llama "sistema-notas" y ya se han preparado los cambios con [git add](#add).

```bash
# Guardar los cambios en el historial con un mensaje descriptivo
git commit -m "Se agregó la funcionalidad para calcular el promedio de las notas"

# Salida típica:
# [main 1a2b3c4] Se agregó la funcionalidad para calcular el promedio de las notas
#  2 files changed, 25 insertions(+), 2 deletions(-)
```

<div style="background-color:#eaf7ff; padding:10px; border-left:5px solid #1e90ff; margin-bottom:15px;"> 💡 <strong>Tip:</strong> Se recomienda configurar el <code>user.name</code> y el <code>user.email</code> con <code>git config</code> antes de realizar el primer <code>git commit</code>. De lo contrario, Git no permitirá registrar cambios hasta que estos datos estén definidos. </div>

---

### `status`:

Muestra el estado de los archivos en el repositorio, indicando cuáles han sido modificados, cuáles están preparados para ser confirmados mediante `commit` (en la "staging area") y cuáles no son rastreados por Git (untracked). Este comando permite ver en qué etapa se encuentran los cambios, facilitando la gestión del proyecto. 

#### Ejemplo:

```bash
# Ver el estado del proyecto
git status

# Salida típica:
# On branch main
# Your branch is up to date with 'origin/main'.
#
# Changes to be committed:
#   (use "git restore --staged <file>..." to unstage)
#       modified:   archivo1.txt
#
# Changes not staged for commit:
#   (use "git add <file>..." to update what will be committed)
#       modified:   archivo2.txt
#
# Untracked files:
#   (use "git add <file>..." to include in what will be committed)
#       archivo3.txt
```

---

### `log`:

Muestra el historial de confirmaciones (commits) de un repositorio Git, permitiendo a los usuarios ver detalles como el autor, la fecha y el mensaje de cada cambio realizado, o filtrar el historial para encontrar modificaciones específicas.

#### Ejemplo:

```bash
# Ver el historial completo de commits en orden cronológico inverso
git log

# Ver el historial resumido en una sola línea por commit
git log --oneline

# Ver los últimos 3 commits
git log -3

# Ver commits hechos por un autor específico
git log --author="Juan Pérez"

# Ver commits que modificaron un archivo en particular
git log -- archivo.txt
```

---

### `diff`:

Muestra las diferencias entre dos conjuntos de datos en un repositorio de Git, como el estado de los archivos de trabajo, el index, ramas o commits. Permite ver qué se ha modificado, qué se ha añadido o eliminado, y en general, proporciona una "ventana" a los cambios dentro del proyecto. Es muy útil para revisar qué modificaciones se han hecho antes de confirmarlas (`commit`) y suele usarse junto con `git status` y `git log` para analizar el estado actual del proyecto. Contempla algunos argumentos opcionales.

#### Ejemplo:

```bash
# Ver qué archivos se modificaron en el proyecto y todavía NO se han guardado en el historial de Git
git diff

# Comparar los cambios que ya están preparados para commit (staged) con el último commit
git diff --cached

# Comparar diferencias entre dos commits específicos
git diff <commit1> <commit2>

# Comparar cambios entre dos ramas
git diff main feature-branch
```

<div style="background-color:#eaf7ff; padding:10px; border-left:5px solid #1e90ff; margin-bottom:15px;">
💡 Tip: <code>git diff</code> muestra las diferencias entre archivos, commits o ramas sin modificar nada. Es ideal para revisar cambios antes de hacer un <code>git commit</code>.
</div>

---

### `branch`:

Permite crear nuevas ramas, enumerar las ramas existentes, cambiarles el nombre y eliminarlas, lo que permite trabajar en paralelo en distintas funcionalidades sin afectar la rama principal (generalmente llamada master o main).

#### Ejemplo:

```bash
# Listar todas las ramas existentes en el proyecto
git branch

# Crear una nueva rama llamada "dev"
git branch dev

# Renombrar la rama actual a "main"
git branch -m main

# Renombrar una rama específica, por ejemplo "dev" → "development"
git branch -m dev development

# Eliminar una rama llamada "sandbox"
git branch -d sandbox
```

<div style="background-color:#eaf7ff; padding:10px; border-left:5px solid #1e90ff; margin-bottom:15px;"> 💡 Tip: Una vez creada la rama con <code>git branch</code>, para cambiarse a ella es necesario usar <code>git checkout nombre-de-rama</code> o el más moderno <code>git switch nombre-de-rama</code>. </div>

---

### `checkout`:

Sirve principalmente para dos cosas: cambiar entre ramas del repositorio, actualizando el directorio de trabajo a la versión de la rama deseada, y restaurar archivos a una versión anterior.

#### Ejemplo:

```bash
# Cambiar a una rama existente llamada "dev"
git checkout dev

# Restaurar un archivo específico a su versión en la rama actual
git checkout -- archivo.txt

# Restaurar un archivo a una versión específica de un commit
git checkout <commit> -- archivo.txt
```

<div style="background-color:#eaf7ff; padding:10px; border-left:5px solid #1e90ff; margin-bottom:15px;"> 💡 Tip: También se puede usar <code>git checkout -b nombre-nueva-rama </code> para crear una nueva rama y cambiar a ella en un solo paso.  </div>

---

### `merge`:

Combina los cambios de una rama específica con otra rama en el proyecto, fusionando los cambios registrados en la rama de origen dentro de la rama actual. Este comando es útil para unir desarrollos paralelos y mantener el proyecto actualizado con distintas funcionalidades sin perder el historial de modificaciones.

#### Ejemplo:

Supongamos que tenemos un proyecto llamado "ProyectoGit", la rama principal es 'main' y la rama de desarrollo es 'dev' y se desea fusionar los cambios de 'dev' a 'main' una vez probados.

```bash
# Cambiar a la rama principal
git checkout main

# Fusionar los cambios de la rama dev
git merge dev

# Salida típica:
# Updating a1b2c3d..d4e5f6g
# Fast-forward
# archivo1.txt | 2 +-
# archivo2.txt | 5 +++--
# 2 files changed, 4 insertions(+), 3 deletions(-)
```

<div style="background-color:#eaf7ff; padding:10px; border-left:5px solid #1e90ff; margin-bottom:15px;">
💡 Tip: El comando <code>merge</code> funciona <strong>solo localmente</strong>, uniendo ramas dentro del proyecto en la máquina. Para actualizar la versión <strong>remota</strong> y que otros colaboradores vean los cambios fusionados, se debe usar <code>git push</code>.
</div>

---

### `clone`:

 Apunta a un repositorio Git existente y crea un clon o copia completa de él en un nuevo directorio, en otra ubicación . El repositorio original puede estar ubicado en el sistema de archivos local o en una máquina remota, incluyendo todo su historial de versiones y ramas.

 #### Ejemplo:

```bash
# Clonar un repositorio local en otra carpeta
git clone <ruta-del-repositorio-original> <ruta-del-nuevo-clon>

# Clonar un repositorio remoto en tu computadora a la ruta actual
git clone https://github.com/usuario/nombre-del-repositorio.git 

# Salida típica:
# Cloning into 'nombre-del-repositorio'...
# remote: Enumerating objects: 10, done.
# remote: Counting objects: 100% (10/10), done.
# Receiving objects: 100% (10/10), done.

# También se puede especificar la ruta de destino
git clone <url-del-repositorio> <ruta-de-destino>
```
<div style="background-color:#eaf7ff; padding:10px; border-left:10px solid #1e90ff; margin-bottom:15px;">
💡 Tip: Git admite distintos tipos de URL para los repositorios:  
- <strong>HTTPS</strong>: fácil de usar y seguro, requiere usuario/token para escribir.  
- <strong>SSH</strong>: más seguro para operaciones de escritura usando llaves.  
- <strong>Git</strong>: solo lectura, rápido pero no seguro para escribir.  
- <strong>Ruta local</strong>: clonar repositorios que ya existen en tu máquina o red local.
</div>

---

### `push`:

Envía las confirmaciones (**commits**) locales al repositorio remoto en la nube (**GitHub, GitLab, Bitbucket, etc**), permitiendo que otros colaboradores tengan acceso a las actualizaciones. Generalmente se indica el nombre del remoto (por convención, *origin*) y la rama a la que se quiere enviar (ej. *main* o *dev*).

#### Ejemplo:

Supongamos que tenemos un proyecto llamado "Tarea1" ya versionado con Git, con [commit](#commit)s confirmados en la rama "dev".

```bash
# Enviamos la rama "dev" al repositorio remoto llamado "origin"
git push origin dev

# Salida típica:
# Enumerating objects: 5, done.
# Counting objects: 100% (5/5), done.
# Delta compression using up to 12 threads
# Compressing objects: 100% (3/3), done.
# Writing objects: 100% (3/3), 1.23 KiB | 1.23 MiB/s, done.
# Total 3 (delta 2), reused 0 (delta 0), pack-reused 0
# To https://github.com/usuario/Tarea1.git
#    abc1234..def5678  dev -> dev

# Subir a un repositorio remoto específico y todas las ramas que contiene
git push --all <NOMBRE-REMOTO>

# Subir a una rama específica con el parámetro force ignorarando los cambios locales hechos al repositorio Git en Github
git push --force <NOMBRE-REMOTO> <RAMA-REMOTA>
```

<div style="background-color:#eaf7ff; padding:10px; border-left:5px solid #1e90ff; margin-bottom:15px;">
💡 Tip: Al hacer <code>git push</code> por primera vez, Git puede pedir autenticación con GitHub. 
Esto puede hacerse directamente en la terminal o a través de una ventana emergente de inicio de sesión, 
dependiendo de cómo esté configurado Git.
</div>

---

### `pull`:

Actualiza un repositorio local con los últimos cambios de un repositorio remoto, descargando y fusionando automáticamente el contenido en la rama actual. Es fundamental en equipos de desarrollo, ya que permite a los colaboradores obtener las últimas versiones del código que otros han subido al repositorio remoto y asegura que el repositorio local esté sincronizado con la versión más reciente del proyecto. 

#### Ejemplo:

Supongamos que el proyecto se llama "sistema-notas" y se está en la rama principal (main) y se desea traer los cambios desde GitHub.

```bash
git pull origin main

# Salida típica:
# remote: Enumerating objects: 5, done.
# remote: Counting objects: 100% (5/5), done.
# remote: Compressing objects: 100% (3/3), done.
# remote: Total 3 (delta 2), reused 0 (delta 0), pack-reused 0
# Unpacking objects: 100% (3/3), done.
# From https://github.com/usuario/sistema-notas
#    1a2b3c4..d5e6f7g  main       -> origin/main
# Updating 1a2b3c4..d5e6f7g
# Fast-forward
#  archivo1.txt | 2 +-
#  archivo2.txt | 5 +++--
#  2 files changed, 4 insertions(+), 3 deletions(-)
```

<div style="background-color:#eaf7ff; padding:10px; border-left:5px solid #1e90ff; margin-bottom:15px;"> 💡 Tip: Al usar <code>git pull</code> se recomienda estar en la rama correcta (ejemplo: <code>main</code> o <code>dev</code>), ya que los cambios descargados se fusionarán automáticamente en esa rama. </div>

---

### `fetch`:

Descarga commits, archivos y referencias de un repositorio remoto a tu repositorio local, sin modificar la rama de trabajo actual. Esto permite ver qué cambios hay en el repositorio remoto antes de aplicarlos en la rama.

#### Ejemplo:

````bash
git fetch origin main
````
Este comando trae los últimos cambios de la rama main desde el remoto llamado origin, pero no los fusiona automáticamente con la rama local.

`git fetch` es muy útil para revisar los cambios disponibles en el remoto antes de hacer un merge o un pull. Se puede combinar con comandos como:

````
git log HEAD..origin/main
````
para ver exactamente qué commits nuevos hay en el remoto.


---
## 🗂️ Funcionamiento de Git - Creación de un repositorio a partir PowerShell

Para empezar a usar Git, primero debemos iniciar un repositorio usando algunos de los comandos que ya hemos visto [[Regresar al contenido]](#-contenido). 

En el caso de Windows, lo haremos de la siguiente manera:

1. **Crear carpeta y entrar en ella con PowerShell (`mkdir`, `cd`):**
    
    Para trabajar con Git, primero necesitaremos tener una carpeta o proyecto a versionar.

    Primero abriremos PowerShell. Escribe en el buscador de Windows “Windows PowerShell” y selecciona.

    <div style="text-align: center; margin-bottom: 10px;">
    <img src="https://i.imgur.com/zKtoA8E.gif" alt="¿Cómo abrir PowerShell?" width="500">
    </div>

    <div style="background-color:#eaf7ff; padding:10px; border-left:5px solid #1e90ff; margin-bottom:15px;"> 💡 Tip: Git también incluye su propia terminal, conocida como Git Bash, que permite ejecutar comandos de Linux en Windows. Sin embargo, se recomienda PowerShell, ya que es más rápida y práctica para los ejercicios y proyectos que realizaremos, además de su integración nativa con Windows. </div>

    Ahora nos situaremos en la ruta en la que queremos crear nuestra carpeta, en caso del ejemplo la crearemos en la carpeta documentos mediante el comando [mkdir](#mkdir-make-directory) y posteriormente nos situamos en ella mediante el comando [cd](#cd-change-directory).

    <div style="text-align: center; margin-bottom: 10px;">
    <img src="https://i.imgur.com/zaHJRUx.gif" alt="Crear carpeta" width="500">
    </div>

    <div style="background-color:#eaf7ff; padding:10px; border-left:5px solid #1e90ff; margin-bottom:15px;"> 💡 Tip: Recuerda que si estás en otra ruta ya establecida puedes subir niveles usando <code>cd ..</code>. </div>


2. **Inicializar el repositorio (`git init`):**

   Ya localizados en la ruta de nuestra carpeta a versionar iniciaremos un repositorio de git usando el comando [git init](#init).

    <div style="text-align: center; margin-bottom: 10px;">
    <img src="https://i.imgur.com/0FoJdeF.gif" alt="Crear carpeta" width="500">
    </div>

3. **Agregar archivos (`git add`):**

    Una vez creado el repositorio en nuestra carpeta, crearemos un archivo cualquiera, en nuestro caso será un .txt, este se encontrará en el area de untracked files (archivos no seguidos por Git), posteriormente lo añadiremos al area de trabajo o staging area con el comando [`git add -A`](#add).

    <div style="text-align: center; margin-bottom: 10px;">
    <img src="https://i.imgur.com/XM2BJ79.gif" alt="Añadir a Staging Zone" width="500">
    </div>

    <div style="background-color:#eaf7ff; padding:10px; border-left:5px solid #1e90ff; margin-bottom:15px;"> 💡 Tip: Recuerda que para saber en que area de Git se encuentra nuestro archivo usamos <code>git status</code>. </div>

4. **Realizar un primer commit. Añadir el archivo al repositorio mediante (`git commit`).**

    Ya teniendo nuestro archivo en la staging zone o area de preparación, podemos proceder a subir esa version del archivo al repositorio Git mediante el comando [`git commit -m`](#commit)

    <div style="text-align: center; margin-bottom: 10px;">
    <img src="https://i.imgur.com/YscFCdk.gif" alt="Añadir al repositorio" width="500">
    </div>

Y listo, así la versión de nuestro archivo, en ese momento, ya está guardada en el repositorio local de Git. El subirlo al repositorio en la nube será visto en la siguiente sección.
