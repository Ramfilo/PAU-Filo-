# Activar la sincronización con Google Drive (una sola vez, ~10 minutos)

La app ya lleva todo el código. Solo hace falta un «ID de cliente» gratuito de Google, pegado en `config.js`.
No cuesta nada y, con el único permiso que usa (`drive.appdata`), no necesita verificación de Google.

## 1. Publica la app en una dirección https
GitHub Pages o Netlify (ver LEEME.md). Anota la dirección exacta, p. ej. `https://ramfilo.github.io`
(el origen es solo `https://usuario.github.io`, sin la ruta del repositorio).
La sincronización NO funciona abriendo el archivo con doble clic.

## 2. Crea el proyecto en Google Cloud
1. https://console.cloud.google.com → selector de proyectos → «Proyecto nuevo» → «Filosofia PAU» → Crear.
2. Menú ☰ → «APIs y servicios» → «Biblioteca» → **Google Drive API** → Habilitar.

## 3. Pantalla de consentimiento (Google Auth Platform)
1. **Información de la app / Branding**: nombre «Filosofía PAU Madrid», correo de asistencia y correo de contacto del desarrollador.
   **Deja VACÍOS** la página principal, el enlace a la política de privacidad, las condiciones del servicio y el logotipo.
   (Si los rellenas, Google exige verificar dominios y la propiedad del sitio; sin ellos no hace falta.)
2. **Público**: tipo de usuario **Externo**.
3. **Acceso a los datos**: añade solo el permiso `.../auth/drive.appdata`
   («Ver y gestionar sus propios datos de configuración en Google Drive»).
4. **Público → «Publicar app»** (pasar a «En producción»). Importante: en modo «Pruebas» solo entran usuarios que añadas a mano y la sesión caduca a los 7 días.

## 4. Crea el ID de cliente
1. «Clientes» / «Credenciales» → «Crear cliente» / «ID de cliente de OAuth».
2. Tipo: **Aplicación web**.
3. «Orígenes autorizados de JavaScript»: `https://ramfilo.github.io` (sin barra final ni ruta). Para probar en tu ordenador, añade también `http://localhost:8000`.
4. No hace falta «URI de redirección».
5. Crear → copia el ID (termina en `.apps.googleusercontent.com`).

## 5. Pégalo en la app
En `config.js`:

    window.FILOSOFIA_CONFIG = {"googleClientId":"TU-ID.apps.googleusercontent.com"};

Sube la carpeta a tu hosting y abre la app (cierra y reabre una vez para que se actualice).
En Ajustes aparece la tarjeta «Sincronizar entre dispositivos».

## 6. Pruébalo
1. En el móvil: Ajustes → «Sincronizar con Google» → elige cuenta → acepta el permiso.
2. En el ordenador, misma dirección y misma cuenta: verás tu progreso.
3. Si generas la APK con PWABuilder, repite la prueba dentro de la APK. Si el inicio de sesión no abriera allí, queda la copia manual.

## Notas
- El ID de cliente no es secreto; puede estar en el repositorio público.
- Cada alumno usa su propio Drive: tú no ves sus datos.
- Si cambias de dirección web, añade la nueva en «Orígenes autorizados».
- Política de privacidad (para Google Play): `https://ramfilo.github.io/PAU-Filo-/privacidad.html` (el archivo está en la raíz de la carpeta). No uses raw.githubusercontent.com.
- Google Play, «Seguridad de los datos»: el autor no recibe datos; la copia va al Drive del propio usuario. Lo habitual es «no recopila datos»; si prefieres prudencia, declara el inicio de sesión con Google.
