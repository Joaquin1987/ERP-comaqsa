# Flujo 3 — NORMAL + CRÉDITO — OBRA

Este flujo describe el proceso de compras cuando la requisición **no es crítica**, pertenece a **Obra**, y el método de pago es **crédito**.  
El punto clave es que en Obra la validación económica depende de si la compra corresponde a un **concepto presupuestado** o no.  
La compra solo se cierra cuando se cumple la **Conciliación Tripartita**:

- OC vs Recepción  
- OC vs Factura  
- Factura vs CxP  

A continuación se describe el proceso paso a paso:

### **1. Requisición**  
El solicitante genera una requisición. Esta inicia en estado *Pendiente*.  
Debe indicar si corresponde a un **concepto presupuestado** de Obra.

### **2. Validación técnica**  
El Jefe de Área revisa si la compra es crítica o no y valida cantidades y especificaciones.  
Si se marca como **crítica**, el flujo abandona este proceso.

### **3. Cotizaciones**  
Según el monto:  
- ≤ 5k → 1 cotización  
- 5–15k → 2 cotizaciones  
- > 15k → 3 cotizaciones + comparativo  

### **4. Validación económica (Obra)**  

#### **Si SÍ es concepto presupuestado:**  
Validaciones:  
- PU real ≤ PU presupuestado  
- Saldo suficiente  

Resultados:  
- PU y saldo correctos → **Autorización automática**  
- PU > PU presupuestado → Autorización del área de obra  
- Saldo insuficiente → Sobreejercicio (20k / 50k / DG)

#### **Si NO es concepto presupuestado:**  
Aplican rangos de Taller:  
- ≤ 20k → Jefe de Área  
- 20–50k → Director  
- > 50k → Director General  

### **5. Orden de Compra (OC) Normal**  
Se genera una OC **con precio final definido**.  
Debe existir validación económica previa (PU+saldo o rangos).

### **6. Entrega del proveedor**  
El proveedor entrega bienes o servicios **después de la OC normal**.  
En crédito no existe pago previo.

### **7. Recepción formal**  
Se valida cantidad y calidad contra la OC y, si aplica, contra el concepto.

### **8. Factura**  
La factura debe coincidir con la OC y la recepción.  
Cualquier diferencia detiene el proceso.

### **9. Programación de pago (CxP)**  
Se genera el documento por pagar basado en la factura validada.  
Se programa según el crédito pactado.

### **10. Conciliación tripartita**  
Se verifica:  
- OC vs Recepción  
- OC vs Factura  
- Factura vs CxP  

Sin estas coincidencias no puede cerrarse la compra.

### **11. Cierre de la compra**  
La compra se cierra solo cuando la conciliación está completa.

---

## **Diagrama del flujo**

```mermaid
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

