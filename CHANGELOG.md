# Gildem Craft Pro v7.4.0 · 8 de noviembre de 2026

- Añadidas comidas con subramas, iconos originales y destino Royal.
- Recetas procedentes de `ao-data/ao-bin-dumps/master/items.json`, con lotes y encantamientos extraídos del archivo, sin fórmulas inventadas.
- Ciudad de especialidad de cocina Caerleon; comparación opcional con Bridgewatch.
- Corregido el transporte por unidad producida para recetas con salida múltiple.
- Revisión de commits de `items.json` (GitHub) y actualización diaria del catálogo de recetas de Netlify, más sincronización manual tras parches.
- Añadidos platos y algunos ingredientes al pequeño monitor horario de AODP.
- Conservado el motor Royal/BM, Focus, diarios de equipo, libros de órdenes, seguimiento de ventas e imágenes con respaldo.
- Último parche verificado en fuentes oficiales: Dragonfire Patch 4, publicado 2026-11-02.

---

# Gildem Craft Pro v7.3.0 · Reparación de imágenes

Esta actualización NO cambia los cálculos de crafting ni el mercado, y mantiene la v7.2 como base.

## Cambios

- El selector y las tablas cargan iconos de Albion desde más de una fuente: Albion Free Market CDN, un proxy propio en Netlify y el servicio oficial Albion Render.
- Manejo de errores de imagen en un solo lugar: si falla la fuente actual, prueba la siguiente sin entrar en bucles. Icono SVG incluido si todas fallan.
- La compilación de Netlify intenta descargar los iconos representativos de las ramas al sitio publicado (`dist/item-icons/`). El resultado es una caché ESTÁTICA de las imágenes conseguidas. Si no hay acceso a los servidores durante el build, la compilación sigue y se usan los proveedores de respaldo en ejecución.
- Nueva función Netlify `item-image` con validación de identificadores, tiempo máximo de descarga, tamaño máximo y caché CDN. No es un proxy abierto.
- En Ajustes > Diagnóstico de imágenes se pueden probar por separado las fuentes desde el navegador.
- Tarjetas del selector con carga prioritaria de imágenes, respetando IDs y nombres españoles.
- Service worker actualizado para evitar utilizar el código de imágenes de v7.2.
- Nuevas pruebas unitarias para rutas, identificadores, fallbacks, proxy y el procedimiento de caché.

## Límites conocidos

- En Netlify Drop NO se ejecutan las funciones de servidor ni el proceso de descarga al compilar. Esa versión depende de que el navegador tenga acceso a algún servidor de imágenes. El SVG de reserva siempre se incluye.
- En GitHub + Netlify la compilación intentará empaquetar iconos originales para el selector, pero el número descargado depende de la disponibilidad de las fuentes durante el build.
- No todos los IDs de juego cuentan con imagen disponible. No se muestran imágenes inventadas para esos casos.
- Una prueba automatizada de rutas no prueba que las imágenes se carguen desde la red del usuario.
