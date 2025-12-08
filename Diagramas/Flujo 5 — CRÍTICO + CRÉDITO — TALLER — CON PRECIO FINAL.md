# Flujo 5 — CRÍTICO + CRÉDITO — TALLER — CON PRECIO FINAL

Este flujo describe el proceso de compras cuando la requisición **es crítica**, pertenece a **Taller**, el pago es **crédito**, y **sí existe precio final desde el inicio**.  
Al existir precio final, el flujo crítico es **simplificado**: no hay recepción preliminar ni paso para definir precio.  
Aun así, la **OC preliminar es obligatoria** en cualquier compra crítica.

La compra solo se cierra cuando se cumple la **Conciliación Tripartita**:

- OC vs Recepción  
- OC vs Factura  
- Factura vs CxP (crédito)

A continuación se describe el proceso paso a paso:

---

### **1. Requisición**

El solicitante genera una requisición. Esta inicia en estado *Pendiente*.  
Debe incluir motivo, cantidades y especificaciones.

---

### **2. Validación técnica**

El Jefe de Área confirma necesidad, cantidades y especificaciones.  
Aquí se marca como **CRÍTICA**, lo que habilita:

- OC preliminar obligatoria  
- Avanzar con 0–1 cotizaciones  
- Entrega anticipada  
- Autorización retroactiva por montos

---

### **3. Cotizaciones (opcional por urgencia)**

En compras críticas:

- No se exige completar cotizaciones al inicio.  
- Puede existir 1 o ninguna cotización.  
- Como ya hay **precio final**, la cotización disponible puede ser definitiva.  
- Cotizaciones faltantes se completan o justifican más adelante.

---

### **4. Orden de Compra PRELIMINAR**

Debe emitirse siempre en compras críticas, aun con precio final.

Características:

- Permite separar mercancía de inmediato.  
- No permite facturación.  
- Debe convertirse después en **OC normal**.

---

### **5. Entrega del proveedor**

El proveedor entrega materiales o servicio **sin pago previo**, ya que el flujo es **crédito**.  
La entrega anticipada es válida porque la compra está marcada como crítica.

---

### **6. Recepción formal**

Como existe **precio final desde el inicio**, NO se usa recepción preliminar.  
La recepción formal valida:

- Cantidad  
- Calidad  
- Coincidencia contra la OC preliminar + precio final

---

### **7. Completar cotizaciones o justificar excepción**

Si faltan cotizaciones:

- Se capturan ahora **o**  
- Se documenta excepción (urgencia, OEM, único proveedor con inventario, entrega inmediata).

Debe registrarse quién autorizó la excepción.

---

### **8. Autorización retroactiva por montos**

Aplica porque la compra es **crítica**.

Rangos Taller:

- ≤ 20k → Jefe de Área  
- 20–50k → Director  
- > 50k → Director General  

La autorización es directa porque ya existía precio final.

---

### **9. Conversión a OC NORMAL**

La OC preliminar se convierte en **OC normal** cuando:

- Precio final ya estaba definido  
- Cotizaciones completas o justificadas  
- Autorización retroactiva aprobada

---

### **10. Factura**

La factura debe coincidir con:

- OC normal  
- Recepción formal  

Cualquier diferencia detiene el flujo.

---

### **11. Conciliación tripartita**

Se valida:

- OC vs Recepción  
- OC vs Factura  
- Factura vs CxP  

La OC solo se cierra con conciliación completa.

---

```mermaid
flowchart TD

T["Flujo 5 - CRÍTICO + CRÉDITO - TALLER (CON PRECIO FINAL)"]

subgraph F5[" "]
direction TB

R1["1. Requisición  
Actor: Solicitante  
Estado: Pendiente"]

R2{"2. Validación Técnica  
Actor: Jefe de área  
¿Crítica?"}

R3["3. Cotizaciones (opcionales)  
0–1 cotizaciones  
Justificación por urgencia"]

R4["4. OC Preliminar  
Obligatoria en crítico  
Precio final existente"]

R5["5. Entrega del proveedor  
Crédito  
Entrega antes de autorización completa"]

R6["6. Recepción formal  
Validación cantidad y calidad"]

R7["7. Completar cotizaciones  
o justificar excepción"]

R8["8. Autorización retroactiva  
<=20k Jefe área  
20-50k Director  
>50k DG"]

R9["9. Convertir a OC Normal  
Precio final ya existente"]

R10["10. Factura  
Debe coincidir con OC y recepción"]

R11["11. Conciliación tripartita  
OC vs Recepción  
OC vs Factura  
Factura vs CxP"]

R12["Cierre de la compra  
Solo con conciliación completa"]

end

T --> R1
R1 --> R2
R2 -->|Crítica| R3
R3 --> R4
R4 --> R5
R5 --> R6
R6 --> R7
R7 --> R8
R8 --> R9
R9 --> R10
R10 --> R11
R11 --> R12
