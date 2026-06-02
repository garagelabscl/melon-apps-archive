# 🚛🏗️ Melon Apps Archive

Repositorio centralizado de entregables para el ecosistema de aplicaciones de **Melon**.

## 📋 Aplicaciones

| App | Descripción | Ir |
|-----|-------------|----|
| **Mimixer** | Mixer de operaciones | [📂 Ver entregas →](mimixer/) |
| **Mi Flota** | Gestión de flotas | [📂 Ver entregas →](miflota/) |
| **MiCamión** | Gestión logística para conductores de camión | [📂 Ver entregas →](micamion/) |

## 📂 Estructura del Repositorio

```
Melon Archives/
├── mimixer/
│   ├── README.md          ← Versiones actuales y entregas recientes
│   ├── CHANGELOG.md       ← Historial completo
│   ├── qa/                ← Builds apuntando a QA
│   ├── preprod/           ← Builds apuntando a Pre-producción
│   └── prod/              ← Builds de Producción
│       └── v3.0.0 - 235/
│           ├── mimixer.prod.apk
│           └── readme.md
├── miflota/
│   ├── README.md
│   ├── CHANGELOG.md
│   ├── qa/
│   ├── preprod/
│   └── prod/
├── micamion/
│   ├── README.md
│   └── qa/
└── README.md              ← Este archivo
```

## 🚀 ¿Cómo encontrar un APK?

1. Elige la app de la tabla de arriba.
2. En el README de la app verás las **versiones actuales** por ambiente y las **entregas recientes** con su descripción.
3. Haz clic en el link de descarga del ambiente que necesites.

Ruta de carpetas: `[app] / [ambiente] / [versión] /`

### Ambientes

| Ambiente | Descripción |
|----------|-------------|
| **qa/** | Entorno de prueba interna y validación de nuevas funcionalidades. |
| **preprod/** | Entorno controlado para revisión del cliente (con datos de producción pero con accesos bajo demanda para mayor control). |
| **prod/** | Versión final certificada para despliegue en tiendas. |

### Contenido de cada carpeta de versión

* 📦 Archivo **.apk** con formato `<app>.<ambiente>.apk` (Ej: `mimixer.prod.apk`).
* 📜 Archivo **readme.md** con changelog y detalles técnicos de la compilación.
