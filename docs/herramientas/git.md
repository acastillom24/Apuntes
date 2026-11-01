# [Git](https://git-scm.com/)

## Git remote

Conecta tu repositorio local con el remoto:

```bash
git remote add origin https://github.com/tu-usuario/nombre-del-repositorio.git
```

Para ver los remotos configurados:

```bash
git remote -v
```

## Git clone

Descargar el código fuente desde un repositorio remoto:

```bash
git clone https://github.com/usuario/nombre-del-repositorio.git
```

## Git branch

Para trabajar con ramas: crearlas, renombrarlas, listarlas y eliminarlas.

### Crear una nueva rama

```bash
git branch <nombre-de-la-rama>
```

### Renombrar una rama

```bash
git branch -m <antigua-rama> <nueva-rama>
```

Para renombrar la rama en la que estás actualmente:

```bash
git branch -m <nueva-rama>
```

!!! warning
    `-M` (mayúscula) fuerza el renombrado aunque ya exista una rama con ese nombre, sobrescribiéndola. Usa `-m` salvo que sepas lo que haces.

### Visualización de ramas

```bash
git branch --list
```

Incluyendo las ramas remotas:

```bash
git branch -a
```

### Borrar una rama

```bash
git branch -d <nombre-de-la-rama>
```

## Git checkout / Git switch

Permite navegar entre ramas. Recuerda que hay algunos pasos que debes seguir antes del cambio:

- Los cambios en tu rama actual deben ser confirmados o almacenados en el guardado rápido (stash) antes de cambiar de rama.
- La rama a la que te quieras cambiar debe existir en local.

```bash
git checkout <nombre-de-la-rama>
```

Adicionalmente, puedes crear una rama y cambiarte a ella en un solo paso:

```bash
git checkout -b <nombre-de-tu-rama>
```

!!! tip "Alternativa moderna"
    Desde Git 2.23 existe `git switch`, pensado solo para cambiar de rama:

    ```bash
    git switch <nombre-de-la-rama>      # cambiar de rama
    git switch -c <nombre-de-tu-rama>   # crear y cambiar
    ```

## Git status

Proporciona información sobre la rama actual, incluyendo:

- Si la rama actual está actualizada.
- Si hay algo para confirmar, enviar o recibir (pull).
- Si hay archivos en preparación (staged), sin preparación (unstaged) o que no están recibiendo seguimiento (untracked).
- Si hay archivos creados, modificados o eliminados.

```bash
git status
```

## Git add

Para incluir los cambios de uno o más archivos en tu siguiente commit.

### Añadir un único archivo

```bash
git add <archivo>
```

### Añadir todos los cambios a la vez

```bash
git add -A
```

## Git commit

Establece un punto de control en el proceso de desarrollo al cual puedes volver más tarde si es necesario.

```bash
git commit -m "mensaje de confirmación"
```

## Git push

Para enviar los cambios al servidor remoto.

```bash
git push <nombre-remoto> <nombre-de-tu-rama>
```

Si tu rama ha sido creada recientemente, puede que tengas que cargar y subir tu rama con el siguiente comando.

```bash
git push --set-upstream <nombre-remoto> <nombre-de-tu-rama>
```

o

```bash
git push -u origin <nombre-de-tu-rama>
```

## Git pull

Para recibir actualizaciones del repositorio remoto. Este comando es una combinación de `git fetch` y `git merge`, lo que significa que recogerás actualizaciones del repositorio remoto y las aplicarás inmediatamente en local.

```bash
git pull <nombre-remoto>
```

## Git revert

Para deshacer los cambios que hemos realizado. Una manera segura para deshacer commits es utilizar `git revert`, que crea un nuevo commit que invierte los cambios. Para ver nuestro historial de commits, primero necesitamos usar:

```bash
git log --oneline
```

Si la lista es larga, se abre un paginador: muévete con las flechas y sal con ++q++.

Entonces, solo necesitamos especificar el código (hash) que encontrarás junto al commit que queremos deshacer:

```bash
git revert <hash>
```

Git abrirá el editor para confirmar el mensaje del commit. En Vim, guarda y sal con `:wq`. Para evitar el editor y usar el mensaje por defecto:

```bash
git revert --no-edit <hash>
```

## Git merge

Integra las características de tu rama con todos los commits realizados a las ramas `dev` (o `main`). Es importante que estés en la rama que va a **recibir** los cambios.

Por ejemplo, cuando quieres fusionar tu rama de características en la rama `dev`:

- Muévete a la rama `dev`

```bash
git checkout dev
```

- Actualiza tu rama `dev` local con lo que haya en el remoto

```bash
git pull
```

!!! note
    `git fetch` solo descarga los cambios del remoto, pero **no** actualiza tu rama local; por eso aquí se usa `git pull`.

- Fusiona tu rama de características en la rama `dev`

```bash
git merge <nombre-de-la-rama>
```
