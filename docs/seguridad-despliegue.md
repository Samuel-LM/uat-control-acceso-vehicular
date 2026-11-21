# Seguridad, permisos y despliegue — aclaraciones para el jurado

## Entorno de evaluación (DEMO JURADO)
- Enlace: https://www.appsheet.com/start/b5ba742d-885d-42d0-9970-d961841d3744
- Se usa cuenta Google. `Allow all signed-in users` fue activado para permitir acceso a jueces cuyos correos se desconocían.
- La DEMO conserva un archivo Google Sheets diferente del original; el equipo informó haber probado acceso desde otra cuenta, entrada y salida de `JURADO999` cerrada.
- Los permisos de la DEMO **se ampliaron** para explorar módulos y operar datos ficticios. No representa los límites de acceso recomendados para uso institucional real.
- En el documento técnico los campos de catálogo `UsuariosApp[Rol]` enumeran Guardia, Supervisor y Administrador. Esa clasificación no implica que en la DEMO haya restricciones de roles efectivas.
- No incluir correos, matrículas, nombres y datos personales reales en ningún conjunto de datos público. El acceso público a la app no convierte las tablas en datos seguros.
- Datos de Google Sheets son entregados por AppSheet según permisos del creador, configuración de seguridad y filtros. El equipo debe comprobar su tratamiento antes de cualquier uso fuera de demo.

## Estado de despliegue
- Exportación AppSheet a las 06:30: `Runnable? Yes` y `Deployable? No`. La aplicación pudo ser probada por segunda cuenta según evidencia del equipo, pero ello **no acredita** un paso exitoso de `Deployment Check` ni una licencia comercial.
- El ejercicio presenta un **prototipo demostrable**. No se garantiza SLA, operación 24/7, seguridad empresarial ni licencia para usuarios ilimitados.
- El enunciado del concurso pidió originalmente Google Apps Script y Google Sheets. El equipo informó haber recibido autorización docente para usar Google AppSheet. No se incluye ni se atribuye código Apps Script inexistente.

## Riesgos y mitigaciones
| Riesgo | Mitigación previa a producción |
|---|---|
| Acceso general por cuenta Google | Desactivar `Allow all signed-in users`; usar lista de acceso institucional |
| Manipulación de catálogos por público | Restaurar autorizaciones por rol y filtros de seguridad |
| Exposición de PII | Sustituir/eliminar PII, aplicar minimización y políticas de conservación |
| Casetas sin asignación para evaluadores | En DEMO elección manual; en producción vinculación de rol/caseta |
| Datos de prueba compartidos | Base de pruebas separada; respaldos y limpieza |
| Límite de usuarios/licencia AppSheet | Verificar suscripción y aforo antes de uso institucional |
| Auditoría modificable fuera de AppSheet | Restringir acceso de edición a Sheets y mantener logs adicionales |

## Evidencia y pruebas
Ver `docs/pruebas.md`. Las pantallas de este prototipo no equivalen a auditoría externa de seguridad.
