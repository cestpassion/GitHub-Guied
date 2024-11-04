# 😽 Tutorial de Git
<br>

## 📄 Contenido: <br><br>
<br>

- [Descargar Git en Linux](#descargar-git-linux)
- [Descargar Git en Windows](#descargar-git-windows)
- [Configurar tu Usuario](#configurar-tu-usuario)
- [Clave SSH](#clave-ssh)
- [Comandos - Repositorios](#comandos---repositorios)
- [Branches](#branches)
- [Mensajes para Commits](#mensajes-para-commits)
- [Cheat Sheets](#cheat-sheets)
---
<br>

## 🔶 Descargar Git Linux
<br>

Para instalar Git en Linux, puedes usar el gestor de paquetes de tu distribución. Aquí están los comandos para algunas distribuciones populares:
<br>

- **Ubuntu/Debian**:

  ```bash
  sudo apt update
  sudo apt install git
  ```
>#### ⚠️ Es importante ejecutar el comando `sudo apt update` antes de instalar algo en Linux por varias razones fundamentales: actualiza la lista de paquetes disponibles; asegura que estás instalando la versión más reciente; sincroniza con los repositorios; mejoras de seguridad; evita problemas de dependencia.

- **Verificar la versión instalada**:
 
  ```bash
  git --version
  ```
---
<br>

## 🔶 Descargar Git Windows
<br>

Para instalar Git en Windows:

1. **Descarga el instalador**: Accede a [git-scm.com](https://git-scm.com/download/win) y descarga la versión más reciente de Git para Windows.
2. **Ejecuta el instalador**: Sigue las instrucciones del instalador, aceptando las configuraciones predeterminadas o personalizando según sea necesario. Presta atención a las opciones, especialmente en la configuración de PATH y cómo deseas usar Git Bash.
3. **Verifica la instalación**: Después de la instalación, abre la terminal (Git Bash o CMD) y ejecuta:

   ```bash
   git --version
   ```
---
<br>

## 🔶 Configurar tu Usuario
<br>

Para configurar tu nombre y correo electrónico, que se utilizarán en tus commits, usa los siguientes comandos:
<br>

### 🔹 Para configuración global (válida para todos los repositorios del usuario en la máquina):

```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tu-correo@example.com"
```
<br>

### 🔹 Para configuración local (válida solo para un repositorio específico):

```bash
git config user.name "Tu Nombre"
git config user.email "tu-correo@ejemplo.com"
```
---
<br>

## 🔶 Clave SSH
<br>
La clave SSH es una forma segura de autenticación que te permite conectarte a repositorios remotos sin tener que ingresar tus credenciales cada vez.
<br><br>

1. **Generar una nueva clave SSH**:<br><br>
   ```bash
   ssh-keygen -t rsa -b 4096 -C "tu-correo@example.com"
   ```
   Presiona `Enter` para aceptar la ubicación predeterminada del archivo, o especifica una ubicación diferente. Luego, se te pedirá que ingreses una contraseña opcional.
<br>

2. **Agregar la clave SSH al agente SSH**:<br><br>
   ```bash
   eval "$(ssh-agent -s)"
   ssh-add ~/.ssh/id_rsa
   ```
<br>

3. **Agregar la clave SSH a tu GitHub**:
   Copia el contenido de la clave pública: <br><br>
   ```bash
   cat ~/.ssh/id_rsa.pub
   ```
<br>

4. **Y agrégala en GitHub en:**
   
    `Configuración > Claves SSH y GPG > Nueva clave SSH`
<br>

- Prueba la conexión con GitHub usando:<br><br>
  ```bash
   ssh -T git@github.com
   ```
  Deberías ver un mensaje de éxito.

---
<br>

## 🔶 Comandos - Repositorios
<br>

### 🔹 Crear un nuevo repositorio:
  
  ```bash
  git init
  ```
  Inicializa un nuevo repositorio Git en el directorio actual. Esto crea un directorio `.git` que almacena todos los archivos y metadatos del repositorio.
<br>
<br>
<br>

### 🔹 Clonar un repositorio:
  
  ```bash
  git clone <url-del-repositorio>
  ```
  Clona el repositorio remoto al directorio local. Reemplaza `<url-del-repositorio>` por la URL del repositorio que deseas clonar.

  *Ejemplo:* `git clone https://github.com/usuario/repositorio.git`
<br>
<br>
<br>

### 🔹 Agregar un nuevo repositorio remoto:
  
  ```bash
  git remote add origin <url-del-repositorio>
  ```
  Agrega un repositorio remoto con el nombre `origin` (o cualquier otro nombre que elijas) y la URL proporcionada. Esto es útil para asociar un repositorio local con un repositorio remoto.

  *Ejemplo:* `git remote add origin https://github.com/usuario/repositorio.git`
<br>
<br>
<br>

### 🔹 Listar repositorios remotos:
  
  ```bash
  git remote -v
  ```
  Muestra la lista de repositorios remotos asociados al repositorio local, incluyendo sus URLs.
<br>
<br>
<br>

### 🔹 Eliminar un repositorio remoto:
  
  ```bash
  git remote remove <nombre-del-repositorio>
  ```
  Elimina un repositorio remoto asociado al repositorio local. Reemplaza `<nombre-del-repositorio>` por el nombre del repositorio remoto que deseas eliminar.

  *Ejemplo:* `git remote remove origin`
<br>
<br>
<br>

### 🔹 Cambiar la URL de un repositorio remoto:
  
  ```bash
  git remote set-url origin <nueva-url-del-repositorio>
  ```
  Actualiza la URL asociada al repositorio remoto `origin`. Usa este comando si la URL del repositorio remoto cambia.
<br>
<br>
<br>

### 🔹 Renombrar un Repositorio Remoto:
  
  ```bash
  git remote rename <nombre-antiguo> <nombre-nuevo>
  ```
  Cambia el nombre de un repositorio remoto.

  *Ejemplo:* `git remote rename origin upstream`
<br>
<br>
<br>

### 🔹 Verificar el estado de los archivos:
  
  ```bash
  git status
  ```
  Muestra el estado de los archivos en el repositorio, indicando cuáles archivos han sido modificados, cuáles están listos para el commit y cuáles no están siendo rastreados.
<br>
<br>
<br>

### 🔹 Agregar archivos al área de preparación (para ser comiteados):
  
  ```bash
  git add <archivo>
  ```
  Agrega un archivo específico al área de preparación, preparándolo para el commit. 

  *Ejemplo:* `git add index.html`
  
  **O**
  
  ```bash
  git add .
  ```
  Agrega todos los archivos modificados.
<br>
<br>
<br>

### 🔹 Hacer commit de los cambios:
  
  ```bash
  git commit -m "Mensaje del commit"
  ```
  Registra los cambios en el repositorio con un mensaje descriptivo. El mensaje debe explicar qué ha sido cambiado.

  *Ejemplo:* `git commit -m "[FEAT][WIP] Introduce un nuevo método de pago"`
<br>
<br>
<br>

### 🔹 Commitear:
  
  ```bash
  git push
  ```
  Envía los cambios del repositorio local al repositorio remoto asociado. Por defecto, el comando envía al branch actual.
<br>
<br>
<br>

### 🔹 Traer cambios del repositorio remoto:
  
  ```bash
  git pull
  ```
  Descarga e integra los cambios del repositorio remoto en el repositorio local. Combina `git fetch` y `git merge` en un solo comando.
<br>
<br>
<br>

### 🔹 Buscar actualizaciones del repositorio remoto:
  
  ```bash
  git fetch
  ```
  Descarga los cambios del repositorio remoto sin integrarlos al repositorio local. Es útil para verificar actualizaciones antes de realizar un merge o rebase.
<br>
<br>
<br>

### 🔹 Fusionar cambios del repositorio remoto:
  
  ```bash
  git merge <branch>
  ```
  Fusiona los cambios del branch especificado en el branch actual. Reemplaza `<branch>` por el nombre del branch que deseas fusionar.

  *Ejemplo:* `git merge feature/nueva-funcionalidad`

---
<br>

## 🔶 Branches
<br>

Los branches (o ramas) te permiten trabajar en diferentes versiones del proyecto simultáneamente.

### 🔹 Crear un nuevo branch:

```bash
git branch <nombre-del-branch>
```
Crea un nuevo branch.

*Ejemplo:* `git branch nueva-funcionalidad`
<br>
<br>
<br>

### 🔹 Cambiar a un branch existente:

```bash
git checkout <nombre-del-branch>
```

*Ejemplo:* `git checkout nueva-funcionalidad`
<br>
<br>
<br>

### 🔹 Crear y cambiar a un nuevo branch:

```bash
git checkout -b <nombre-del-branch>
```

*Ejemplo:* `git checkout -b nueva-funcionalidad`
<br>
<br>
<br>

### 🔹 Listar todos los branches:

```bash
git branch
```
<br>

### 🔹 Fusionar un branch en otro:

```bash
git merge <

nombre-del-branch>
```
Fusiona el branch especificado en el branch actual.
<br>
<br>
<br>

### 🔹 Rebase los cambios de un branch:
  
  ```bash
  git rebase <branch>
  ```
  Reaplica tus cambios sobre el branch especificado. El rebase es útil para mantener un historial lineal al integrar cambios.

  *Ejemplo:* `git rebase main`
<br>
<br>
<br>

### 🔹 Eliminar un branch:

```bash
git branch -d <nombre-del-branch>
```
Elimina un branch local. Usa `-D` para forzar la eliminación.

*Ejemplo:* 
`git branch -d nueva-funcionalidad`

---
<br>

## 🔶 Cheat Sheets
<br>

Aquí hay algunos enlaces a cheat sheets útiles de Git:

- [Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)
- [Git Command Cheatsheet](https://github.github.io/git-cheat-sheet/)
