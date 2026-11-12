# Filosofía PAU Madrid — versión PWA (instalable)

Creación de Víctor Ramírez Vélez, profesor de Filosofía del IES Ágora. Licencia CC BY-NC-ND 4.0 (ver LICENCIA.txt).

## Contenido
- `index.html`: la app completa (tipografías incluidas, sin dependencias externas).
- `manifest.webmanifest` e `icons/`: datos e iconos para instalarla.
- `sw.js`: service worker que permite usarla sin conexión.
- `screenshots/`: capturas declaradas en el manifiesto (las lee PWABuilder y el cuadro de instalación de Chrome).
- `config.js`: aquí se pega el ID de cliente de Google para activar la sincronización opcional con Drive (guía paso a paso en `GUIA-SINCRONIZACION.md`). Vacío = sin sincronización.
- `privacidad.html`: política de privacidad (la URL que pide Google Play: `https://tu-direccion/privacidad.html`). El correo de contacto ya está incluido.

## Publicarla gratis (hace falta HTTPS; estos servicios lo dan)
**Netlify (lo más rápido):** entra en app.netlify.com/drop y arrastra esta carpeta entera. Te da una dirección https://….netlify.app.
**GitHub Pages:** crea un repositorio público, sube el contenido de esta carpeta a la raíz, y en Settings → Pages elige la rama `main` y la carpeta `/ (root)`.

## Instalarla en el móvil
Abre la dirección en Chrome (Android) → menú ⋮ → «Instalar aplicación» (o «Añadir a pantalla de inicio»). Tras la primera carga funciona sin conexión.
En iPhone: Safari → Compartir → «Añadir a pantalla de inicio».

## Importante
- Abrir `index.html` con doble clic (file://) funciona como página normal, pero no se instala ni cachea: para eso necesita HTTPS.
- El progreso se guarda en el navegador de cada dispositivo. Con la sincronización de Google activada (opcional) se comparte solo entre los dispositivos de la misma cuenta. Para pasarlo sin cuenta a otro: Ajustes → Copia de seguridad → «Generar y copiar», y en el otro dispositivo «Restaurar desde el texto».
- Si cambias de dirección web, el progreso no se traslada solo: usa la copia de seguridad.
- Al publicar una versión nueva: la app abre siempre al instante con la copia guardada. En segundo plano comprueba si hay novedades (al abrirla, al volver a primer plano y cada 30 minutos) y, si las hay, muestra el aviso «Hay una versión nueva de la app» con el botón «Actualizar». Si no pulsas el botón, la versión nueva ya queda descargada y se carga sola la próxima vez que cierres y abras la app. GitHub Pages tarda entre 1 y 10 minutos en servir los archivos nuevos tras subirlos.
- Si un dispositivo se queda con una versión antigua (sobre todo en iPhone, donde la app puede quedar suspendida en segundo plano): ciérrala desde el selector de apps (deslizar hacia arriba) y vuelve a abrirla. Quitar el icono y volver a añadirlo borra los datos guardados en ese dispositivo, así que solo como último recurso y con copia de seguridad.
