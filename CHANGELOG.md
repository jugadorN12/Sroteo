# Historial de Cambios (CHANGELOG)

Todos los cambios notables de este proyecto se registrarán en este archivo.

## [1.1.0] - 2026-10-27
### Seguridad y Privacidad
- **Blindaje de canal público de sorteo**: `sorteo/actual` ya no transmite teléfonos celulares ni fechas de nacimiento a la pantalla pública.
- **Canal administrativo de contacto**: Los datos privados de contacto del ganador ahora se canalizan por `sorteo/privado_ganador`, requiriendo autenticación administrativa en Firestore.
- **Validaciones estrictas en Firestore**: En `firestore.rules`, se limitan los campos permitidos (`hasOnly`), se validan tipos (`is string`), se restringen longitudes (nombres 2-80 caracteres, teléfonos 8-25) y se bloquea la manipulación de estados de ganador (`ya_gano == false`).
- **Atomicidad**: Se implementó `writeBatch` tanto en `admin.html` como en `control-remoto.html` para asegurar que el registro de ganador, el estado de la pantalla y los datos de contacto se sincronicen en una única operación atómica.

## [1.0.0] - 2026-10-27
### Añadido
- Inicialización del repositorio Git y conexión con GitHub (`jugadorN12/Sroteo.git`).
- Configuración de exclusiones con `.gitignore` raíz.
- Estructura de documentación estándar del equipo: `PROYECTO.md`, `ARQUITECTURA.md`, `DECISIONES.md`, `PROGRESO.md`, `PENDIENTES.md`, `CHANGELOG.md`.
- Módulos del sistema de sorteo en `sorteo-cuba-eventos/`: formulario, pantalla interactiva, control remoto, panel admin, QR y gestión de participantes.
