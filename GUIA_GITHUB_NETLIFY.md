# Gildem Craft Pro v7.4.1 | GitHub + Netlify

Este paquete es el **código fuente completo** de la herramienta, preparado para GitHub.
No publiques el ZIP como un único archivo dentro del repositorio y no utilices Netlify Drop.

## 1. Crear un repositorio en GitHub

1. En https://github.com/new escribe **gildem-craft-pro** como nombre.
2. Selecciona **Private** (puedes hacer el repositorio público si lo prefieres).
3. En la creación inicial, deja **sin marcar** README, .gitignore y License, pues ya tenemos README y .gitignore.
4. Pulsa **Create repository**.
5. En el repositorio, elige **uploading an existing file** o **Add file > Upload files**.
6. Descomprime este ZIP en tu computadora, abre la carpeta resultante y arrastra **el contenido interior**, conservando las carpetas `core`, `icons`, `scripts`, `netlify` y `tests`.
7. Pulsa **Commit changes** y comprueba que `netlify.toml` esté en la raíz, junto a `package.json` y `index.html`.

## 2. Conectar el mismo sitio de Netlify

1. Abre https://app.netlify.com y selecciona el proyecto que usa `marvelous-sopapillas-56ddac.netlify.app`.
2. Abre **Project configuration > Developer settings > Continuous deployment > Repository**.
3. Selecciona **Link repository**, autoriza GitHub y elige `gildem-craft-pro`.
4. Revisa la configuración y usa: **Base directory** (vacío), **Build command** `npm run build`, **Publish directory** `dist`, **Functions directory** `netlify/functions`, **Production branch** `main`.
5. Guarda los cambios y desde **Deploys** inicia la compilación si no empieza automáticamente.
6. Abre **Deploy log**. Busca `npm test`, `Gildem Craft Pro: dist/ preparado` y el mensaje final de deploy publicado.

## 3. Verificar funciones

- https://marvelous-sopapillas-56ddac.netlify.app/.netlify/functions/health
  Debe responder JSON con `status: "ok"`, `functions: true`, `version: "7.4.1"`.
- https://marvelous-sopapillas-56ddac.netlify.app/.netlify/functions/recipes
  Es una función más pesada: la primera consulta puede tardar. Si devuelve error, consulta los logs de funciones en Netlify.
- Las funciones `market`, `item-image`, `snapshot` y `hourly-prices` deben aparecer en el panel de funciones si se desplegaron. `hourly-prices` está programada cada hora y **no** se invoca por URL en producción.

## 4. Actualizar el proyecto en el futuro

Sube los archivos cambiados a GitHub y haz un commit. Netlify reconstruirá el sitio automáticamente. Es recomendable conservar el repositorio privado y no guardar credenciales dentro del código.

## Problemas comunes

- **404 en health:** no se han desplegado las funciones, sitio incorrecto, o el deploy todavía no está publicado.
- **404 en la web:** revisa que el directorio de publicación sea `dist` y el archivo `index.html` se construya ahí.
- **Falló la compilación:** en Netlify abre **Deploys > [deploy] > Deploy log**; copia las últimas líneas de error.
- **Datos antiguos:** fuerza la recarga, borra caché del sitio y comprueba las fechas individuales de precios en AODP.
- **La web funciona pero no hay recetas:** consulta logs de `recipes`, que necesita descargar el dump público del juego.

**Importante:** la compilación no garantiza que la API comunitaria tenga datos recientes o que cada consulta externa funcione en producción. Verifica fechas y cotizaciones antes de invertir silver.
