# 🚛🏗️ Melon Apps Archive

Repositorio centralizado de entregables para el ecosistema de aplicaciones de **Melon**.

## 📂 Estructura del Repositorio
El repositorio está organizado jerárquicamente por ambiente, aplicación y versión para facilitar la gestión de lanzamientos y la revisión por parte del cliente:

1.  **qa/**: Versiones de prueba interna y validación de nuevas funcionalidades.
2.  **preproduccion/**: Versiones estables para revisión del cliente en entornos controlados (evita alteración de datos reales).
3.  **produccion/**: Versiones finales certificadas para despliegue en tiendas o hotfixes rápidos.

## 🚀 Guía de Navegación
Para encontrar un APK, sigue esta ruta de carpetas:
`[ambiente] / [nombre-app] / [versión] /`

Cada carpeta de versión incluye:
* 📦 El archivo **.apk** (Ej: `miseguridad-v1.2.0-qa.apk`).
* 📜 Un archivo **README.md** con el changelog y detalles técnicos de esa compilación.

---

## 📝 Formato del Changelog (README por versión)
Para mantener la trazabilidad, cada entrega debe documentar:
* **Fecha:** Día de generación del build.
* **Ambiente:** QA, Pre-producción o Producción.
* **Novedades:** Funcionalidades añadidas.
* **Fixes:** Errores corregidos.
* **Notas:** Instrucciones especiales (ej: "Requiere desinstalar versión anterior").