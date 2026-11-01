# [Kaggle](https://www.kaggle.com/docs/api)

## Crear un token de API

- Una vez que hayas iniciado sesión, ve a tu perfil (haz clic en tu avatar en la esquina superior derecha y selecciona "Settings").

- En la sección "API", haz clic en "Create New Token". Esto descargará un archivo `kaggle.json` que contiene tus credenciales de API.

## Instalar la API de Kaggle

```bash
python -m pip install kaggle
```

## Configurar la API de Kaggle

- Crea una carpeta `.kaggle` en tu directorio de usuario si no la crea la instalación:

=== "PowerShell"

    ```powershell
    mkdir $HOME\.kaggle
    ```

=== "cmd"

    ```bat
    mkdir %USERPROFILE%\.kaggle
    ```

- Mueve el archivo `kaggle.json` a la carpeta `C:\Users\{tu-usuario}\.kaggle\` (en PowerShell, por ejemplo):

```powershell
Move-Item $HOME\Downloads\kaggle.json $HOME\.kaggle\
```

- Verificar la configuración:

```bash
kaggle datasets list
```

## Descargar los datos de una competición

```bash
kaggle competitions download -c <nombre-competicion>
```

## Enviar una predicción (submit)

```bash
kaggle competitions submit -c <nombre-competicion> -f submission.csv -m "mensaje"
```
