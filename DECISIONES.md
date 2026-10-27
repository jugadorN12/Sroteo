# Registro de Decisiones de Arquitectura (ADR)

## [2026-10-27] - Decisión 01: Adopción de Firebase Hosting y Firestore
- **Decisión**: Utilizar Firebase Hosting para la distribución web estática y Cloud Firestore para sincronización en tiempo real entre el control remoto y la pantalla del sorteo.
- **Motivo**: No requiere mantener servidores propios, es altamente reactivo ante eventos en vivo (tiempos de respuesta en milisegundos) y se mantiene dentro de los límites gratuitos para uso estándar en eventos.
- **Alternativas descartadas**: Servidor Express/Node.js propio (mayor costo de mantenimiento y complejidad de despliegue).

## [2026-10-27] - Decisión 02: Vinculación con repositorio remoto Git en GitHub
- **Decisión**: Conectar el proyecto a `https://github.com/jugadorN12/Sroteo.git` en la rama `main` para control de cambios seguro.
- **Motivo**: Cumplir con la regla de respaldo previo a cualquier refactorización o cambio crítico de seguridad.
