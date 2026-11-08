# Filosofía PAU Madrid — versión PWA (instalable)

Creación de Víctor Ramírez Vélez, profesor de Filosofía del IES Ágora. Licencia CC BY-NC-ND 4.0 (ver LICENCIA.txt).

## Contenido
- `index.html`: la app completa (tipografías incluidas, sin dependencias externas).
- `manifest.webmanifest` e `icons/`: datos e iconos para instalarla.
- `sw.js`: service worker que permite usarla sin conexión.
- `screenshots/`: capturas declaradas en el manifiesto (las lee PWABuilder y el cuadro de instalación de Chrome).
- `privacidad.html`: política de privacidad (la URL que pide Google Play: `https://tu-direccion/privacidad.html`). Antes de publicar, sustituye `[TU CORREO DE CONTACTO]` por tu correo.

## Publicarla gratis (hace falta HTTPS; estos servicios lo dan)
**Netlify (lo más rápido):** entra en app.netlify.com/drop y arrastra esta carpeta entera. Te da una dirección https://….netlify.app.
**GitHub Pages:** crea un repositorio público, sube el contenido de esta carpeta a la raíz, y en Settings → Pages elige la rama `main` y la carpeta `/ (root)`.

## Instalarla en el móvil
Abre la dirección en Chrome (Android) → menú ⋮ → «Instalar aplicación» (o «Añadir a pantalla de inicio»). Tras la primera carga funciona sin conexión.
En iPhone: Safari → Compartir → «Añadir a pantalla de inicio».

## Importante
- Abrir `index.html` con doble clic (file://) funciona como página normal, pero no se instala ni cachea: para eso necesita HTTPS.
- El progreso se guarda en el navegador de cada dispositivo. Para pasarlo a otro: Ajustes → Copia de seguridad → «Generar y copiar», y en el otro dispositivo «Restaurar desde el texto».
- Si cambias de dirección web, el progreso no se traslada solo: usa la copia de seguridad.
- Al publicar una versión nueva, el service worker se actualiza solo (la versión se recalcula al compilar); los usuarios la ven tras cerrar y reabrir la app.
