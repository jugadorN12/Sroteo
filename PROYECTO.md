# Cuba Eventos — Sistema de Sorteo

## 1. Objetivo
Brindar a Cuba Eventos una plataforma web ágil, segura y moderna para que los asistentes al boliche/evento participen en sorteos desde su celular mediante un código QR, y la organización pueda controlar el sorteo en tiempo real con una pantalla gigante animada y un control remoto móvil.

## 2. Usuarios y Roles
- **Público / Asistentes**: Escanean el QR, completan el formulario con sus datos básicos (nombre, cumpleaños, celular, consentimiento legal) y reciben su número de participación.
- **Administrador / Staff**: Inician sesión con cuenta autorizada de Google para:
  - Personalizar textos, colores y premios del sorteo.
  - Ver el listado y métricas de participantes.
  - Iniciar cuenta regresiva y girar la ruleta del sorteo.
  - Llamar o enviar mensaje de WhatsApp directamente al ganador desde el celular.
  - Reincluir participantes si hace falta volver a sortear.
- **Pantalla Gigante (Proyector/TV del salón)**: Muestra la cuenta regresiva, la ruleta giratoria, sonido de redoblantes, fanfarria, confeti y fuegos artificiales al anunciar el ganador.

## 3. Alcance de Funcionalidades (v1)
- Formulario público accesible por QR y link web.
- Validación de mayoría de edad (18+ años) y celular.
- Pantalla de sorteo sincronizada en tiempo real mediante Firebase Firestore.
- Control remoto móvil para el animador o DJ.
- Panel administrativo con listado de próximos cumpleaños (7 días) para fidelización.
- Base de datos en Cloud Firestore y Hosting en Firebase.

## 4. Próximas mejoras (v2)
- Prevención de registros duplicados por número de celular en una misma noche.
- Ocultamiento de datos sensibles (teléfono y cumpleaños) de la vista pública de Firestore.
- Gestión de roles de administrador dinámica (sin correos fijos en las reglas).
