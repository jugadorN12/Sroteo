# Tareas Pendientes y Mejoras Futuras (PENDIENTES)

## Hecho recientemente
- [x] **Proteger datos privados en sorteo en vivo**: Números de celular y fechas de nacimiento ya no viajan al canal público.
- [x] **Validación estricta en Firestore Rules**: Forzado de tipos (`string`, `bool`), largos máximos y campos autorizados.
- [x] **Control anti-duplicados por celular**: Normalización de teléfonos y bloqueo por noche de evento (con corte a las 07:00 AM).
- [x] **Transacciones atómicas**: Sincronización conjunta de ganadores con `writeBatch`.
- [x] **Despliegue a producción**: Versión 1.2.0 activa en Firebase Hosting y Firestore.

## Pendientes actuales

### 1. Limpieza y orden (Inmediato)
- [ ] Eliminar borrador viejo `formulario-sorteo.html` de la raíz.
- [ ] Revisar o archivar la subcarpeta `sorteo-cuba-eventos/backup_local_/`.

### 2. Pruebas y verificación (QA)
- [ ] Probar el flujo de registro real en un celular y verificar el rechazo de celular duplicado.
- [ ] Probar el giro de ruleta y el botón de WhatsApp al ganador desde el control remoto.

### 3. Mejoras operativas (Para más adelante / v2)
- [ ] **Roles dinámicos**: Poder agregar y quitar correos de administradores (staff/animadores) desde el panel de administración, sin tener que editar código en `firestore.rules`.
- [ ] **Filtro por noche en la lista de participantes**: En `participantes.html`, poder filtrar participantes por fecha de evento para separar los inscriptos de cada noche.
