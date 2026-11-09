# Gildem Craft Pro v7.4 · Instalación en Netlify

## Versión completa (recomendada)

1. Extrae el ZIP **COMPLETA**.
2. Sube todos los archivos a tu repositorio conectado con Netlify (no subas solamente `dist`).
3. En Netlify usa `npm run build`, directorio de publicación `dist`, y deja que detecte `netlify/functions` desde `netlify.toml`.
4. Publica. Abre Plan de crafting > **Comidas** > elige una familia > Generar plan.
5. En el nuevo aviso bajo el formulario, pulsa **Actualizar recetas tras parche** si hubo una actualización del juego.

## Versión Netlify Drop

1. Extrae el ZIP **DROP** y arrastra la carpeta con `index.html` a Netlify Drop.
2. Carga el selector, pero no hay funciones de Netlify para recetas/precios: depende del acceso del navegador a los servidores externos.
3. Si aparecen errores de CORS o timeouts en las recetas, usa la **COMPLETA**.

## Después de actualizar

- Fuerza la recarga: Windows `Ctrl+F5`, Mac `Cmd+Shift+R`.
- La web usa service worker, con número de versión nuevo para limpiar sus archivos antiguos.
- Comprueba la fecha de los precios AODP antes de comprar ingredientes.
- El catálogo de recetas se revisa cuando se vuelve a utilizar tras 24 h, contra la versión de `items.json` publicada en GitHub. No garantiza sincronización instantánea con cada actualización oficial del juego.
- Los iconos se cargan desde servidores externos con respaldo; en la versión completa se intentan guardar iconos de las ramas durante el build.

Fuente de parches: https://albiononline.com/update
Fuente de recetas: https://github.com/ao-data/ao-bin-dumps
Fuente de precios: https://www.albion-online-data.com/api/
