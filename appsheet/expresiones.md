# Expresiones fuente AppSheet

Transcripciones de valores observados en `Documentacion_Tecnica_AppSheet.pdf` (21-11-2026, 06:30). Pegar únicamente en la propiedad y tabla indicadas: AppSheet no interpreta este archivo Markdown automáticamente. Las expresiones que siguen no son JavaScript ni Apps Script.

## Accesos[AccesoID] — Initial value
```appsheet
UNIQUEID()
```

## Accesos[Placa] — Valid If (una estancia abierta por placa)
```appsheet
AND(
  ISNOTBLANK([_THIS]),
  COUNT(
    SELECT(
      Accesos[AccesoID],
      AND(
        UPPER(TRIM([Placa])) = UPPER(TRIM([_THISROW].[Placa])),
        [Estado] = "Abierto",
        [AccesoID] <> [_THISROW].[AccesoID]
      )
    )
  ) = 0
)
```

## Accesos[TipoUsuario] — Valid If (la política configurada en la DEMO)
```appsheet
AND(
  COUNT(
    SELECT(Vehiculos[VehiculoID],
      AND(
        UPPER(TRIM([Placa])) = UPPER(TRIM([_THISROW].[Placa])),
        [Autorizado] = FALSE
      )
    )
  ) = 0,
  OR(
    [_THIS] = "Visitante",
    COUNT(
      SELECT(Vehiculos[VehiculoID],
        AND(
          UPPER(TRIM([Placa])) = UPPER(TRIM([_THISROW].[Placa])),
          [Autorizado] = TRUE
        )
      )
    ) > 0
  )
)
```

El mensaje de error configurado es: "Acceso no permitido: placa sin autorización o tipo de usuario incorrecto. Si es un visitante nuevo, selecciona Visitante y verifica su identificación." Interpretación: un vehículo explícitamente registrado con `Autorizado = FALSE` se bloquea; un vehículo no registrado se admite únicamente en categoría Visitante. Verificar identidad real es una tarea humana.

## Accesos[ResultadoAutorizacion] — App formula (virtual)
```appsheet
IFS(
  ISBLANK([Placa]), "SIN PLACA",
  COUNT(
    SELECT(Vehiculos[VehiculoID],
      AND(
        UPPER(TRIM([Placa])) = UPPER(TRIM([_THISROW].[Placa])),
        [Autorizado] = TRUE
      )
    )
  ) > 0, "AUTORIZADO",
  COUNT(
    SELECT(Vehiculos[VehiculoID],
      UPPER(TRIM([Placa])) = UPPER(TRIM([_THISROW].[Placa]))
    )
  ) > 0, "REGISTRADO SIN AUTORIZACION",
  TRUE, "NO REGISTRADO - VERIFICAR VISITANTE"
)
```
*El estado virtual de autorización es una clasificación de la placa y no una verificación física de credenciales.*

## Accesos[FechaHoraEntrada] — Initial value
```appsheet
NOW()
```
## Accesos[OperadorEntrada] — Initial value
```appsheet
USEREMAIL()
```
## Accesos[CasetaEntradaID] — Initial value
```appsheet
LOOKUP(USEREMAIL(), "UsuariosApp", "Correo", "CasetaID")
```
En DEMO se permite seleccionar manualmente la caseta aun cuando este LOOKUP quede vacío.

## Accesos[Estado] — Initial value
```appsheet
"Abierto"
```
La propiedad `Editable?` de Estado es `FALSE` en la exportación para que la acción de salida controle el cierre.

## Auxiliares de gráficas (App formula, virtuales)
```appsheet
TEXT([FechaHoraEntrada], "YYYY-MM-DD")
```
`DiaEntradaGrafica`.
```appsheet
IF(ISBLANK([FechaHoraSalida]), "", TEXT([FechaHoraSalida], "YYYY-MM-DD"))
```
`DiaSalidaGrafica`.
```appsheet
TEXT([FechaHoraEntrada], "HH")
```
`HoraEntradaGrafica`.

## Roles (catálogo)
`UsuariosApp[Rol]`: `Guardia`, `Supervisor`, `Administrador`. La demo altera visibilidad y permisos para evaluadores no invitados. La existencia del catálogo de roles no implica que cada vista de la DEMO restrinja efectivamente el acceso.
