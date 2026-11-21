# Trazabilidad de requisitos

Fuente: `HACKATON.pdf` (alcance funcional mínimo) y configuración observada en `Documentacion_Tecnica_AppSheet.pdf`. **Evidenciado** indica configuración o prueba reportada, no certificación exhaustiva; **por verificar** indica que no consta prueba suficiente o una diferencia entre requisito y solución.

| ID | Requisito del hackatón | Implementación / evidencia | Estado |
|---|---|---|---|
| RF-01 | Vehículos autorizados | `Vehiculos[Autorizado]`, clasificación `ResultadoAutorizacion` | Evidenciado |
| RF-02 | Empleados, estudiantes y visitantes | `Personas` y `TipoUsuario` | Evidenciado |
| RF-03 | Tres casetas | `Casetas`, referencias desde entradas/salidas | Evidenciado |
| RF-04 | Entrada de vehículos | `Accesos_Form`, fecha/operador automáticos | Probado |
| RF-05 | Salida de vehículos | Acción `Registrar Salida` | Probado |
| RF-06 | Placa y tipo usuario | `Placa` y enum de cuatro tipos | Evidenciado |
| RF-07 | Consulta por placa | Buscador, `ConsultaFiltrada` | Probado |
| RF-08 | Consulta por fechas | `FechaDesde` y `FechaHasta` | Configurado |
| RF-09 | Consulta por caseta | `FiltroCaseta` y referencias de caseta | Configurado |
| RF-10 | Consulta por tipo | `FiltroTipo` | Configurado |
| RF-11 | Entradas y salidas por periodo | `EntradasPeriodo`, `SalidasPeriodo` | Configurado |
| RF-12 | Vehículos más frecuentes | `Grafica Frecuencia` | Configurado |
| RF-13 | Horarios de mayor afluencia | `Grafica Horarios` | Configurado |
| RF-14 | Exportación a Excel | `Exportar Historial CSV` | **Parcial:** CSV abre en Excel; sin `.xlsx` nativo |
| RF-15 | Bitácora de actividades | `Auditoria` y Bots entrada/salida | Probado según equipo; otros eventos no confirmados |
| RF-16 | Restricción de permisos por tipo de usuario | `UsuariosApp[Rol]`; original con roles | **Parcial en DEMO:** acceso ampliado para jurados |

## Notas de conformidad
- El PDF original exige **Google Apps Script + Google Sheets**; el equipo reporta **autorización docente para AppSheet + Sheets**. La variante no representa una implementación Apps Script.
- Las exigencias del SRS (RF/RNF, casos de uso, diagramas) y manual están en documentos de entrega distintos; estos archivos técnicos sirven de base.
- La exportación aparece con `Deployable? No` a las 06:30; el uso de prototipo es verificable pero despliegue productivo aprobado no está confirmado.

## Trazabilidad de evidencias
Cada fila puede vincularse a captura identificada, timestamp y registro de prueba en el PDF de requisitos/manual. Evitar calificar como “cumplido 100 %” sin evidencia.
