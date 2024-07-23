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

# [ffmpeg](https://www.ffmpeg.org/)

## Redimensionar el video a una resolución de `1920x1080` píxeles

```bash
ffmpeg -i input.mp4 -vf scale=1920:1080 -b:v 11994k -maxrate 11994k -bufsize 24000k -b:a 128k -ac 2 output.mp4
```

- `-vf scale=1920:1080`: Utiliza un filtro de video (`-vf`) para escalar el video a una resolución de 1920x1080 píxeles (Full HD).

- `-b:v 11994k`: Establece la tasa de bits del video a 11994 kbps.

- `-maxrate 11994k`: Establece la tasa máxima de bits del video a 11994 kbps.

- `-bufsize 24000k`: Establece el tamaño del búfer a 24000 kbps.

- `-b:a 128k`: Establece la tasa de bits del audio a 128 kbps.

- `-ac 2`: Establece el número de canales de audio a 2 (estéreo).

## Cortar un video sin perder la calidad

```bash
ffmpeg -i input.mp4 -ss 00:05:30 -to 00:15:45 -c copy output.mp4
```

- `-i input.mp4`: Especifica el archivo de entrada.

- `-ss 00:05:30`: Establece el tiempo de inicio (en este ejemplo, 5 minutos y 30 segundos).

- `-to 00:15:45`: Establece el tiempo de finalización (en este ejemplo, 15 minutos y 45 segundos).

- `-c copy`: Copia los streams de audio y video sin recodificar, manteniendo la calidad original.

- `output.mp4`: Nombre del archivo de salida.

Notas importantes:

- Los tiempos se especifican en formato HH:MM:SS o en segundos (por ejemplo, -ss 330 -to 945).

- También puedes usar `-t` en lugar de `-to` para especificar la duración en lugar del tiempo final. Por ejemplo: `-t 00:10:15` para una duración de 10 minutos y 15 segundos.

- En algunos casos, para obtener un corte más preciso, podrías necesitar usar el comando en dos pasos:

```bash
ffmpeg -ss 00:05:30 -i input.mp4 -to 00:10:15 -c copy output.mp4
```

Esto es más preciso pero puede tardar un poco más en comenzar el proceso.

- Si el corte no es preciso en los keyframes, podrías necesitar recodificar, lo que podría afectar ligeramente la calidad:

```bash
ffmpeg -ss 00:05:30 -i input.mp4 -to 00:15:45 -c:v libx264 -crf 17 -c:a copy output.mp4
```

## Reparar un video

```bash
ffmpeg -i input.mp4 -c:v libx264 -preset slow -crf 18 -c:a aac -b:a 192k -vf "fps=25" -metadata:s:v:0 language=fra -metadata:s:a:0 language=fra output.mp4
```

- `-i input.mp4`: Especifica el archivo de entrada (en este caso, un archivo MP4).

- `-c:v libx264`: Establece el códec de video a H.264. Esto recodificará el video usando el códec x264.

- `-preset slow`: Esto hace que la codificación sea más lenta pero de mayor calidad. Opciones como `slower` o `veryslow` darían aún mejor calidad a costa de más tiempo de procesamiento.

- `-crf 18`: El Factor de Tasa Constante (CRF) va de 0 (sin pérdida) a 51 (peor calidad). Un valor de 18 es considerado visualmente sin pérdidas. Puedes usar valores entre 17 y 20 para una calidad muy alta.

- `-c:a aac`: Establece el códec de audio a AAC. Esto recodificará el audio a AAC.

- `-b:a 192k`: Esto establece la tasa de bits de audio a 192 kbps, que es de buena calidad para la mayoría de los casos. Puedes aumentarla a 256k o 320k para audio de mayor calidad.

- `-vf "fps=25"`: Aplica un filtro de video (vf) para cambiar los fotogramas por segundo (fps) a 25. Esto ajustará la tasa de fotogramas del video a 25 fps, independientemente de la tasa original.

- `-metadata:s:v:0 language=fra`: Establece los metadatos de idioma para la primera pista de video (s:v:0) a francés (fra).

- `-metadata:s:a:0 language=fra`: Establece los metadatos de idioma para la primera pista de audio (s:a:0) a francés (fra).

- `output.mp4`: Especifica el nombre del archivo de salida.

# [kaggle](https://www.kaggle.com/docs/api)

## Crear un token de API

- Una vez que hayas iniciado sesión, ve a tu perfil (haz clic en tu avatar en la esquina superior derecha y selecciona "My Account" o "Mi Cuenta").

- En la sección "API", haz clic en "Create New API Token". Esto descargará un archivo `kaggle.json` que contiene tus credenciales de API.

## Instalar la API de Kaggle

```bash
python -m pip install kaggle
```

## Configurar la API de Kaggle

- Crea una carpeta `.kaggle` en tu directorio de usuario si no la crea la instalación:

```bash
mkdir %HOMEPATH%\.kaggle
```

- Mueve el archivo `kaggle.json` a la carpeta `.kaggle`:

- Mueve el archivo `kaggle.json` manualmente a la carpeta `C:\Users\{tu-usuario}\.kaggle\`

- Verificar la configuración

```bash
kaggle datasets list
```

## Descargar los datos de una competición

```bash
kaggle competitions download -c {name-competition}
```

## Submit Prediction

```bash
kaggle competitions submit -c {name-competition} -f {submission.csv} -m {"Message"}
```
