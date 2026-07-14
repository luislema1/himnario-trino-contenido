# Contenido Online - Himnario Trino de Dios

Esta carpeta es el contenido que puede publicarse en GitHub Pages para que la app descargue nuevos himnos cuando exista internet.

## Archivos Publicados

- `manifest.json`: indica versión, fecha y SHA-256 del catálogo aprobado.
- `hymns.json`: contiene los himnos aprobados.
- `app-update.json`: indica la versión del APK disponible.
- `HimnarioTD.apk`: APK firmado para descarga.
- `README_COLABORADORES.md`: guía para personas que desean proponer nuevas alabanzas.

## URL Esperada en la App

Configure en `local.properties`:

```properties
HTD_HYMN_UPDATE_MANIFEST_URL=https://luislema1.github.io/himnario-trino-contenido/manifest.json
HTD_APP_UPDATE_MANIFEST_URL=https://luislema1.github.io/himnario-trino-contenido/app-update.json
```

La app descargará `manifest.json` para himnos y `app-update.json` para revisar si existe un APK más reciente.

## Generar Paquete

Desde la raíz del proyecto Android:

```powershell
python tools\import_hymns_from_word.py --include-all --write-app-assets
python tools\build_github_hymn_package.py --version 3 --hymns-url https://luislema1.github.io/himnario-trino-contenido/hymns.json
```

El primer comando importa los Word oficiales. El segundo genera `github-content/hymns.json`, actualiza la versión del catálogo y recalcula el SHA-256 del `manifest.json`.

Si solo desea empaquetar el JSON ya incluido en la app:

```powershell
python tools\build_github_hymn_package.py --version 1 --hymns-url https://luislema1.github.io/himnario-trino-contenido/hymns.json
```

## Seguridad

El campo `hymns_sha256` permite que la app rechace descargas dañadas o alteradas accidentalmente. Para una versión premium posterior, el campo `signature` puede usarse con firma digital asimétrica.

## Publicar APK

Después de generar un APK release firmado:

```powershell
python tools\build_app_update_package.py --version-code 5 --version-name 1.1.0
```

Suba a GitHub:

```text
github-content/HimnarioTD.apk
github-content/app-update.json
```

Enlace recomendado para usuarios:

```text
https://luislema1.github.io/himnario-trino-contenido/HimnarioTD.apk
```

No use el enlace `blob` para compartir:

```text
https://github.com/luislema1/himnario-trino-contenido/blob/main/HimnarioTD.apk
```

Si necesita enlace directo desde GitHub, use `raw`:

```text
https://github.com/luislema1/himnario-trino-contenido/raw/main/HimnarioTD.apk
```
