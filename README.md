# [Git](https://git-scm.com/)

## Git clone

Descargar el código fuente desde un repositorio remoto:

```bash
git clone <https://link-con-nombre-del-repositorio>
```

## Git branch

Para trabajar con ramas: crearlas, listarlas y eliminarlas.

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

Para recibir actualizaciones del repositorio remoto. Este comando es una combinación de git fetch y git merge, lo que significa que recogerás actualizaciones del repositorio remoto y las aplicarás inmediatamente en local.

```bash
git pull <nombre-remoto>
```

## Git revert

Para deshacer los cambios que hemos realizado. Una manera segura para deshacer commits es utilizar git revert. Para ver nuestro historial de commits, primero necesitamos usar:

```bash
git log -- oneline
```

Entonces, solo necesitamos especificar el código de comprobación que encontrarás junto al commit que queremos deshacer

```bash
git revert <código>
```

y debes presionar `shift + q`.

## Git merge

Integra las características de tu rama con todos los commits realizados a las ramas `dev` (o `master`). Es importante que estés en esa rama específica que quieres fusionar con tu rama de características.

Por ejemplo, cuando quieres fusionar tu rama de características en la rama `dev`:

- Muévete a la rama `dev`

```bash
git checkout dev
```

- Actualiza tu rama `dev` local

```bash
git fetch
```

- Fusiona tu rama de características en la rama `dev`

```bash
git merge <nombre-de-la-rama>
```

# [Winget](https://github.com/microsoft/winget-cli)

## Verificar la versión de Winget
Para comprobar la versión de Winget que tienes instalada, ejecuta:
```bash
winget --version
```

## Listar las fuentes de programas de Winget
Para ver las fuentes de programas que Winget utiliza, usa el siguiente comando:
```bash
winget source list
```

## Buscar un programa
Para buscar un programa específico en las fuentes de Winget, usa:
```bash
winget search <programa>
```

## Instalar un programa
Para instalar un programa utilizando Winget, ejecuta:
```bash
winget install <programa>
```

## Instalar un programa aceptando acuerdos de licencia y sin intervención del usuario
Si quieres instalar un programa aceptando automáticamente los acuerdos de licencia y sin necesidad de intervención, usa el siguiente comando:
```bash
winget install <programa> --accept-source-agreements --disable-interactivity
```

# [Pandoc](https://pandoc.org/)

## Especificando formatos

El formato de la entrada y salida puede especificarse explícitamente usando las opciones de línea de comandos.

- Convertir `hola.txt` de Markdown a LaTeX:

```bash
pandoc -f markdown -t latex hola.txt
```

- Convertir `hola.html` de HTML a Markdown:

```bash
pandoc -f html -t markdown hola.html
```

Si el formato de entrada o salida no se especifica explícitamente, Pandoc intentará adivinarlo a partir de las extensiones de los nombres de archivo:
```bash
pandoc -o hola.tex hola.txt
```

## Codificación de caracteres

Pandoc utiliza la codificación de caracteres UTF-8 tanto para la entrada como para la salida. Si tu codificación de caracteres local no es UTF-8, debes canalizar la entrada y salida a través de `iconv`:

```bash
iconv -t utf-8 entrada.txt | pandoc | iconv -f utf-8
```

## Creando un PDF a partir de un Markdown

Para producir un PDF, especifica un archivo de salida con una extensión `.pdf`:

```bash
pandoc prueba.md -o prueba.pdf
```

## Creando un Word a partir de un Markdown

Para producir un Word, especifica un archivo de salida con una extensión `.docx`:

```bash
pandoc prueba.md -o prueba.docx
```
