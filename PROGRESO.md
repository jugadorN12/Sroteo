# Estado del Proyecto (PROGRESO)

## Hecho
- [x] Formulario web de inscripción en Firebase Hosting (`index.html`).
- [x] Cartel QR para escaneo en el salón (`qr.html`).
- [x] Pantalla interactiva de sorteo con ruleta, sonidos y confeti (`pantalla-sorteo.html`).
- [x] Control remoto móvil para el DJ/animador (`control-remoto.html`).
- [x] Panel administrativo con cumpleaños semanales (`admin.html`).
- [x] Creación del repositorio Git y respaldo en GitHub (`jugadorN12/Sroteo.git`).
- [x] Documentación base del proyecto según estándares (`PROYECTO.md`, `ARQUITECTURA.md`, etc.).
- [x] **Blindaje de privacidad y seguridad**: Se eliminó la exposición de celulares y cumpleaños en `sorteo/actual`.
- [x] **Transacciones atómicas**: Adopción de `writeBatch` en `admin.html` y `control-remoto.html`.
- [x] **Hardening de reglas**: Validación de tipos, tamaños y campos restringidos en `firestore.rules`.
- [x] **Despliegue a producción de v1.1.0** completado en Firebase.
- [x] **Prevención de registros duplicados por celular y noche**: Normalización de teléfonos, cálculo de noche contable (corte 07:00 AM) y bloqueo en Firestore.

## En Curso
- [ ] Despliegue de versión 1.2.0 (reglas y formulario anti-duplicados).

## Siguiente
- [ ] Retiro o archivo de versiones redundantes (`formulario-sorteo.html` de la raíz).
