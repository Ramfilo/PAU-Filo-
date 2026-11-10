# Cómo activar la sincronización con Google Drive (una sola vez, ~10 minutos)

La app ya lleva todo el código. Solo falta crear un «ID de cliente» gratuito en Google y pegarlo en `config.js`.
No cuesta nada y no necesita verificación de Google (el permiso `drive.appdata` no es sensible).

## 1. Publica la app en una dirección HTTPS
Netlify, GitHub Pages… (ver LEEME.md). Anota la dirección exacta, p. ej. `https://filosofia-pau.netlify.app`.
La sincronización NO funciona abriendo el archivo con doble clic.

## 2. Crea el proyecto en Google Cloud
1. Entra en https://console.cloud.google.com con tu cuenta de Google.
2. Arriba, selector de proyectos → «Proyecto nuevo» → nombre «Filosofia PAU» → Crear.
3. Menú ☰ → «APIs y servicios» → «Biblioteca» → busca **Google Drive API** → Habilitar.

## 3. Pantalla de consentimiento
1. «APIs y servicios» → «Pantalla de consentimiento de OAuth» (o «Google Auth Platform»).
2. Tipo de usuario: **Externo**. Nombre de la app: «Filosofía PAU Madrid». Correo de asistencia y de contacto: el tuyo.
3. Dominio autorizado: el de tu hosting (p. ej. `netlify.app`). Enlace a política de privacidad: `https://tu-direccion/privacidad.html`.
4. Permisos (Scopes) → «Añadir o quitar permisos» → marca `.../auth/drive.appdata` («Ver y gestionar sus propios datos de configuración en Google Drive») → Guardar.
5. **Publicar la aplicación** («Publicar app» / «En producción»). Muy importante: en modo «Pruebas» solo pueden entrar usuarios que añadas a mano y la sesión caduca a los 7 días. Con solo ese permiso no hay verificación ni revisión.

## 4. Crea el ID de cliente
1. «Credenciales» → «Crear credenciales» → «ID de cliente de OAuth».
2. Tipo: **Aplicación web**. Nombre libre.
3. «Orígenes autorizados de JavaScript»: añade tu dirección exacta, sin barra final (`https://filosofia-pau.netlify.app`). Si quieres probar en tu ordenador, añade también `http://localhost:8000`.
4. No hace falta «URI de redirección».
5. Crear → copia el ID (termina en `.apps.googleusercontent.com`).

## 5. Pégalo en la app
Abre `config.js` (en la carpeta de la PWA) con el Bloc de notas y pon:

    window.FILOSOFIA_CONFIG = {"googleClientId":"1234567890-abc.apps.googleusercontent.com"};

Vuelve a subir la carpeta a tu hosting. Cierra y reabre la app una vez (el service worker se actualiza solo).
En Ajustes aparecerá la tarjeta «Sincronizar entre dispositivos».

## 6. Pruébalo
1. En el móvil, Ajustes → «Sincronizar con Google» → elige tu cuenta → acepta el permiso.
2. Haz unas preguntas. En el ordenador abre la misma dirección, activa la sincronización con la misma cuenta: verás tu progreso.
3. Si se instala como APK (PWABuilder), repite la prueba dentro de la app instalada. Si el inicio de sesión no abriera allí, el alumnado puede usar la copia manual (sigue disponible).

## Notas
- El ID de cliente NO es secreto; puede ir en el código público.
- Cada alumno usa su propia cuenta y su propio Drive: tú no ves nada de sus datos.
- Si cambias de dirección web, hay que añadir la nueva en «Orígenes autorizados».
- Google Play, «Seguridad de los datos»: el autor no recibe ningún dato; la copia va al Drive del propio usuario mediante el inicio de sesión de Google. Es la lectura habitual para marcar «no recopila datos», pero si quieres máxima prudencia puedes declarar que la app permite iniciar sesión con Google y guarda datos de la app en la cuenta del usuario. Revísalo en la consola al rellenar el formulario.
