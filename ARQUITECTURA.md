# Arquitectura del Sistema — Cuba Eventos

## 1. Esquema General
El sistema opera sobre **Firebase** (Google Cloud) sin servidores dedicados (arquitectura Serverless):
- **Hosting**: Firebase Hosting (`https://cuba-eventos.web.app/`).
- **Base de datos en tiempo real**: Cloud Firestore.
- **Autenticación**: Firebase Auth (Google Sign-In para administradores).

## 2. Mapa de Páginas y Componentes
1. `index.html`: Formulario público de registro de participantes.
2. `qr.html`: Cartel limpio con código QR de alta resolución para imprimir o proyectar.
3. `pantalla-sorteo.html`: Pantalla para proyectores/LED con sonido, ruleta animada, confeti y pirotecnia digital.
4. `control-remoto.html`: Interfaz móvil para el animador o DJ con acciones rápidas (iniciar sorteo, WhatsApp al ganador, llamar).
5. `admin.html`: Panel administrativo para configurar textos, colores, premios y ver cumpleaños de la semana.
6. `participantes.html`: Tabla de gestión y exportación de datos de los participantes registrados.

## 3. Modelo de Datos (Firestore)
- Colección `participantes_sorteo`:
  - `nombre` (string): Nombre y apellido.
  - `celular` (string): Teléfono de contacto.
  - `fecha_nacimiento` (string YYYY-MM-DD): Fecha de cumpleaños.
  - `consentimiento_datos` (boolean): Aceptación legal Ley 25.326.
  - `acepta_marketing` (boolean): Si acepta avisos futuros.
  - `ya_gano` (boolean): Flag para excluirlo de repetición inmediata si ya ganó.
  - `creado` (timestamp): Fecha y hora de inscripción.
- Documento `sorteo/actual`:
  - `status` (string): 'idle', 'countdown', 'rolling', 'finished'.
  - `entries` (array): Lista de participantes activos en el sorteo.
  - `winnerIndex` (number): Posición del ganador.
  - `durationMinutes` (number): Minutos de cuenta regresiva.
  - `serverStartAt` (timestamp): Momento de inicio de la cuenta regresiva.
- Documento `configuracion/formulario`:
  - Colores, textos, links y premios editables desde el panel admin.
