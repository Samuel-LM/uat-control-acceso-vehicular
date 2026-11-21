# Acciones y flujo de registro

Se documenta la acción explícita **Registrar Salida**, presente en la exportación `Documentacion_Tecnica_AppSheet.pdf`, sección **Behavior → Actions**.

## Registrar Salida
- **Tabla:** `Accesos`
- **Tipo:** `Data: set the values of some columns in this row` (internamente `SET_COLUMN_VALUE`)
- **Presentación:** `Display_Prominently`
- **Parámetro de entrada:** `CasetaSalida` (selección de caseta)
- **Condición de disponibilidad:**
```appsheet
AND([Estado] = "Abierto", ISBLANK([FechaHoraSalida]))
```
- **Asignaciones (una única acción):**
```text
Estado           := "Cerrado"
FechaHoraSalida  := NOW()
OperadorSalida   := USEREMAIL()
CasetaSalidaID   := [_INPUT].[CasetaSalida]
```

No insertar `NOW()` como App formula de `FechaHoraSalida`: el valor se establece **al registrar la salida**, no al registrar entrada.

## Entrada nueva
El formulario `Accesos_Form` guarda un registro con llave `UNIQUEID()`, fecha/hora `NOW()`, correo del operador `USEREMAIL()` y `Estado = "Abierto"`. Al ingresar placa aplica `Valid If` y la clasificación de autorización.

## Exportación del historial
Acción `Exportar Historial CSV`: `EXPORT_VIEW`, localización `es-MX`, etiqueta "Exportar Historial". Genera CSV, no Excel nativo. El CSV puede abrirse desde Excel; documentar como **CSV compatible con Excel**.

## Otros artefactos evidenciados
La exportación describe 36 acciones, incluidas `Add`, `Edit`, `Delete`, `View Ref`, `Compose Email`, los accesos a datos de gráficas y dos acciones de inserción en `Auditoria`. Los 36 incluyen acciones estándar/generadas; no todas son lógica personalizada.
