# Apuntes

Notas personales de comandos y herramientas (Git, Winget, Pandoc, ffmpeg, Kaggle...).

📖 **Léelas aquí:** https://acastillom24.github.io/apuntes/

## Cómo añadir una nota

1. Crea o edita un archivo `.md` dentro de `docs/` (un archivo por herramienta/tema).
2. Si es un archivo nuevo, agrégalo a la sección `nav` de `mkdocs.yml`.
3. Haz commit y push a `main`: el sitio se publica solo con GitHub Actions.

## Ver el sitio en local

```bash
python -m venv .venv
.venv\Scripts\activate        # Windows (en Linux/macOS: source .venv/bin/activate)
pip install -r requirements.txt
mkdocs serve                  # abre http://127.0.0.1:8000
```
