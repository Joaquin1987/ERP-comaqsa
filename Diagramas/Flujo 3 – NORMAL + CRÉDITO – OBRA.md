✅ Flujo 3 — NORMAL + CRÉDITO — OBRA

(Documento generado con el mismo estilo y estructura del archivo que subiste)

Este flujo describe el proceso de compras cuando la requisición no es crítica, pertenece a Obra, y el método de pago es crédito.

El elemento clave de este flujo es que NO hay pago antes de la entrega, y que en Obra la validación económica depende del concepto presupuestado, su PU y su saldo disponible, salvo cuando la compra NO corresponde a un concepto.

La compra solo se cierra cuando se completa la Conciliación Tripartita:

OC vs Recepción

OC vs Factura

Factura vs CxP (programación de pago)

1. Requisición

Actor: Solicitante
Estado: Pendiente

La requisición debe indicar:

descripción,

cantidades,

especificaciones,

si corresponde a un concepto presupuestado,

motivo de la solicitud.

2. Validación técnica

Actor: Jefe de área**
Estado: Requisición validada

Acciones:

confirmar necesidad,

validar especificaciones,

ajustar cantidades,

confirmar si aplica a concepto presupuestado.

Candado importante:

Si se marca como crítica → se abandona este flujo y se pasa al flujo crítico de Obra.

3. Cotizaciones según monto

Reglas generales:

≤ 5k → 1 cotización

5–15k → 2 cotizaciones

15k → 3 cotizaciones + comparativo

4. Validación económica (Obra)

Aquí se determina si la compra corresponde o no a un concepto presupuestado, lo cual cambia completamente la autorización:

4.1 Si SÍ es concepto presupuestado

Validaciones:

PU real ≤ PU presupuestado

Saldo del concepto suficiente

Resultado:

Si PU y saldo son correctos → autorización automática del sistema

Si PU > PU presupuestado → requiere autorización del área de obra

Si saldo insuficiente → autorización de sobreejercicio (20k / 50k / DG)

4.2 Si NO es concepto presupuestado

Se aplican los rangos de Taller:

≤ 20k → Jefe de Área

20–50k → Director

50k → Director General

5. Orden de Compra (OC) Normal

Se genera una OC normal con precio final definido.

Candados:

No puede emitirse sin validación económica previa (PU+saldo o rangos).

6. Entrega del proveedor

El proveedor entrega materiales o ejecuta el servicio posterior a la OC normal.

Candados:

En crédito no existe pago previo, por lo tanto la entrega es posterior a la OC.

7. Recepción formal

Se valida:

cantidades,

calidad,

correspondencia exacta con la OC,

correspondencia con el concepto (si aplica).

8. Factura

Debe coincidir con:

la OC,

la recepción,

el precio unitario presupuestado (si aplica).

Cualquier diferencia detiene el flujo hasta corregirla.

9. Programación de pago (CxP)

Acciones:

se genera el documento por pagar,

se integra al calendario según días de crédito.

Candado:

no se genera CxP sin factura válida.

10. Conciliación tripartita

Se debe verificar estrictamente:

OC vs Recepción

OC vs Factura

Factura vs CxP

Sin esta conciliación, no puede cerrarse la compra.

11. Cierre de la compra

La compra se cierra únicamente cuando la conciliación está completa.

Diagrama del flujo (idéntico estilo al que subiste)
flowchart TD

T["Flujo 3 - NORMAL + CREDITO - OBRA"]

subgraph F3[" "]
direction TB

R1["1. Requisicion  
Actor: Solicitante  
Estado: Pendiente"]

R2{"2. Validacion Tecnica  
Actor: Jefe de area  
¿Es critica?"}

Rcrit["Se va al flujo critico de Obra"]

R3["3. Cotizaciones  
<= 5k: 1 cotizacion  
5-15k: 2 cotizaciones  
> 15k: 3 cotizaciones"]

R4{"4. Validacion economica  
¿Es concepto presupuestado?"}

R4a["Si es concepto:  
PU <= PU presupuestado  
Saldo suficiente → Aprobacion automatica  
PU > PU presupuestado → Autorizacion area Obra  
Saldo insuficiente → Sobreejercicio"]

R4b["Si NO es concepto:  
<= 20k: Jefe de area  
20-50k: Director  
> 50k: Director General"]

R5["5. OC Normal  
Precio final definido"]

R6["6. Entrega del proveedor"]

R7["7. Recepcion formal  
Validacion de cantidad, calidad y concepto"]

R8["8. Factura  
Debe coincidir con OC y recepcion"]

R9["9. Programacion de pago (CxP)"]

R10["10. Conciliacion tripartita  
OC vs Recepcion vs Factura vs CxP"]

R11["11. Cierre de OC  
Solo con conciliacion completa"]

end

T --> R1
R1 --> R2
R2 -->|No critica| R3
R2 -->|Critica| Rcrit
R3 --> R4
R4 -->|Concepto| R4a
R4 -->|No concepto| R4b
R4a --> R5
R4b --> R5
R5 --> R6
R6 --> R7
R7 --> R8
R8 --> R9
R9 --> R10
R10 --> R11
