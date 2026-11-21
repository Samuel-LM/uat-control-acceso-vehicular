# Reproducir / mantener el prototipo AppSheet

Este proyecto **no se ejecuta desde GitHub**: las configuraciones se aplican a una aplicación alojada en el servicio AppSheet, con Google Sheets como fuente. No existe un `npm install`, compilación JavaScript o despliegue Apps Script de esta versión.

## Requisitos previos
- Cuenta Google autorizada para crear aplicaciones en AppSheet.
- Acceso a Google Sheets.
- Un Google Sheets **propio y ficticio** con pestañas: `Accesos`, `Personas`, `Vehiculos`, `Casetas`, `UsuariosApp`, `Incidencias`, `Auditoria`.
- Campos según `docs/modelo-datos.md` y `Documentacion_Tecnica_AppSheet.pdf` (evidencia de exportación completa en custodia del equipo).

## Guía resumida
1. Crear el archivo Sheets con encabezados exactos, sin registros reales.
2. En AppSheet, **Create → Start with your own data** y conectar archivo Sheets.
3. En **Data → Columns**, asignar claves `UNIQUEID()`, tipos `Ref`, `Enum`, `DateTime`, `Email`; configurar `Valid If` y las fórmulas de `appsheet/expresiones.md`.
4. Verificar que `CasetaEntradaID` y `CasetaSalidaID` referencian `Casetas`.
5. Crear acción `Registrar Salida` con los cuatro cambios simultáneos descritos en `appsheet/acciones.md`.
6. Crear los tres slices y las vistas de tabla/gráficas/dashboard de `docs/reportes-consultas.md`.
7. Configurar Bots de entrada/salida e inserción de eventos de auditoría siguiendo `appsheet/automatizaciones.md`.
8. Crear roles y visibilidad, **separando** la configuración DEMO de la configuración institucional; nunca conceder `ALL_CHANGES` a usuarios anónimos en una versión real.
9. Probar una placa permitida, una sin autorización, una nueva visitante, duplicado abierto y salida con caseta seleccionada.
10. Revisar **Manage → Deploy → Deployment Check** antes de operación productiva; resolver advertencias de licencia/configuración.

## Nota sobre fidelidad de reproducción
Este repositorio contiene **artefactos fuente verificables y documentación de configuración**. No contiene todavía un export automático de la definición completa alojada en AppSheet; para una reconstrucción idéntica se necesita también la exportación técnica completa y acceso al editor AppSheet del propietario. La existencia de este repositorio no concede permisos sobre el editor.

## Mantenimiento
- Versionar cambios en expresiones y reglas.
- Nunca subir el Google Sheet operacional con datos personales.
- Mantener evidencia de pruebas y registrar cambios de seguridad por entorno.
