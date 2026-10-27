# Historial de Cambios (CHANGELOG)

Todos los cambios notables de este proyecto se registrarán en este archivo.

## [1.2.0] - 2026-10-27
### Añadido y Mejorado
- **Control anti-duplicados por celular**: Se normalizan los teléfonos (quitando prefijos `0`, `15`, `+54` y caracteres no numéricos) y se asocian a la noche del evento (`fecha_evento`).
- **Noche contable para boliches (Corte 07:00 AM)**: Las inscripciones realizadas entre las 00:00 y las 07:00 AM se unifican bajo la noche del día anterior, evitando que una persona burle el sistema al pasar la medianoche.
- **Validación criptográfica en Firestore Rules**: El ID de cada nuevo registro se valida para coincidir con `${fecha_evento}_${celular_normalizado}`. Si el usuario intenta registrarse de nuevo esa noche, Firestore rechaza la operación (`permission-denied`) y la interfaz notifica amablemente que ya está registrado.
- **Limpieza de código y repositorio**: Se eliminó el borrador obsoleto `formulario-sorteo.html` de la raíz y la carpeta `sorteo-cuba-eventos/backup_local_/`.
- **Temática visual de Halloween**: Se integró fondo temático de alta resolución (`fondo-halloween.jpg`) en la pantalla gigante de sorteo (`pantalla-sorteo.html`), con overlay de contraste y sombras reforzadas para máxima legibilidad de textos y logo.

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
