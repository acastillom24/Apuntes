# Notas sobre comandos Git

## Git clone

Descargar el código fuente desde un repositorio remoto.

```bash
git clone <https://link-con-nombre-del-repositorio>
```

## Git branch

Para trabajar con ramas. Podemos crearlas, listarlas y eliminarlas.

### Crear una nueva rama
```bash
git branch <nombre-de-la-rama>
```

### Visualización de ramas
```bash
git branch --list
```

### Borrar una rama
```bash
git branch -d <nombre-de-la-rama>
```

## Git checkout

Permite navegar entre ramas, recuerda que hay algunos pasos que debes seguir antes del cambio.

- Los cambios en tu rama actual tienen que ser confirmados o almacenados en el guardado rápido (stash) antes de que cambies de rama.
- La rama a la que te quieras cambiar debe existir en local.

```bash
git checkout <nombre-de-la-rama>
```

Adicionalmente, puedes crear una rama y cambiarte a ella en un solo paso:

```bash
git checkout -b <nombre-de-tu-rama>
```

## Git status

Información necesaria sobre la rama actual como:

- Si la rama actual está actualizada.
- Si hay algo para confirmar, enviar o recibir (pull).
- Si hay archivos en preparación (staged), sin preparación(unstaged) o que no están recibiendo seguimiento (untracked).
- Si hay archivos creados, modificados o eliminados.

## Git add

Para incluir los cambios del o de los archivos en tu siguiente commit.

### Añadir un único archivo
```bash
git add <archivo>
```

### Añadir todo de una vez
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

Si tu rama ha sido creada recientemente, puede que tengas que cargar y subir tu rama cpn el siguiente comando.

```bash
git push --set-upstream <nombre-remoto> <nombre-de-tu-rama>
```

o

```bash
git push -u origin <nombre-de-tu-rama>
```

## Git pull

Para recibir actualizaciones del repositorio remoto. Este comando es una combinación del git fetch y del git merge lo cual significa que cundo usemos el git pull recogeremos actualizaciones del repositorio remoto (git fetch) e inmediatamente aplicamos estos últimos cambios en local (git merge).

```bash
git pull <nombre-remoto>
```

## Git revert

Para deshacer los cambios que hemos realizado. Una manera segura para deshacer nuestras commits es utilizar git revert. Para ver nuestro historial de commits, primero necesitamos utilizar:

```bash
git log -- oneline
```

Entonces, solo necesitamos especificar el código de comprobación que encontrarás junto al commit que queremos deshacer

```bash
git revert <código>
```

y debes presionar `shift + q`.

## Git merge

Integra las características de tu rama con todos los commits realizados a las ramas dev (o master). Es importante que recuerdes que tienes que estar en esa rama específica que quieres fusionar  con tu rama de características.

Por ejemplo, cuando quieres fusionar tu rama de características en la rama dev:

### Muévete a la rama dev
```bash
git checkout dev
```

### Actualiza tu rama dev local
```bash
git fetch
```

### Fusiona tu rama de características en la rama dev.
```bash
git merge <nombre-de-la-rama>
```