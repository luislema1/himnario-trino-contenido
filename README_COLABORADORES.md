# Himnario Trino de Dios - Colaboraciones

Gracias por apoyar el crecimiento del himnario.

## Cómo Proponer una Alabanza

Puede colaborar de una de estas formas:

- Enviar una propuesta al administrador del proyecto.
- Crear un Pull Request en GitHub modificando `hymns.json`.
- Compartir letra, idioma, categoría y autorización de uso.

## Reglas de Aprobación

Antes de publicar una alabanza, el administrador debe revisar:

- Que la letra sea propia, autorizada o de dominio público.
- Que el número del himno no esté duplicado.
- Que el idioma sea `Español`, `Kichwa 1` o `Kichwa 2`.
- Que la categoría esté escrita de forma consistente.
- Que no existan errores evidentes de ortografía o contenido.

## Formato de Cada Himno

```json
{
  "number": 101,
  "title": "Título de la alabanza",
  "lyrics": "Primera línea\nSegunda línea\n\nCoro:\nTexto del coro",
  "language": "Español",
  "category": "Adoración",
  "author": "Nombre del autor o fuente autorizada",
  "key": "G",
  "is_active": true
}
```

## Publicación

Después de aprobar cambios:

1. Actualice `hymns.json`.
2. Genere un nuevo `manifest.json` con:

```powershell
python tools\build_github_hymn_package.py --version 2
```

3. Suba `manifest.json` y `hymns.json` a GitHub Pages.
4. La app descargará los cambios desde la pantalla **Nuevos Himnos**.

## Importante

No publique canciones protegidas por derechos de autor sin permiso escrito o autorización válida.
