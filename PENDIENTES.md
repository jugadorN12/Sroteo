# Tareas Pendientes y Mejoras Futuras (PENDIENTES)

## Seguridad
- [ ] **Proteger datos privados en sorteo en vivo**: No guardar celulares ni fechas de nacimiento en `sorteo/actual` ya que es de lectura pública.
- [ ] **Validación en Firestore Rules**: Forzar tipos de datos (`string`, `bool`) y limitar largo máximo de texto para evitar payloads maliciosos.
- [ ] **Roles dinámicos**: Migrar la lista de correos fijos en `firestore.rules` a Custom Claims o colección interna de roles.

## Funcionalidad y Negocio
- [ ] **Anti-duplicados**: Validar si un número de celular ya participó en la misma fecha para evitar inscripciones masivas de un mismo usuario.
- [ ] **Limpieza de código**: Retirar `formulario-sorteo.html` de la raíz si ya se reemplazó completamente por `sorteo-cuba-eventos/index.html`.
