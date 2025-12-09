# **#8 FLUJO COMPLETO — CRÍTICO + CONTADO — TALLER — SIN PRECIO FINAL**  
*(Documento oficial COMAQSA — Formato GitHub — Basado estrictamente en el archivo #8)* :contentReference[oaicite:0]{index=0}

> **Caso #8 del listado maestro**  
> **Crítico + Contado — Taller — SIN precio final**  
>  
> Como **NO existe precio final desde el inicio**, este flujo es un **flujo crítico completo**, con:  
> - OC preliminar obligatoria  
> - Anticipo/pago estimado  
> - Entrega anticipada  
> - Recepción preliminar  
> - Definición posterior del precio final  
> - Autorización retroactiva por montos  
> - Conversión a OC normal  
> - Conversión de recepción preliminar a formal  
> - Conciliación tripartita obligatoria  
> - Cierre solo con conciliación completa  

---

# **1. REQUISICIÓN**

**Actor:** Usuario solicitante  
**Estado:** Pendiente  

**Inputs:** descripción, cantidades, especificaciones, motivo.  

**Reglas / Candados:**

- La requisición es obligatoria para iniciar cualquier compra.

**Output:** Requisición creada.

---

# **2. VALIDACIÓN TÉCNICA (VT)**

**Actor:** Jefe de área  
**Estado:** Requisición validada  

**Acciones:**  
- Confirmar necesidad real  
- Revisar especificaciones  
- Ajustar cantidades si corresponde  

**Candado crítico:**  
- Aquí se **marca como CRÍTICA**.  
- El sistema registra:  
  - Responsable  
  - Motivo  
  - Urgencia operativa  
- Al marcar crítica se habilitan:  
  - **OC preliminar**  
  - **Anticipos sin precio final**  
  - **Recepción preliminar**  
  - **Entrega antes de autorización**  
  - **Autorización retroactiva por montos**

**Output:** Requisición validada y marcada como crítica.

---

# **3. COTIZACIONES (OPCIONALES POR URGENCIA)**

**Estado:** En cotización  

**Reglas:**  
- En compra crítica **NO se exige completar cotizaciones al inicio**.  
- Puede existir una cotización o incluso ninguna.  
- Las cotizaciones faltantes se completarán después o se justificarán.

**Output:** Cotizaciones cargadas o justificación de urgencia.

---

# **4. ORDEN DE COMPRA PRELIMINAR (OC PRELIMINAR)**

**Estado:** OC preliminar emitida  

**Características:**  
- Obligatoria en compra crítica.  
- **No existe precio final**, por lo cual **NO puede generarse OC normal** todavía.  
- Permite separar mercancía o solicitar servicio inmediato.  
- **No permite facturar.**

**Output:** OC preliminar generada.

---

# **5. ANTICIPO ESTIMADO (SOLICITUD + PAGO)**

**Estado:** Solicitud de pago y pago registrado  

**Reglas:**  
- En crítico + contado, el proveedor exige anticipo antes de la entrega.  
- Como **NO existe precio final**, el pago se basa en **monto estimado**.  
- El pago anticipado **NO cierra la compra**.

**Output:** Pago anticipado aplicado.

---

# **6. ENTREGA / SERVICIO**

**Estado:** En recepción  

**Acciones:**  
- El proveedor entrega bienes/servicios **después del anticipo**.

**Candado:**  
- En contado **NO hay entrega sin pago previo**.

**Output:** Entrega realizada.

---

# **7. RECEPCIÓN PRELIMINAR**

**Estado:** Recepción preliminar registrada  

**Razones:**  
- NO existe precio final.  
- NO existe OC normal.  

**Reglas críticas:**  
- La recepción preliminar **debe validarse dentro de 72 horas**.  
- Será convertida a **recepción formal** cuando se genere la OC normal.

**Output:** Recepción preliminar concluida.

---

# **8. DEFINIR PRECIO FINAL**

**Estado:** En ajuste de precio  

**Acciones:**  
- El proveedor confirma el **precio final real**.  
- Se actualiza la OC preliminar con ese monto.

**Candado clave:**  
> **Sin precio final NO puede existir autorización retroactiva.**

**Output:** Precio final definido.

---

# **9. COMPLETAR COTIZACIONES O JUSTIFICAR EXCEPCIÓN**

**Estado:** Validación documental  

**Reglas:**  
Para autorizar retroactivamente se deben:  
- Completar cotizaciones mínimas **o**  
- Registrar justificación de excepción:  
  - Urgencia crítica  
  - Único proveedor  
  - OEM  
  - Inventario inmediato  
  - Riesgo operativo  

**Registros obligatorios:**  
- Proveedor elegido  
- Motivo de excepción  
- Responsable que autorizó  

**Output:** Cotizaciones completas o excepción registrada.

---

# **10. AUTORIZACIÓN RETROACTIVA POR MONTOS (TALLER)**

**Estado:** En autorización  

**Rangos TALLER:**  
- Hasta $20,000 → Jefe de Área  
- $20,001–$50,000 → Director de Área  
- Más de $50,000 → Director General  

**Reglas:**  
- La compra es crítica.  
- El precio final se conoció después, por lo que la autorización ocurre aquí.

**Output:** Compra autorizada retroactivamente.

---

# **11. CONVERTIR A OC NORMAL**

**Estado:** OC normal emitida  

**Condiciones:**  
- Precio final definido  
- Autorización retroactiva aprobada  
- Cotizaciones completas o justificadas  

**Acciones automáticas:**  
- Se emite la OC normal definitiva.

**Output:** OC normal generada.

---

# **12. CONVERTIR RECEPCIÓN PRELIMINAR A RECEPCIÓN FORMAL**

**Estado:** Recepción formal registrada  

**Acción del ERP:**  
- La recepción preliminar se **convierte automáticamente en recepción formal**  
  al existir OC normal y precio final.

**Output:** Recepción formal concluida.

---

# **13. FACTURA**

**Estado:** En espera de conciliación  

**Reglas:**  
- La factura debe coincidir con:  
  - OC normal  
  - Recepción formal  
- Cualquier diferencia detiene el flujo.

**Output:** Factura aceptada.

---

# **14. CONCILIACIÓN TRIPARTITA**

**Estado:** En conciliación  

Debe coincidir exactamente:  
1. **OC vs Recepción formal**  
2. **OC vs Factura**  
3. **Factura vs Pago (contado)**  

**Candado maestro:**  
> **El pago NO cierra la compra.  
> Solo la conciliación completa cierra la OC.**

**Output:** Conciliación completada.

---

# **15. CIERRE DE LA OC**

**Estado:** Cerrada  

**Reglas:**  
- El flujo solo cierra con conciliación tripartita.  
- No puede cerrarse por pago, entrega o factura aislados.

**Output:** OC cerrada correctamente.

---

# **DIAGRAMA MERMAID (FUNCIONAL PARA GITHUB)**

```mermaid
flowchart TD

A1["1. Requisición  
Estado: Pendiente"]

A2{"2. Validación Técnica  
¿Se marca CRÍTICA?"}

A3["Requisición marcada como CRÍTICA"]

A4["3. Cotizaciones opcionales  
(Urgencia crítica)"]

A5["4. OC PRELIMINAR  
No existe precio final"]

A6["5. Anticipo estimado  
(Sin precio final)"]

A7["6. Entrega del proveedor  
(Contado → no entrega sin pago)"]

A8["7. Recepción PRELIMINAR  
Debe validarse en 72 h"]

A9["8. Definir precio final"]

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
Solo con conciliación completa"]

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
