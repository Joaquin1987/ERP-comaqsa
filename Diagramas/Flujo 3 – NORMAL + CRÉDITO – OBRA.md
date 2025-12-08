Flujo 3 – NORMAL + CRÉDITO – OBRA

Este flujo describe el proceso de compras cuando la requisición no es crítica, pertenece a Obra, y el método de pago es crédito.

El elemento clave de este flujo es que no existe pago antes de la entrega y que la validación económica depende de si la compra corresponde o no a un concepto presupuestado de obra.

La compra solo se cierra cuando se cumple la Conciliación Tripartita:

OC vs Recepción

OC vs Factura

Factura vs CxP

A continuación se describe el proceso paso a paso:

1. Requisición

El solicitante genera una requisición. Esta inicia en estado Pendiente.
Debe incluir: descripción, cantidades, especificaciones, si aplica a un concepto presupuestado de obra, y motivo.

2. Validación Técnica

El Jefe de Área revisa la requisición.
Valida necesidad, cantidades, especificaciones y si corresponde a un concepto presupuestado.

Si aquí se marca Crítica, el flujo abandona esta ruta y pasa al flujo Crítico + Crédito – Obra.

3. Cotizaciones

Según el monto de la requisición:

≤ 5,000 → 1 cotización

5,001–15,000 → 2 cotizaciones

15,000 → 3 cotizaciones + comparativo

4. Validación Económica – Obra

Se valida según si la compra corresponde o no a un concepto presupuestado.

4.1 Si SÍ es concepto presupuestado

Validaciones:

PU real ≤ PU presupuestado

Saldo del concepto suficiente

Resultados:

PU ≤ PU presupuestado y saldo suficiente → Autorización automática

PU > PU presupuestado → Autorización del área de obra

Saldo insuficiente → Sobreejercicio (20k / 50k / DG)

4.2 Si NO es concepto presupuestado

Aplican rangos tipo Taller:

≤ 20k → Jefe de Área

20k–50k → Director de Área

50k → Director General

5. Orden de Compra (OC) Normal

Se genera la OC normal con precio final definido.
No puede generarse sin validación económica previa.

6. Entrega (Crédito)

El proveedor entrega los bienes o ejecuta el servicio después de emitirse la OC normal.
En flujo normal + crédito no existe pago antes de la entrega.

7. Recepción Formal

Se valida:

Cantidades vs OC

Calidad

Coincidencia contra concepto presupuestado (si aplica)

8. Factura

Debe coincidir con:

La OC normal

La recepción formal

Cualquier diferencia detiene el flujo.

9. Programación de Pago (CxP)

Se genera el documento por pagar y se agenda según días de crédito.
No se puede programar pago sin factura válida.

10. Conciliación Tripartita

OC vs Recepción

OC vs Factura

Factura vs CxP

Solo con estas tres coincidencias la compra puede cerrarse.

11. Cierre

La OC pasa a estado Cerrada cuando no quedan diferencias.

flowchart TD

T["Flujo 3 - NORMAL + CREDITO - OBRA"]

subgraph F3[" "]
direction TB

R1["1. Requisición<br/>Actor: Solicitante<br/>Estado: Pendiente"]

R2{"2. Validación Técnica<br/>Actor: Jefe de área<br/>¿Es crítica?"}

Rcrit["Se va al flujo crítico de Obra"]

R3["3. Cotizaciones<br/>&lt;= 5k: 1 cotización<br/>5-15k: 2 cotizaciones<br/>&gt; 15k: 3 cotizaciones + comparativo"]

R4{"4. Validación económica<br/>¿Es concepto presupuestado?"}

R4a["Si es concepto:<br/>PU real vs PU presupuestado<br/>+ saldo del concepto"]

R4b["Si NO es concepto:<br/>Autorización por montos<br/>&lt;=20k Jefe<br/>20-50k Director<br/>&gt;50k DG"]

R5["5. OC Normal<br/>Precio final definido"]

R6["6. Entrega del proveedor<br/>(crédito, sin pago previo)"]

R7["7. Recepción formal<br/>Validación de cantidad, calidad y concepto"]

R8["8. Factura<br/>Debe coincidir con OC y recepción"]

R9["9. Programación de pago (CxP)"]

R10["10. Conciliación tripartita<br/>OC vs Recepción vs Factura vs CxP"]

R11["11. Cierre de OC<br/>Solo con conciliación completa"]

end

T --> R1
R1 --> R2
R2 -->|No crítica| R3
R2 -->|Crítica| Rcrit
R3 --> R4
R4 -->|Es concepto| R4a
R4 -->|No es concepto| R4b
R4a --> R5
R4b --> R5
R5 --> R6
R6 --> R7
R7 --> R8
R8 --> R9
R9 --> R10
R10 --> R11
