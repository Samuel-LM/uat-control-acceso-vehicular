# Consultas, reportes y análisis

La exportación AppSheet (21-11-2026) incluye tres slices `ConsultaFiltrada`, `EntradasPeriodo`, `SalidasPeriodo`; vistas de tabla y cuatro gráficas integradas en el `Panel de Control` (dashboard).

## Parámetros por usuario
`USERSETTINGS("FiltroPlaca")`, `USERSETTINGS("FechaDesde")`, `USERSETTINGS("FechaHasta")`, `USERSETTINGS("FiltroCaseta")`, `USERSETTINGS("FiltroTipo")`.

## Slice ConsultaFiltrada — filtro de filas
```appsheet
AND(
  OR(ISBLANK(USERSETTINGS("FiltroPlaca")),
     CONTAINS(UPPER([Placa]), UPPER(USERSETTINGS("FiltroPlaca")))),
  OR(ISBLANK(USERSETTINGS("FechaDesde")),
     DATE([FechaHoraEntrada]) >= USERSETTINGS("FechaDesde")),
  OR(ISBLANK(USERSETTINGS("FechaHasta")),
     DATE([FechaHoraEntrada]) <= USERSETTINGS("FechaHasta")),
  OR(ISBLANK(USERSETTINGS("FiltroCaseta")),
     [CasetaEntradaID] = USERSETTINGS("FiltroCaseta"),
     [CasetaSalidaID] = USERSETTINGS("FiltroCaseta")),
  OR(ISBLANK(USERSETTINGS("FiltroTipo")),
     [TipoUsuario] = USERSETTINGS("FiltroTipo"))
)
```

## Slice EntradasPeriodo
```appsheet
AND(
  ISNOTBLANK([FechaHoraEntrada]),
  OR(ISBLANK(USERSETTINGS("FechaDesde")),
     DATE([FechaHoraEntrada]) >= USERSETTINGS("FechaDesde")),
  OR(ISBLANK(USERSETTINGS("FechaHasta")),
     DATE([FechaHoraEntrada]) <= USERSETTINGS("FechaHasta"))
)
```

## Slice SalidasPeriodo
```appsheet
AND(
  [Estado] = "Cerrado", ISNOTBLANK([FechaHoraSalida]),
  OR(ISBLANK(USERSETTINGS("FechaDesde")),
     DATE([FechaHoraSalida]) >= USERSETTINGS("FechaDesde")),
  OR(ISBLANK(USERSETTINGS("FechaHasta")),
     DATE([FechaHoraSalida]) <= USERSETTINGS("FechaHasta"))
)
```

## Gráficas
- `Grafica Entradas`: histograma por `DiaEntradaGrafica`.
- `Grafica Salidas`: histograma por `DiaSalidaGrafica`.
- `Grafica Frecuencia`: histograma por `Placa`.
- `Grafica Horarios`: histograma por `HoraEntradaGrafica`.
- `Panel de Control`: dashboard que reúne las cuatro vistas.

## Exportación
Acción `Exportar Historial CSV` de tipo `EXPORT_VIEW` (es-MX). CSV compatible con Excel; **no prometer exportación directa a .xlsx o PDF**. Se puede convertir a Excel o PDF fuera de la app cuando el jurado lo necesite.

## Limitaciones
Los filtros por settings dependen de sincronización y conexión; no afirmar funcionamiento totalmente offline. Un histograma y su agregación no deben confundirse con medidas certificadas de tráfico sin validar la muestra y los datos de entrada.
