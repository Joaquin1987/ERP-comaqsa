# Flujo 1 — NORMAL + CRÉDITO — TALLER

Este flujo describe el proceso de compras cuando la requisición **no es crítica**, pertenece al **Taller**, y el método de pago es **crédito**.  
La característica principal es que **el pago ocurre después de la factura**, mediante **Cuenta por Pagar (CxP)**, pero **el pago NO cierra la compra**.

La compra solo se cierra cuando se cumple la **Conciliación Tripartita**:

- OC vs Recepción  
- OC vs Factura  
- Factura vs CxP  

A continuación se describe el proceso paso a paso:

### **1. Requisición**
El solicitante genera una requisición.  
Esta inicia en estado **Pendiente**.

### **2. Validación técnica**
El Jefe de Área revisa si la compra es crítica o no.  
Si fuera crítica, se envía al flujo correspondiente.  
Si no lo es, continúa el flujo normal.

### **3. Cotizaciones**
Según el monto de la requisición se requiere:  
- ≤ 5k → 1 cotización  
- 5–15k → 2 cotizaciones  
- > 15k → 3 cotizaciones  

### **4. Autorización por montos**
Dependiendo del monto total, la compra debe ser autorizada por:  
- ≤ 20k → Jefe de Área  
- 20–50k → Director  
- > 50k → Director General  

### **5. Orden de Compra (OC) Normal**
Se genera una OC **con precio final definido**.  
Es un documento formal.

### **6. Entrega del proveedor**
El proveedor entrega los materiales o el servicio según lo indicado en la OC.

### **7. Recepción formal**
Se valida cantidad y calidad contra la OC.  
La recepción debe coincidir con lo solicitado.

### **8. Factura**
El proveedor entrega la factura.  
La factura debe coincidir con lo recibido y con la OC.

### **9. Programación de pago (CxP)**
Se genera la **Cuenta por Pagar**, programando el pago según los días de crédito.  
El pago **NO cierra** la compra.

### **10. Conciliación tripartita**
Se verifica:
- OC vs Recepción  
- OC vs Factura  
- Factura vs CxP  

Sin esta conciliación, no puede cerrarse la compra.

### **11. Cierre de la compra**
La OC se cierra **solo** cuando todas las conciliaciones están completas.

---

## **Diagrama del flujo**

```mermaid
flowchart TD

T["Flujo 1 - NORMAL + CREDITO - TALLER"]

subgraph F1[" "]
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

R6["6. Entrega del proveedor"]

R7["7. Recepcion formal  
Validacion de cantidad y calidad"]

R8["8. Factura  
Debe coincidir con OC y recepcion"]

R9["9. Programacion de pago (CxP)  
Se genera CxP segun dias de credito"]

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
R4 --> R5
R5 --> R6
R6 --> R7
R7 --> R8
R8 --> R9
R9 --> R10
R10 --> R11
```
