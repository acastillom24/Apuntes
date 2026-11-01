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
