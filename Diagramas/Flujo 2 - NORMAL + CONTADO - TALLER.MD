mermaid
flowchart TD

T["Flujo 2 - NORMAL + CONTADO - TALLER"]

subgraph F2[" "]
direction TB

R1["1. Requisicion  
Actor: Solicitante  
Estado: Pendiente"]

R2{"2. Validacion Tecnica  
Actor: Jefe de area  
Es critica?"}

Rcrit["Se va al flujo critico"]

R3["3. Cotizaciones  
<= 5k: 1 cotizacion  
5-15k: 2 cotizaciones  
> 15k: 3 cotizaciones"]

R4["4. Autorizacion por montos  
<= 20k: Jefe de area  
20-50k: Director  
> 50k: Director General"]

R5["5. OC Normal  
Precio final definido"]

R6["6. Pago de contado  
Ocurre antes de la entrega  
El pago NO cierra la compra"]

R7["7. Entrega del proveedor"]

R8["8. Recepcion formal  
Validacion de cantidad y calidad"]

R9["9. Factura  
Debe coincidir con OC y recepcion"]

R10["10. Conciliacion tripartita  
OC vs Recepcion vs Factura vs Pago"]

R11["11. Cierre de OC  
Solo con conciliacion completa"]

end

T --> R1
R1 --> R2
R2 -->|No critica| R3
R2 -->|Critica| Rcrit
R3 --> R4
R4 --> R5
R5 --> R6
R6 --> R7
R7 --> R8
R8 --> R9
R9 --> R10
R10 --> R11
