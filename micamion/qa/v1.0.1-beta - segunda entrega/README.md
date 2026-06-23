
MiCamión v1.0.1-beta — Segunda Entrega QA
Fecha: 11/06/2026
Ambiente: QA
APK: micamion-qa v1.0.1.apk

Entrega incremental sobre v1.0.0-beta. Agrega registro de llegada a obra en guías de despacho.

Funcionalidades incluidas
Guías de Despacho — Registro de llegada a obra

Nuevo botón "Registrar llegada a obra" en el detalle de cada guía de despacho
Llama al endpoint POST /api/delivery/{id}/arrive y almacena el timestamp de llegada (arrived_at)
El botón desaparece una vez registrada la llegada (se oculta si arrivedAtSiteAt ya tiene valor)
Indicador de carga mientras el request está en curso
Feedback visual mediante snackbar: éxito (verde) o error (rojo) según resultado de la llamada
Cambios técnicos
DispatchGuide — nuevo campo arrivedAtSiteAt (nullable)
DispatchGuideService — nuevo método registerArrival(guideId)
DispatchGuideRepository — expone registerArrival al viewmodel
DispatchGuideViewModel — nuevo estado isArrivalLoading / arrivalError + método registerArrival
DispatchGuideScreen — renderiza el botón condicionalmente en el panel de detalle