# Pruebas funcionales y criterios de aceptación

Casos que el equipo ejecutó durante el hackatón, según capturas y descripciones compartidas. **No son resultados automatizados ni una certificación externa.**

| ID | Caso | Resultado esperado | Evidencia reportada |
|---|---|---|---|
| CP-01 | Registrar entrada con placa ficticia y caseta | Nueva fila `Abierto`; fecha y operador capturados | Sí, flujo de primera meta |
| CP-02 | Registrar salida de estancia abierta | `Cerrado`, fecha/hora, operador y caseta de salida | Sí, segunda meta |
| CP-03 | Repetir placa con estancia abierta | Valid If rechaza duplicidad | Sí, tercera meta |
| CP-04 | Placa DEMO123 | Clasificación `AUTORIZADO` | Sí, tercera meta |
| CP-05 | Placa BLOQ001 (sin autorización) | `REGISTRADO SIN AUTORIZACION`; bloqueo según tipo | Sí, tercera meta |
| CP-06 | Placa nueva VISITA999 | `NO REGISTRADO - VERIFICAR VISITANTE` | Sí, tercera meta |
| CP-07 | Filtrar por placa | Historial filtrado | Sí, búsqueda DEMO |
| CP-08 | Exportación | Descarga CSV del historial | Sí, archivo `AppSheet.ViewData...` |
| CP-09 | Acceso DEMO desde otra cuenta | Visualización de módulos | Sí, prueba en otro navegador |
| CP-10 | Cuenta externa cierra JURADO999 | Nueva estancia pasa a `Cerrado` | Sí, captura entregada |
| CP-11 | Bots entrada/salida a Auditoria | Filas `CREAR_ENTRADA`, `REGISTRAR_SALIDA` | Reportado funcional por el equipo; revisar prueba registrada |
| CP-12 | Prueba de carga y licencia de más de diez usuarios | Comprobar aforo de jueces | No ejecutada/documentada |

## Criterios de revisión del jurado
1. Abrir enlace de DEMO desde una cuenta Google diferente de la propietaria.
2. Confirmar acceso a módulo de consultas/estadísticas y casetas.
3. Registrar `JURADO999` o una placa inédita distinta (por ejemplo `EVAL2026`); evitar duplicado abierto.
4. Elegir caseta de entrada y guardar.
5. Registrar salida y elegir caseta de salida; verificar cambio a `Cerrado`.
6. Abrir reportes y exportar historial CSV.
7. Inspeccionar `Auditoria` desde el entorno autorizado.

## Pruebas adicionales recomendadas
- Un registro de cada tipo de usuario, límites de permisos por rol en app original (en DEMO permisos ampliados), sincronización, incidencia, carga de varias cuentas y reserva de acceso.
