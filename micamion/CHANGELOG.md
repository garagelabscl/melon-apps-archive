# MiCamión — Changelog

## v1.0.0-beta — 02/06/2026 🔄 En revisión

Primera entrega QA. La app nunca ha sido lanzada a producción.

### Incluido en esta versión

**Autenticación y Seguridad**
- Login con OTP vía email
- Sistema de permisos dinámicos por perfil (`Entidad.contexto.acción.destino`)
- Panel superadmin para gestión global de usuarios, perfiles y permisos

**Panel de Administración**
- CRUD de empresas, usuarios, conductores y vehículos
- Asignación de perfiles y permisos por usuario
- Auto-envío de credenciales por email al crear usuarios

**Plantas y Vehículos**
- Gestión de plantas (tipo Plant / Branch)
- Semáforo de estado del vehículo (RTI, GPS, checklist)

**Conductores**
- Gestión de conductores con asignación de vehículo y estado laboral
- Historial de estados

**Citaciones**
- Reserva de turnos para presentarse a planta
- Estados: pendiente → confirmada → cumplida / no presentado / cancelada / reprogramada
- Cálculo de puntualidad (±30 min)

**Acreditación (Semáforo)**
- 4 requisitos: test de fatiga (Angelis), checklist (MiFlota), GPS (UNIGIS), RTI vehículo
- Bloqueo de avance a la cola si algún requisito falla

**Cola de Asignación**
- Cola FIFO por planta para carga granel
- Asignación directa para carga envasada (plantas tipo Branch)
- Reordenamiento manual con justificación desde el panel supervisor

**Chat Supervisor ↔ Conductor**
- Mensajería en tiempo real vía Mercure (SSE)
- Respuestas rápidas predefinidas

**Órdenes de Carga**
- Sincronización de órdenes desde JDE vía webhook
- Confirmación de carga por pesaje Webtrack (granel) o manual (envasado)

**Guías de Despacho y Entrega**
- Creación automática desde webhook Visión/Paperless
- Entrega completa, parcial o con rechazo en destino
- Firma digital del receptor + fotos de evidencia (AWS S3)
- Historial de guías con todos los estados
