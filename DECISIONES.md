# Registro de Decisiones de Arquitectura (ADR)

## [2026-10-27] - Decisión 01: Adopción de Firebase Hosting y Firestore
- **Decisión**: Utilizar Firebase Hosting para la distribución web estática y Cloud Firestore para sincronización en tiempo real entre el control remoto y la pantalla del sorteo.
- **Motivo**: No requiere mantener servidores propios, es altamente reactivo ante eventos en vivo (tiempos de respuesta en milisegundos) y se mantiene dentro de los límites gratuitos para uso estándar en eventos.
- **Alternativas descartadas**: Servidor Express/Node.js propio (mayor costo de mantenimiento y complejidad de despliegue).

## [2026-10-27] - Decisión 02: Vinculación con repositorio remoto Git en GitHub
- **Decisión**: Conectar el proyecto a `https://github.com/jugadorN12/Sroteo.git` en la rama `main` para control de cambios seguro.
- **Motivo**: Cumplir con la regla de respaldo previo a cualquier refactorización o cambio crítico de seguridad.

## [2026-10-27] - Decisión 03: Blindaje de privacidad y transacciones atómicas en sorteo
- **Decisión**: Separar el canal público (`sorteo/actual`, leído por proyectores sin autenticación) del canal privado administrativo (`sorteo/privado_ganador`, protegido por login). Utilizar `writeBatch` para atomicidad en la designación de ganadores.
- **Motivo**: Cumplir con la Ley 25.326 evitando que números de celular y fechas de nacimiento viajen a pantallas públicas. Evitar desincronizaciones de base de datos ante caídas de red durante el evento.
