# MiCamión v0.1.2-beta
Fecha: 23/06/2026
Ambiente: QA
APK: micamion-qa v1.0.2-beta.apk

Entrega incremental sobre v0.1.0-beta. Actualiza vistas de orden de carga para reflejar
la nueva estructura de la API (items por entrega), introduce un sistema de notificaciones
en foreground con diálogos por tipo, y unifica el estilo de todos los SnackBars.

---

Funcionalidades incluidas

Orden de Carga — Granel
- Rediseño completo: un BorderCard por destino con borde naranja
- Cada tarjeta muestra cliente, dirección, estado, y sus productos como items
- Card de planta con IconBox (planta + número de ticket JDE)
- Número de secuencia con caja estilo IconBox (_NumberBox)
- Indicador de "Requiere muestra" por producto

Orden de Carga — Envasados
- Productos por item dentro de cada tarjeta de entrega
- Cantidad formateada: sin decimales si son cero, máximo 2 decimales
- Total de ocupación calculado desde items (no desde delivery)

Notificaciones en Foreground
- Diálogo modal al recibir notificaciones con la app abierta
- Tipos soportados: appointment.created (nueva citación) y load_order_called (orden llamada)
- Citación: muestra fecha, hora y planta; botón navega a /appointment
- Orden de carga: muestra mensaje de la notificación y estado; botón navega a /current-load-order
- Notificaciones de otros tipos son ignoradas (solo log en consola)

SnackBars — Unificación de estilo
- Nuevo widget CustomSnackBar con tipos: success, error, warning, info, neutral
- Colores e íconos automáticos según tipo; neutral (negro) como default
- Comportamiento floating aplicado en toda la app
- Todos los call sites migrados al nuevo widget

---

Cambios técnicos

Modelos
- LoadOrderDeliveryItem: nuevo modelo de dominio (id, guideNumber, productName, quantity, unit, requiresSample)
- LoadOrderDelivery: quantity/unit ahora nullable; agrega List<LoadOrderDeliveryItem> items
- LoadOrder: eliminados campos top-level clientName, productName, quantity, unit, requiresSample

API Response
- LoadOrderDeliveryItemResponse: nuevo response model con fromJson
- LoadOrderDeliveryResponse: parsea items[] desde JSON

Servicios / Handlers
- NotificationService: nuevo stream onForegroundMessage para mensajes en foreground
- NotificationHandler: filtra mensajes por type y expone onShowDialog stream
- bootstrap.dart: suscripción a NotificationHandler; navigator key global para showDialog fuera del árbol

UI
- CurrentLoadOrderBulkScreen: reescritura completa con BorderCard, IconBox y _NumberBox
- CurrentLoadOrderPackagedScreen: items en delivery cards, _formatQty helper
- CustomSnackBar: extiende SnackBar directamente (sin static build)
- NotificationDialog: dialog con header degradado azul, info card con divisores, botón de acción por tipo

Correcciones
- Error 409 en confirmación de carga: mensaje específico vía ConflictException
- Back button en /appointment y /current-load-order: canPop() ? pop() : go('/') para evitar GoError