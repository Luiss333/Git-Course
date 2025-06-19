
# Curso de Git + GitHub 🐙

## 🧰 Instalación recomendada

- [x] Visual Studio Code (Editor de texto)
- [x] Git (Sistema de control de versiones)
- [x] Google Chrome (Navegador)

---

## 🛠 Primeros comandos

```bash
git --version      # Verifica la versión instalada
git help           # Muestra ayuda general
git help commit    # Ayuda específica sobre el comando "commit"
```

> 🔎 Cuando se muestre la ayuda en consola y aparezca `:`, presiona `Q` para salir.

---

## 👤 Configuración del usuario

```bash
git config --global user.name "Luis Gerardo Martinez Garcia"
git config --global user.email "luis.martinez0125@hotmail.com"
git config --global -e  # Abre el archivo de configuración global
```

> ✍️ En versiones antiguas se edita en consola (modo vi). Presiona `a` para editar, luego `ESC`, escribe `:wq!` y presiona `Enter` para guardar y salir.

---

## 🗂 Inicializar un repositorio

```bash
git init
```

> Crea una carpeta `.git` (¡no la modifiques ni elimines!).

---

## 📌 Estado de los archivos

```bash
git status        # Ver estado actual
git status --short  # Estado abreviado
```

Archivos en **rojo**: no rastreados.  
Archivos en **verde**: listos para commit.

---

## ➕ Añadir y remover archivos

```bash
git add index.html     # Añade un archivo
git add .              # Añade todos los archivos del directorio
git add *.html         # Añade todos los archivos con extensión .html
git add css/           # Añade una carpeta
git reset index.html   # Quita un archivo del área de staging
```

> ⚠️ El archivo `.gitkeep` en versiones antiguas debe agregarse como `.gitkeep` y no `*.gitkeep`.

---

## 💾 Realizar commits

```bash
git commit -m "Mensaje del commit"
git commit -am "Mensaje"  # Añade y comitea archivos ya rastreados
git commit --amend        # Modifica el último commit
```

---

## 🔄 Deshacer cambios

```bash
git checkout -- .            # Revierte todos los cambios al último commit
git reset --soft HEAD^       # Vuelve al commit anterior sin perder cambios
git reset --soft <commit>    # Vuelve a un commit específico
git reset --mixed <commit>   # Igual que soft, pero deja los cambios en staging
git reset --hard <commit>    # Elimina todos los cambios posteriores al commit
git reflog                   # Ver historial de cambios (incluso los perdidos)
```

---

## 🏷 Manejo de ramas

```bash
git branch                     # Ver ramas existentes
git branch nueva               # Crear nueva rama
git branch -m master main      # Renombrar rama actual
git branch --all               # Ver todas las ramas (locales y remotas)
git branch -d nueva            # Eliminar rama (si ya se hizo merge)
git branch -D nueva            # Forzar eliminación

git checkout main              # Cambiar de rama
git checkout -b nueva          # Crear y cambiar a una nueva rama
git merge nueva                # Hacer merge de la rama "nueva" a la actual
```

> 🌿 Puedes configurar el nombre de rama predeterminado:
```bash
git config --global init.defaultBranch main
```

---

## 🏷 Etiquetas (Tags)

```bash
git tag                       # Ver todas las etiquetas
git tag release               # Crear una etiqueta
git tag -d release            # Eliminar etiqueta
git tag -a v0.1.0 <commit> -m "Mensaje"  # Crear etiqueta anotada
git push --tags               # Subir etiquetas al repositorio remoto
```

---

## 📦 Stash (Guardar cambios temporalmente)

```bash
git stash save "Comentario"     # Guardar cambios
git stash list                  # Ver lista de stash
git stash show stash@{0}        # Ver detalles de un stash
git stash pop                   # Aplicar y eliminar el stash más reciente
git stash apply stash@{2}       # Aplicar un stash específico sin eliminarlo
git stash drop stash@{0}        # Eliminar stash específico
git stash clear                 # Eliminar todos los stash
git stash list --stat           # Ver detalles de cambios en todos los stash
```

---

## 🧬 Rebase (reestructura commits)

```bash
git rebase rama                   # Traer commits de otra rama
git rebase -i HEAD~4              # Reescribir últimos 4 commits (modo interactivo)
git rebase --continue             # Continuar rebase después de resolver conflicto
```

> En modo interactivo:
- `pick`: mantener commit
- `reword`: cambiar mensaje
- `squash`: fusionar con el anterior
- `edit`: modificar

---

## 🌐 Conexión con GitHub

```bash
git remote add origin https://github.com/Luiss333/liga-justicia.git
git branch -M main
git push -u origin main
git push                         # Subir cambios
git pull                         # Traer cambios del remoto
git pull origin main             # Especificar rama
git pull --all                   # Traer todo, incluso ramas nuevas
```

> ⚠️ Si aparece un warning al hacer pull:
```bash
git config --global pull.ff only
```

---

## 🔄 Eliminar ramas en remoto

```bash
git push origin :rama
git remote prune origin   # Actualizar ramas eliminadas en remoto
```

---

## 🐛 Issues y Pull Requests

- **Issue**: Crear solicitud, duda o mejora.
- **Pull request**: Solicita revisión de cambios antes de hacer merge.

```bash
git commit -am "Fixes #1: Mensaje"  # Cierra automáticamente una issue
```

---

## 🧠 Alias útiles

```bash
git config --global alias.s "status --short"
git config --global alias.lg "log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(bold yellow)%d%C(reset)' --all"
```

---

## 🛠 Solución a errores comunes

- **Problema CRLF** (fin de línea en Windows):
```bash
git config core.autocrlf true
```

---

## 🧾 Configuración global de Git (`.gitconfig`)

```ini
[core]
	editor = "C:\Users\Luis\AppData\Local\Programs\Microsoft VS Code\bin\code" --wait
[user]
	name = Luis Gerardo Martinez Garcia
	email = luis.martinez0125@hotmail.com
[init]
	defaultBranch = main
[alias]
	s = status -sb
	lg = log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(bold yellow)%d%C(reset)' --all
```

---

> 🚨 **No compartas tokens públicos.** Si lo hiciste, elimínalo de GitHub y genera uno nuevo.
