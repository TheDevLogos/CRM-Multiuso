# CRM Multi-Negocio

CRM multi-tenant en un solo archivo HTML, preparado para publicar en GitHub Pages o cualquier hosting estático y conectar con Google Apps Script + Google Sheets como backend ligero.

## Qué incluye

- Dashboard por tipo de CRM.
- Calendario editable con avisos de día, semana y mes.
- CRUD de registros.
- Persistencia local con `localStorage`.
- Configuración de Web App de Apps Script.
- Push/Pull a Google Sheets.
- Script base de Apps Script integrado para copiar y pegar.

## Archivos

- `index.html`: archivo principal del frontend.
- `README.md`: guía de instalación, despliegue y conexión.

## Requisitos

- Cuenta de Google.
- Un Spreadsheet de Google Sheets.
- Un proyecto en Google Apps Script desplegado como Web App.
- Un hosting estático o GitHub Pages para publicar el HTML.

## Estructura recomendada de Sheets

Crea un Spreadsheet maestro y dentro crea hojas con estos nombres según el tenant:

### Médico
- `contacts`
- `appointments`
- `cases`
- `documents`
- `payments`

### Consultoría
- `contacts`
- `projects`
- `meetings`
- `deliverables`
- `payments`
- `opportunities`

### Despacho
- `contacts`
- `cases`
- `hearings`
- `documents`
- `payments`
- `tasks`

### Inmobiliaria
- `leads`
- `properties`
- `visits`
- `offers`
- `payments`
- `opportunities`

### Ventas
- `leads`
- `pipeline`
- `quotes`
- `payments`
- `activities`

### Servicios
- `contacts`
- `services`
- `schedules`
- `documents`
- `payments`
- `tickets`

## Despliegue en GitHub Pages

1. Crea un repositorio nuevo en GitHub.
2. Sube el archivo `index.html` en la raíz.
3. Entra a **Settings > Pages**.
4. Selecciona la rama principal y la carpeta raíz.
5. Guarda y espera la URL pública.
6. Abre el sitio y prueba el CRM.

## Despliegue en Netlify

1. Entra a Netlify.
2. Sube el archivo `index.html` o la carpeta del proyecto.
3. Publica como sitio estático.
4. Usa la URL generada para probar.

## Despliegue en Vercel

1. Crea un proyecto nuevo.
2. Sube el repositorio o importa desde GitHub.
3. Al ser HTML estático, no necesitas build complejo.
4. Publica y prueba la URL.

## Configuración final del CRM

Abre el CRM y entra al panel **Setup Apps Script**.

### 1. Pega la URL
Usa esta URL de Web App:

`https://script.google.com/macros/s/AKfycbxxVbOtt9GJrf14QaFzhHQaTVLLznnEOZ2P9d1vT-F-ptXMk4hRsJ3HuAkxLcKfdrrYGw/exec`

### 2. Sheet ID
Pega únicamente el ID del Spreadsheet, no la URL completa.

### 3. Token
El token puede quedar vacío al inicio.
Si después quieres proteger la Web App, define un token compartido en Apps Script y en el frontend.

### 4. Prueba
Usa estos botones:
- **Health** para verificar que la Web App responde.
- **Sync completo** para probar Push y Pull.

## Apps Script base

Pega la lógica base en Google Apps Script y luego despliega como Web App.

### Variables a personalizar
- `SHEET_ID`
- `TOKEN`

### Acciones soportadas
- `health`
- `schema`
- `pull`
- `push`

## Flujo recomendado de implementación

1. Crear el Spreadsheet maestro.
2. Crear las hojas por tenant.
3. Pegar el Apps Script base.
4. Configurar `SHEET_ID`.
5. Definir `TOKEN` o dejarlo vacío.
6. Desplegar como Web App.
7. Pegar la URL en el CRM.
8. Ejecutar Health.
9. Probar Sync completo.

## Buenas prácticas

- Mantén un tenant por operación para evitar mezclar datos.
- Usa nombres de hojas consistentes con el mapping.
- Agrega `updated_at` si quieres resolver conflictos en una versión posterior.
- Versiona el HTML en GitHub para poder hacer rollback.
- Haz pruebas primero con datos de demo antes de cargar información real.

## Problemas comunes

### La Web App no responde
- Revisa que esté desplegada como Web App.
- Verifica permisos de ejecución.
- Confirma que la URL sea la correcta.

### El sync no guarda
- Verifica el `Sheet ID`.
- Confirma que las hojas existan.
- Revisa si el token está vacío o coincide con el script.

### No aparecen datos
- Revisa el tenant activo.
- Confirma que el navegador no haya bloqueado el request.
- Verifica que la hoja tenga estructura válida.

## Siguiente mejora sugerida

La versión 11 puede incluir:
- autenticación más robusta,
- mapeo por columnas real,
- `updated_at`,
- conflictos por timestamp,
- y sincronización automática al guardar.

## Licencia de uso interno

Este proyecto está pensado como base de trabajo para implementación interna y customización por cliente.
