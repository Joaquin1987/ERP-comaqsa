Flujo 6 — CRÍTICO + CRÉDITO — TALLER — SIN PRECIO FINAL

Este flujo describe el proceso de compras cuando la requisición es crítica, pertenece al Taller, el método de pago es crédito y no existe precio final al inicio.
Los elementos clave de este flujo son:

Se puede avanzar sin precio final y con cotizaciones incompletas.

Se usa OC preliminar (obligatoria en compras críticas).

El proveedor puede entregar sin pago y sin autorización completa.

Primero hay recepción preliminar, después recepción formal.

La autorización por montos es retroactiva, una vez conocido el precio final.

La compra solo se cierra cuando se cumple la Conciliación Tripartita:

OC vs Recepción

OC vs Factura

Factura vs CxP

A continuación se describe el proceso paso a paso:

1. Requisición

El solicitante genera una requisición con descripción, cantidades, especificaciones y motivo.
La requisición inicia en estado Pendiente y es obligatoria para cualquier compra.

2. Validación técnica (se marca CRÍTICA)

El Jefe de Área revisa la necesidad, especificaciones y cantidades.
En este punto la compra se marca como CRÍTICA y el sistema registra:

Responsable que marcó crítica.

Motivo y urgencia operativa.

Al marcarla crítica se habilita el uso de OC preliminar, recepción preliminar, entrega sin autorización completa y autorización retroactiva.

3. Cotizaciones (opcionales por urgencia)

Al ser una compra crítica, el sistema no exige completar cotizaciones al inicio.

Puede haber:

0 cotizaciones (solo urgencia justificada).

1 cotización.

O más, si dio tiempo de cotizar.

Las cotizaciones faltantes se completarán después o se justificarán formalmente.

4. Orden de Compra (OC) preliminar

Se genera una OC preliminar, porque no existe precio final todavía, por lo que no puede emitirse una OC normal.

La OC preliminar:

Es obligatoria en compras críticas.

Permite separar mercancía o solicitar servicio inmediato.

No permite facturar ni cerrar la compra.

5. Entrega sin pago (crédito)

El proveedor entrega los bienes o realiza el servicio sin haber recibido pago, porque la compra es a crédito.

Esto solo se permite por ser compra crítica: la prioridad es resolver la urgencia operativa.

6. Recepción preliminar

Se registra una recepción preliminar, ligada a la OC preliminar.

Sucede porque:

Aún no existe precio final.

Aún no existe OC normal.

La recepción preliminar debe validarse en un máximo de 72 horas y no sirve para conciliación hasta que se vuelva formal.

7. Definir precio final

Una vez realizado el servicio o entregado el material, el proveedor confirma el precio final real.

Con ese dato:

Se actualiza la OC preliminar con el precio final.

Se cierra la etapa de “monto estimado”.

Sin precio final no puede existir autorización retroactiva por montos.

8. Completar cotizaciones o justificar excepción

Antes de autorizar retroactivamente, el área de compras completa las cotizaciones mínimas o documenta la excepción.

Opciones:

Completar las cotizaciones según rangos normales.

O justificar por qué no fue posible obtenerlas (urgencia crítica, único proveedor disponible, OEM, inventario inmediato, riesgo operativo, etc.).

Se debe registrar:

Proveedor elegido.

Motivo de la excepción.

Responsable que autorizó continuar con esa excepción.

9. Autorización retroactiva por montos

Ya con el precio final definido y cotizaciones/comparativos listos (o excepciones documentadas), se aplica la autorización por montos de forma retroactiva.

Rangos Taller:

≤ 20k → Jefe de Área.

20–50k → Director de Área.

50k → Director General.

Esta autorización se hace aquí porque la compra avanzó por urgencia y el monto real solo se conoció después.

10. Conversión a OC normal

Con el precio final, cotizaciones (o excepciones) y autorización retroactiva aprobada, la OC preliminar se convierte en OC normal.

A partir de ahora:

La OC normal es el documento contractual definitivo.

Cualquier cambio de precio requeriría nueva autorización.

11. Recepción formal

Una vez que ya existe OC normal y precio final, la recepción puede ser formal.

El sistema:

Toma la recepción preliminar existente.

La vincula a la OC normal.

Cambia su estado de preliminar a formal, conservando cantidades y detalles técnicos.

Solo esta recepción formal sirve para la conciliación tripartita.

12. Factura

El proveedor emite la factura con base en el precio final y lo efectivamente recibido.

La factura debe coincidir con:

La OC normal.

La recepción formal.

Si hay diferencias, el flujo se detiene hasta corregir o justificar.

13. Programar pago (CxP)

Con la factura validada, se genera el documento por pagar (CxP) según las condiciones de crédito pactadas.

Reglas:

Sin factura válida no existe CxP.

La CxP se programa en el calendario de pagos.

14. Conciliación tripartita

Antes de cerrar la compra, el sistema realiza la conciliación tripartita:

OC vs Recepción (ya formal).

OC vs Factura.

Factura vs CxP.

Candado maestro:
Ni la recepción preliminar, ni la OC, ni la programación de pago cierran la compra.
Solo la conciliación completa permite el cierre.

15. Cierre de la compra

Una vez que la conciliación tripartita es correcta, la OC se marca como Cerrada.

La compra queda sin pendientes:

Sin diferencias de cantidades.

Sin diferencias de precio.

Sin saldos abiertos de CxP asociados a esa OC.

Diagrama del flujo
flowchart TD

T["Flujo 6 - CRITICO + CREDITO - TALLER - SIN PRECIO FINAL"]

subgraph F6[" "]
direction TB

R1["1. Requisicion  
Actor: Solicitante  
Estado: Pendiente"]

R2["2. Validacion Tecnica  
Actor: Jefe de area  
Se marca CRITICA"]

R3["3. Cotizaciones (opcionales)  
En compra critica no son obligatorias  
Pueden ser 0, 1 o mas"]

R4["4. OC Preliminar  
No existe precio final  
No permite facturar"]

R5["5. Entrega sin pago  
Credito: proveedor entrega  
antes de recibir pago"]

R6["6. Recepcion preliminar  
No hay precio final ni OC normal  
Debe validarse < 72 horas"]

R7["7. Definir precio final  
Proveedor confirma monto real  
Se actualiza la OC preliminar"]

R8["8. Completar cotizaciones  
o justificar excepcion  
(urgencia, OEM, unico proveedor, etc.)"]

R9["9. Autorizacion retroactiva por montos  
<= 20k: Jefe de area  
20-50k: Director  
> 50k: Director General"]

R10["10. Convertir a OC Normal  
Precio final definido  
OC preliminar se sustituye"]

R11["11. Recepcion formal  
Se convierte la recepcion  
preliminar en formal"]

R12["12. Factura  
Debe coincidir con  
OC normal y recepcion formal"]

R13["13. Programar pago (CxP)  
Documento por pagar generado  
No existe CxP sin factura valida"]

R14["14. Conciliacion tripartita  
OC vs Recepcion  
OC vs Factura  
Factura vs CxP"]

R15["15. Cierre de OC  
Solo con conciliacion completa"]

end

T --> R1
R1 --> R2
R2 --> R3
R3 --> R4
R4 --> R5
R5 --> R6
R6 --> R7
R7 --> R8
R8 --> R9
R9 --> R10
R10 --> R11
R11 --> R12
R12 --> R13
R13 --> R14
R14 --> R15
