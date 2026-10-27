# Prompt maestro — Publicar formulario en Firebase Hosting + Firestore

Actuá como un asistente técnico que me va a ayudar a publicar una web app estática en Firebase Hosting y dejar conectada su base de datos en Firestore. Te doy todo el contexto necesario, andá haciendo los pasos en orden y contame en cada uno qué encontraste antes de seguir con el siguiente (no asumas que algo funcionó si no viste la confirmación en la terminal).

## Contexto del proyecto

- Ya tengo una cuenta de Google con un proyecto de Firebase creado, Project ID: `cuba-eventos`
- Ya tengo Node.js instalado (versión 24.20.0 LTS)
- Tengo un archivo `formulario-sorteo.html` que es un formulario de sorteo/promoción para un boliche, con el `firebaseConfig` ya completado dentro del archivo, apuntando al proyecto `cuba-eventos`
- El formulario guarda cada registro en la colección de Firestore `participantes_sorteo`

## Tareas a realizar, en orden

1. **Verificar entorno**: correr `node -v` y `npm -v`, confirmarme las versiones antes de seguir.

2. **Instalar Firebase CLI** de forma global: `npm install -g firebase-tools`. Si ya está instalado, correr `firebase --version` para confirmarlo en vez de reinstalar.

3. **Loguearme en Firebase**: correr `firebase login` y esperar a que yo confirme en el navegador que quedé autenticado con la cuenta correcta.

4. **Crear carpeta de proyecto** (si no existe) llamada `sorteo-cuba-eventos`. Dentro, copiar o mover el archivo `formulario-sorteo.html` y renombrarlo a `index.html`.

5. Dentro de esa carpeta, correr `firebase init hosting`:
   - Elegir "Use an existing project" y seleccionar `cuba-eventos`
   - Cuando pregunte por el "public directory", usar la carpeta actual (donde está `index.html`)
   - Configurar como single-page app: **NO** (es un solo archivo estático, no una SPA con rutas)
   - **NO** sobrescribir `index.html` si pregunta

6. Antes de hacer deploy, mostrame el contenido del archivo `firestore.rules` (si `init` lo generó) o creá uno con este contenido exacto, y **pedime confirmación antes de aplicarlo**:

   ```
   rules_version = '2';
   service cloud.firestore {
     match /databases/{database}/documents {
       match /participantes_sorteo/{docId} {
         allow create: if request.resource.data.keys().hasAll(['nombre', 'fecha_nacimiento', 'celular', 'consentimiento_datos'])
                       && request.resource.data.consentimiento_datos == true;
         allow read, update, delete: if false;
       }
     }
   }
   ```

7. Si el proyecto no tiene `firestore.rules` vinculado al hosting init, decime cómo aplicar esas reglas manualmente (por CLI con `firebase deploy --only firestore:rules`, para lo cual antes hay que correr `firebase init firestore` y apuntar al archivo de reglas de arriba).

8. Correr `firebase deploy`. Al terminar, mostrame la URL pública final (algo como `https://cuba-eventos.web.app`).

9. Como verificación final, abrí esa URL (o decime que la abra yo) y confirmame que el formulario carga bien, sin errores de consola relacionados a Firebase.

## Reglas generales

No inventes valores de configuración, no modifiques el `firebaseConfig` del archivo, y si algo falla mostrame el error completo de la terminal antes de intentar una solución.
