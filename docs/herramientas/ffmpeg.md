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

- Los tiempos se especifican en formato HH:MM:SS o en segundos (por ejemplo, `-ss 330 -to 945`).

- También puedes usar `-t` en lugar de `-to` para especificar la duración en lugar del tiempo final. Por ejemplo: `-t 00:10:15` para una duración de 10 minutos y 15 segundos.

- Si pones `-ss` **antes** de `-i`, la búsqueda es más rápida. En ese caso `-to` se cuenta desde el nuevo inicio (actúa como duración): este ejemplo corta 10 minutos y 15 segundos a partir del minuto 5:30.

```bash
ffmpeg -ss 00:05:30 -i input.mp4 -to 00:10:15 -c copy output.mp4
```

- Con `-c copy` el corte solo puede empezar en un keyframe, así que puede no ser exacto. Si necesitas precisión, recodifica el video (puede afectar ligeramente la calidad):

```bash
ffmpeg -ss 00:05:30 -i input.mp4 -to 00:10:15 -c:v libx264 -crf 17 -c:a copy output.mp4
```

## Reparar un video

Recodificar el video suele arreglar archivos con timestamps rotos, fps variables o problemas de compatibilidad:

```bash
ffmpeg -i input.mp4 -c:v libx264 -preset slow -crf 18 -c:a aac -b:a 192k -vf "fps=25" output.mp4
```

- `-i input.mp4`: Especifica el archivo de entrada (en este caso, un archivo MP4).

- `-c:v libx264`: Establece el códec de video a H.264. Esto recodificará el video usando el códec x264.

- `-preset slow`: Esto hace que la codificación sea más lenta pero de mayor calidad. Opciones como `slower` o `veryslow` darían aún mejor calidad a costa de más tiempo de procesamiento.

- `-crf 18`: El Factor de Tasa Constante (CRF) va de 0 (sin pérdida) a 51 (peor calidad). Un valor de 18 es considerado visualmente sin pérdidas. Puedes usar valores entre 17 y 20 para una calidad muy alta.

- `-c:a aac`: Establece el códec de audio a AAC. Esto recodificará el audio a AAC.

- `-b:a 192k`: Esto establece la tasa de bits de audio a 192 kbps, que es de buena calidad para la mayoría de los casos. Puedes aumentarla a 256k o 320k para audio de mayor calidad.

- `-vf "fps=25"`: Aplica un filtro de video (vf) para cambiar los fotogramas por segundo (fps) a 25. Esto ajustará la tasa de fotogramas del video a 25 fps, independientemente de la tasa original.

- `output.mp4`: Especifica el nombre del archivo de salida.

!!! tip "Opcional: etiquetar el idioma de las pistas"
    No es parte de la reparación, pero puedes añadir metadatos de idioma (aquí francés, `fra`; para español usa `spa`):

    ```bash
    -metadata:s:v:0 language=fra -metadata:s:a:0 language=fra
    ```

    - `-metadata:s:v:0`: primera pista de video.
    - `-metadata:s:a:0`: primera pista de audio.
