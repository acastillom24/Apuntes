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
