# Sistema de Control de Acceso Vehicular — UAT CUTM Sur

**Hackatón UAT 2026 · Equipo Informatix · Universidad Autónoma de Tamaulipas**

Sistema de registro y control de entradas y salidas de vehículos en tres casetas del campus. Solución desarrollada con **Google AppSheet (no-code)** y **Google Sheets**, conforme a la modalidad indicada al equipo por el docente. La especificación original del hackatón menciona Google Apps Script; **no se atribuye código Apps Script a este proyecto**.

## Probar la aplicación
**Versión de evaluación, con datos de demostración:**  
https://www.appsheet.com/start/b5ba742d-885d-42d0-9970-d961841d3744

1. Abrir el enlace en el navegador; iniciar sesión con una cuenta Google.
2. Entrar a **Control de Acceso**; examinar los movimientos abiertos y cerrados.
3. Seleccionar **+ Add**, registrar una placa ficticia como visitante y elegir la caseta.
4. Abrir el movimiento abierto, pulsar **Registrar Salida**, escoger caseta y guardar.
5. Consultar **Historial y consultas**, **Reporte de Entradas**, **Reporte de Salidas**, **Reportes y Estadísticas**, **Vehículos**, **Incidencias**, **Casetas** y **Gestión de usuarios**.
6. Utilizar únicamente datos ficticios. Los cambios en la DEMO son compartidos entre evaluadores.

La DEMO está separada de la aplicación original; **no debe usarse con datos reales ni en producción**.

## ¿Dónde está el código fuente de una solución no-code?
En AppSheet, la lógica ejecutable se define en **expresiones**, validaciones de columnas, acciones, slices, vistas, automatizaciones Bots y la configuración del modelo de datos. Este repositorio documenta esos artefactos con la sintaxis original de AppSheet y explicaciones de cómo reproducirlos. No hay un proyecto HTML/JavaScript ni un servidor Apps Script que se pueda compilar por separado.

## Contenido del repositorio
- [Arquitectura y flujo de datos](docs/arquitectura.md)
- [Modelo de datos y relaciones](docs/modelo-datos.md)
- [Expresiones ejecutables AppSheet](appsheet/expresiones.md)
- [Acciones y registro de salida](appsheet/acciones.md)
- [Automatizaciones y bitácora](appsheet/automatizaciones.md)
- [Consultas, reportes y exportaciones](docs/reportes-consultas.md)
- [Trazabilidad frente a requisitos](docs/trazabilidad-requisitos.md)
- [Pruebas y criterios de aceptación](docs/pruebas.md)
- [Seguridad, permisos y limitaciones](docs/seguridad-despliegue.md)
- [Guía de reproducción / mantenimiento](docs/reproduccion.md)

## Base documental
- **Documento técnico exportado de AppSheet:** `Documentacion_Tecnica_AppSheet.pdf`, 189 páginas, generado el **21/11/2026 a las 06:30:56**. Referencia utilizada para documentar configuraciones reales; el archivo de exportación se conserva como evidencia del proyecto.
- **Enunciado:** `HACKATON.pdf` (5 páginas).
- La exportación informa 12 tablas técnicas (incluyendo estados internos), 180 columnas, 3 slices, 35 vistas y 36 acciones. Los siete conjuntos funcionales alojados en Google Sheets son `Accesos`, `Personas`, `Vehiculos`, `Casetas`, `UsuariosApp`, `Incidencias` y `Auditoria`.
- La exportación indica `Runnable? Yes` y `Deployable? No` en ese instante. El estado de **Deploy** y las licencias se deben volver a comprobar en AppSheet antes de alegar preparación para producción.

## Alcance y honestidad técnica
La versión de evaluación simplifica permisos para permitir que cuentas de jueces desconocidas usen la DEMO; la original empleaba diferenciación de roles. Esto es **una facilitación de demostración, no seguridad de producción**. La exportación de historial observada es CSV compatible con Excel, no un archivo Excel nativo `.xlsx`. Se documentan pruebas observadas sin inferir una cobertura automática inexistente.

## Equipo
Informatix — Loredo Martinez Orlando Samuel
             Osorio Olivares Edgar Eduardo
             Montelongo Fernández Sheyla
             Pérez Camacho Edgar Eduardo
             Garcia Navarro Carlos Nadir

> El sistema funciona en el servicio alojado de AppSheet. Este repositorio conserva la descripción técnica y expresiones fuente disponibles; no sustituye el acceso a la app en la plataforma.
