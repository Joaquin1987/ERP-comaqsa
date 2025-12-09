# **FLUJO #8 — CRÍTICO + CONTADO — TALLER — *CON PRECIO FINAL***  
*(Formato oficial para GitHub — siguiendo exactamente el estilo del Flujo #7)*

> **Caso #8 del listado oficial:**  
> **Crítico + Contado – Taller – *Con precio final***  
> Como **sí existe precio final desde el inicio**, este flujo es **crítico simplificado**,  
> pero **NO elimina** el uso obligatorio de **OC preliminar**, **pago anticipado**,  
> **recepción preliminar**, y **autorización retroactiva**, según reglas COMAQSA.

---

# 1. REQUISICIÓN

**Actor:** Usuario solicitante  
**Estado:** Pendiente  

**Inputs:** descripción, cantidades, especificaciones, motivo.

**Reglas / Candados:**

- La requisición es obligatoria para iniciar cualquier compra.

**Output:** Requisición creada.

---

# 2. VALIDACIÓN TÉCNICA (VT)

**Actor:** Jefe de área  
**Estado:** Requisición validada  

**Acciones:**

- Confirmar necesidad real.  
- Revisar especificaciones.  
- Ajustar cantidades si corresponde.

**Candado crítico:**

- Aquí se **marca como CRÍTICA**.
- El sistema registra: responsable, motivo, urgencia operativa.
- Al marcar crítica se habilita:
  - Uso de **OC preliminar** (obligatoria),
  - **Pago anticipado**,
  - **Entrega antes de autorización completa**,
  - **Autorización retroactiva por montos**.

**Output:** Requisición validada y marcada como crítica.

---

# 3. COTIZACIONES (OPCIONALES POR URGENCIA)

**Estado:** En cotización  

**Reglas:**

- En compra crítica, **NO se exige completar cotizaciones antes de avanzar**.  
- Puede haber **1 cotización o incluso ninguna**.  
- Como **sí existe precio final**, esa cotización puede ser la definitiva.  

**Output:** Cotización(es) cargadas o justificación de urgencia.

---

# 4. ORDEN DE COMPRA PRELIMINAR (OC PRELIMINAR)

**Estado:** OC preliminar emitida  

**Características:**

- Obligatoria en compra crítica incluso con precio final.  
- Permite separar mercancía o solicitar servicio inmediato.  
- **No permite facturar.**  
- **Debe convertirse posteriormente a OC normal.**

**Output:** OC preliminar generada.

---

# 5. PROVEEDOR EXIGE ANTICIPO / PAGO (CONTADO)

**Estado:** Solicitud de pago  

**Reglas:**

- En crítico + contado, el proveedor normalmente exige anticipo o el pago completo **antes de la entrega**.
- Como **sí existe precio final**, el pago se basa en ese monto.

**Output:** Exigencia de pago registrada.

---

# 6. PAGO ANTICIPADO O TOTAL

**Estado:** Pago registrado  

**Reglas:**

- El pago ocurre **antes de la entrega**.  
- Puede ser total o anticipo.  
- **El pago NO cierra la compra.**

**Output:** Pago aplicado.

---

# 7. ENTREGA / SERVICIO

**Estado:** En recepción  

**Acciones:**

- El proveedor entrega bienes o realiza el servicio **después del pago**.

**Candado:**

- En contado **NO puede haber entrega sin pago previo**.

**Output:** Entrega realizada.

---

# 8. RECEPCIÓN PRELIMINAR

**Estado:** Recepción preliminar registrada  

**Razón absoluta:**

> **Mientras exista solo OC preliminar, NO puede haber recepción formal**,  
> incluso si sí existe precio final.

**Reglas:**

- La recepción debe ser **preliminar**, no formal.  
- Debe validarse en máximo **72 horas**.  

**Output:** Recepción preliminar concluida.

---

# 9. COMPLETAR COTIZACIONES O JUSTIFICAR EXCEPCIÓN

**Estado:** Validación documental  

**Reglas:**

- Si faltan cotizaciones, deben completarse.  
- Si la urgencia lo justifica, se documenta excepción por:
  - único proveedor,  
  - OEM,  
  - inventario inmediato,  
  - urgencia crítica.  

**Registros obligatorios:**

- Proveedor elegido  
- Motivo de excepción  
- Responsable que autorizó  

**Output:** Cotizaciones completas o excepción registrada.

---

# 10. AUTORIZACIÓN RETROACTIVA POR MONTOS (TALLER)

**Estado:** En autorización  

**Rangos Taller:**

- Hasta $20,000 → Jefe de Área  
- $20,001–$50,000 → Director de Área  
- Más de $50,000 → Director General  

**Reglas:**

- Aplica porque la compra es crítica.  
- Como **sí existe precio final desde el inicio**, esta autorización es directa.

**Output:** Compra autorizada retroactivamente.

---

# 11. CONVERTIR A OC NORMAL

**Estado:** OC normal emitida  

**Condiciones:**

- Precio final ya existía.  
- Autorización retroactiva completa.  
- Cotizaciones completas o justificadas.

**Output:** OC normal generada.

---

# 12. CONVERTIR RECEPCIÓN PRELIMINAR A RECEPCIÓN FORMAL

**Estado:** Recepción formal registrada  

**Acciones:**

- El sistema convierte la recepción preliminar en **recepción formal**,  
  ahora sí validable para conciliación.  

**Condiciones:**

- Ya existe OC normal.  
- Ya existe precio final.  

**Output:** Recepción formal concluida.

---

# 13. FACTURA

**Estado:** En espera de conciliación  

**Reglas:**

- Debe coincidir exactamente con:
  - OC normal,  
  - Recepción formal.  

- Diferencias detienen el flujo hasta corregir.

**Output:** Factura aceptada.

---

# 14. CONCILIACIÓN TRIPARTITA

**Estado:** En conciliación  

Debe coincidir estrictamente:

1. **OC vs Recepción formal**  
2. **OC vs Factura**  
3. **Factura vs Pago (contado)**  

**Candado maestro:**  
> **El flujo NO cierra por pagar.  
> Solo cierra cuando la conciliación está completa.**

**Output:** Compra totalmente conciliada.

---

# 15. CIERRE DE LA OC

**Estado:** Cerrada  

**Reglas:**

- Una compra crítica + contado **solo cierra cuando las 3 conciliaciones coinciden**.  
- No puede cerrarse por el pago ni por la entrega.

**Output:** OC cerrada correctamente.

---

---

# **DIAGRAMA MERMAID (FUNCIONAL PARA GITHUB)**

```mermaid
flowchart TD

A1["1. Requisición  
Estado: Pendiente"]

A2{"2. Validación Técnica  
¿Se marca CRÍTICA?"}

A3["Requisición marcada como CRÍTICA"]

A4["3. Cotizaciones (opcionales por urgencia)"]

A5["4. OC Preliminar  
(Obligatoria en compra crítica)"]

A6["5. Proveedor exige anticipo/pago"]

A7["6. Pago anticipado o total  
(No cierra la compra)"]

A8["7. Entrega del proveedor  
(Contado → no hay entrega sin pago)"]

A9["8. Recepción PRELIMINAR  
(No puede haber recepción formal sin OC normal)"]

A10["9. Completar cotizaciones  
o justificar excepción"]

A11["10. Autorización retroactiva por montos  
Taller: 20k / 50k / DG"]

A12["11. Convertir a OC Normal"]

A13["12. Convertir recepción preliminar  
a recepción FORMAL"]

A14["13. Factura  
Debe coincidir con OC y recepción"]

A15["14. Conciliación tripartita  
OC vs Recepción vs Factura vs Pago"]

A16["15. Cierre de OC  
(Únicamente con conciliación completa)"]

A1 --> A2
A2 -->|Sí, es crítica| A3
A3 --> A4
A4 --> A5
A5 --> A6
A6 --> A7
A7 --> A8
A8 --> A9
A9 --> A10
A10 --> A11
A11 --> A12
A12 --> A13
A13 --> A14
A14 --> A15
A15 --> A16

A2 -->|No crítica| NORM["Se va al flujo Normal + Contado (Taller)"]
