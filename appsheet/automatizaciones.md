# Automatizaciones y auditoría

**Fuentes:** capturas del editor de Bots y las pruebas del equipo; exportación de AppSheet que incluye las acciones auxiliares. Atención: el resumen de la exportación indica **0 Workflow Rules**. Esto NO significa necesariamente 0 Bots: los Bots modernos usan Automation y no equivalen a Workflow Rules antiguos.

## Bot AUD - Registrar Entrada
- Evento: adición de fila en `Accesos` (nombre mostrado: `Entrada registrada`).
- Proceso asociado: `Proceso Auditoria Entrada`.
- Acción `Action for Proceso Auditoria Entrada`: `ADD_RECORD_TO` tabla `Auditoria`.
- Asignaciones observadas:

| Campo destino | Expresión |
|---|---|
| AuditoriaID | `UNIQUEID()` |
| FechaHora | `[FechaHoraEntrada]` |
| UsuarioEmail | `[OperadorEntrada]` |
| Accion | `"CREAR_ENTRADA"` |
| TablaAfectada | `"Accesos"` |
| RegistroID | `[AccesoID]` |
| Detalle | `CONCATENATE("Placa: ", [Placa], " - Caseta: ", [CasetaEntradaID])` |

## Bot AUD - Registrar Salida
- Evento esperado: actualización de la fila en `Accesos` cuando `Estado` pasa a `Cerrado`, tras la acción de salida.
- Acción auxiliar `Proceso Auditoria Salida Action - 1`: `ADD_RECORD_TO` tabla `Auditoria`.
- Asignaciones observadas:

| Campo destino | Expresión |
|---|---|
| AuditoriaID | `UNIQUEID()` |
| FechaHora | `[FechaHoraSalida]` |
| UsuarioEmail | `[OperadorSalida]` |
| Accion | `"REGISTRAR_SALIDA"` |
| TablaAfectada | `"Accesos"` |
| RegistroID | `[AccesoID]` |
| Detalle | `CONCATENATE("Placa: ", [Placa], " | Caseta de salida: ", [CasetaSalidaID])` |

**Precisión:** la exportación de configuración de 189 páginas no detalla íntegramente el predicado del evento Bot de salida; se debe comprobar in situ en **Automation → Bots → Event** que no se dispare con actualizaciones que no correspondan a cierres. La prueba funcional de salida fue reportada como exitosa por el equipo.

## Reglas de persistencia y cautelas
- `Auditoria` usa `ADDS_ONLY` en la exportación (evita edición/borrado desde acciones normales AppSheet).
- Esto no equivale a una bitácora legalmente inmutable ni a una garantía frente a ediciones directas de Google Sheets o de su propietario.
- Auditar cambios de autorización, altas de incidencias y modificaciones administrativas adicionales es un **posible trabajo futuro** salvo evidencia concreta de Bots implementados.
