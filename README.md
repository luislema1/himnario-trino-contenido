# Contenido Online - Himnario Trino de Dios

Esta carpeta es el contenido que puede publicarse en GitHub Pages para que la app descargue nuevos himnos cuando exista internet.

## Archivos Publicados

- `manifest.json`: indica versión, fecha y SHA-256 del catálogo aprobado.
- `hymns.json`: contiene los himnos aprobados.
- `README_COLABORADORES.md`: guía para personas que desean proponer nuevas alabanzas.

## URL Esperada en la App

Configure en `local.properties`:

```properties
HTD_HYMN_UPDATE_MANIFEST_URL=https://luislema1.github.io/himnario-trino-contenido/manifest.json
```

La app descargará `manifest.json` y luego `hymns.json`.

## Generar Paquete

Desde la raíz del proyecto Android:

```powershell
python tools\build_github_hymn_package.py --version 1
```

Si desea indicar la URL absoluta de `hymns.json`:

```powershell
python tools\build_github_hymn_package.py --version 1 --hymns-url https://luislema1.github.io/himnario-trino-contenido/hymns.json
```

## Seguridad

El campo `hymns_sha256` permite que la app rechace descargas dañadas o alteradas accidentalmente. Para una versión premium posterior, el campo `signature` puede usarse con firma digital asimétrica.
