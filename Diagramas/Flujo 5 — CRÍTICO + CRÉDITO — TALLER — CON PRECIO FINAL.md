# Flujo 5 — CRÍTICO + CRÉDITO — TALLER — CON PRECIO FINAL

Este flujo describe el proceso de compras cuando la requisición **es crítica**, pertenece a **Taller**, el pago es **crédito**, y **sí existe precio final desde el inicio**.  
Al existir precio final, el flujo crítico es **simplificado**: no se requiere definir precio final después, pero **la OC preliminar sigue siendo obligatoria**.

La compra solo se cierra cuando se cumple la **Conciliación Tripartita**:

- OC vs Recepción  
- OC vs Factura  
- Factura vs CxP (crédito)

A continuación se describe el proceso paso a paso:

---

### **1. Requisición**

El solicitante genera una requisición. Esta inicia en estado *Pendiente*.  
Debe incluir descripción, cantidades, especificaciones y motivo.

---

### **2. Validación técnica**

El Jefe de Área confirma necesidad, cantidades y especificaciones.  
Aquí se marca como **CRÍTICA**, lo que habilita:

- Uso obligatorio de **OC preliminar**  
- Posibilidad de avanzar con cotizaciones incompletas  
- Entrega anticipada  
- Autorización retroactiva por montos  
- **Recepción preliminar** (aunque haya precio final)

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
- **No permite facturación.**  
- Debe convertirse después en **OC normal**.

---

### **5. Entrega del proveedor**

El proveedor entrega materiales o servicio **sin pago previo** (crédito).  
La entrega anticipada es válida porque la compra está marcada como crítica.

---

### **6. Recepción PRELIMINAR**

Regla COMAQSA:

> Aunque exista precio final, **NO puede existir recepción formal mientras no exista OC normal**.  
> La OC preliminar **únicamente permite recepción preliminar**.

La recepción preliminar valida:

- Cantidad  
- Calidad  
- Coincidencia con la entrega y OC preliminar  

La recepción deberá formalizarse más adelante cuando exista la OC normal.

---

### **7. Completar cotizaciones o justificar excepción**

Si faltan cotizaciones:

- Se capturan ahora **o**  
- Se documenta excepción (urgencia, OEM, único proveedor, inventario inmediato)

Debe registrarse quién autorizó la excepción.

---

### **8. Autorización retroactiva por montos**

Aplica porque la compra es **crítica**.

Rangos Taller:

- ≤ 20k → Jefe de Área  
- 20–50k → Director  
- > 50k → Director General  

La autorización es directa porque el precio final ya existía desde el inicio.

---

### **9. Conversión a OC NORMAL**

La OC preliminar se convierte en **OC normal** cuando:

- Precio final ya estaba definido  
- Autorización retroactiva aprobada  
- Cotizaciones completas o justificadas  

---

### **10. Convertir recepción preliminar a recepción FORMAL**

Regla COMAQSA:

> La **recepción formal solo puede existir cuando ya existe OC normal**.

Acciones:

- Tomar la recepción preliminar registrada en el paso 6  
- Validar cantidad, calidad y correspondencia con la OC normal  
- Cambiar estado a **Recepción Formal**

---

### **11. Factura**

La factura debe coincidir con:

- OC normal  
- Recepción formal  

Cualquier diferencia detiene el flujo.

---

### **12. Programar pago (CxP)**

- Se genera Documento por Pagar (CxP)  
- Se agenda el pago conforme a los días de crédito pactados

---

### **13. Conciliación tripartita**

Se valida:

- OC vs Recepción formal  
- OC vs Factura  
- Factura vs CxP  

La OC solo se cierra con conciliación completa.

---

### **14. Cierre de la compra**

La compra se cierra cuando los tres documentos están totalmente conciliados.

---

```mermaid
flowchart TD

T["Flujo 5 - CRÍTICO + CRÉDITO - TALLER (CON PRECIO FINAL)"]

subgraph F5[" "]
direction TB

R1["1. Requisición  
Actor: Solicitante  
Estado: Pendiente"]

R2["2. Validación Técnica  
Se marca CRÍTICA"]

R3["3. Cotizaciones opcionales  
0–1 cotizaciones  
Justificación por urgencia"]

R4["4. OC Preliminar  
Obligatoria en crítico  
Precio final existente"]

R5["5. Entrega del proveedor  
Crédito  
Entrega sin pago"]

R6["6. Recepción PRELIMINAR  
Obligatoria mientras exista OC preliminar"]

R7["7. Completar cotizaciones  
o justificar excepción"]

R8["8. Autorización retroactiva  
<=20k Jefe área  
20–50k Director  
>50k DG"]

R9["9. Convertir a OC Normal  
Precio final ya existente"]

R10["10. Convertir recepción preliminar  
a recepción FORMAL"]

R11["11. Factura  
Debe coincidir con OC normal y recepción formal"]

R12["12. Programar pago (CxP)"]

R13["13. Conciliación tripartita  
OC vs Recepción  
OC vs Factura  
Factura vs CxP"]

R14["14. Cierre de la compra  
Solo con conciliación completa"]

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
