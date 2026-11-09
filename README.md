# Gildem Craft Pro v7.4.0

Web app de crafting en español para Albion Online, Royal + Black Market, servidor América (West) por defecto.

## Novedad principal: iconos de objetos con recuperación automática

La v7.2 cargaba los iconos solo desde `render.albiononline.com`, de modo que algunas conexiones mostraban únicamente imágenes de respaldo.

La v7.3 utiliza:

1. Iconos del selector empaquetados localmente en el build de Netlify, si el servidor pudo descargarlos.
2. `https://cdn.albionfreemarket.com/item/` como primera fuente online de iconos.
3. Función de Netlify `/.netlify/functions/item-image`, cuyo backend consulta dos fuentes permitidas, con caché y validación.
4. `https://render.albiononline.com/v1/item/` como fuente oficial de respaldo.
5. `./icons/item-fallback.svg` cuando ninguna fuente entrega imagen válida.

Una fuente online inaccesible no afecta el cálculo de profit, mercado ni inventario.

En **Ajustes y datos** encontrarás **Comprobar servidores de imágenes**, que prueba cada servicio desde tu navegador.

## Instalar

Lee `INSTALAR_EN_NETLIFY.md` para la versión completa GitHub + Netlify o para Netlify Drop.

## Desarrollo

- `npm test`: pruebas del motor.
- `npm run build`: comprobación, tests y dist/ (sin descarga online de iconos en local).
- `GILDEM_PREFETCH_ICONS=1 npm run build`: intenta guardar iconos representativos con conexión a Internet.
- En Netlify el cacheo de iconos durante el build se activa automáticamente; define `GILDEM_PREFETCH_ICONS=0` para desactivarlo si el proveedor está caído.

## Fuentes

- Precios: https://www.albion-online-data.com/api/
- Render oficial: https://render.albiononline.com/
- CDN alternativo: https://cdn.albionfreemarket.com/item/
- Recetas: https://github.com/ao-data/ao-bin-dumps

Los precios de AODP son datos aportados por jugadores, no precios garantizados. Los iconos no proceden de la API de precios.


## Novedades v7.4: Comidas y control de revisiones del juego

- Selector visual con **Comidas** y las familias: sopas, ensaladas, pasteles, tortillas, guisos, bocadillos, asados, pescado y recetas avalonianas.
- Solo se recomiendan las recetas que aparecen con `craftingrequirements` en el `items.json` público de ao-data. No se inventan ingredientes.
- La familia `T1_MEAL_` hasta `T8_MEAL_` se calcula con el valor real de `@amountcrafted` (generalmente lotes de 10, platos de pescado a menudo 1).
- Las comidas se venden únicamente en los mercados Royal. Bonificación local de cocina: **Caerleon**. La opción de comparación usa **Bridgewatch** como ciudad sin bono.
- Para comidas y pociones, el transporte se cobra por **unidad de producto**. El costo de estación es por **fabricación o lote**.
- Se agregó botón **Actualizar recetas tras parche**. Netlify comprueba la revisión de `items.json` en GitHub y refresca el catálogo compacto al cambiar, con caché de 24 horas.
- Último parche oficialmente comprobado al preparar esta entrega: **Dragonfire Patch 4 (2 de noviembre de 2026)**. Para cambios nuevos, consultar https://albiononline.com/update. La publicación de un parche no garantiza que las fuentes de terceros o AODP lo reflejen instantáneamente.
- Los precios de AODP son observaciones con su propia fecha: no garantizan inventario, demanda, ejecución ni actualización instantánea.

**Aviso:** la primera descarga del archivo completo puede ser grande cuando se usa Netlify Drop; para mejores resultados, publicar el proyecto completo mediante GitHub + Netlify.

**Importante:** el catálogo principal de armas/armaduras y las traducciones procede de `vkorne-web/albion-market`, con refresco cada 24 horas cuando la aplicación se usa. Su actualización puede retrasarse respecto a la publicación de un parche. Para crafting especial, la versión y las recetas se contrastan con `ao-data/ao-bin-dumps`.
