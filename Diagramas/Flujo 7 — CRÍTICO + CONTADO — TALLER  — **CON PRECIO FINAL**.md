#7 FLUJO COMPLETO — CRÍTICO + CONTADO — TALLER — **CON PRECIO FINAL**

> **Este flujo sigue EXACTAMENTE el formato de los flujos #1–#6.**  
> Caso #7 del listado oficial: *Crítico + Contado – Taller – Con precio final*.  
> Como existe **precio final desde el inicio**, este flujo es **crítico simplificado** (no requiere paso de “definir precio final”).

---

## 1. REQUISICIÓN

**Actor:** Usuario solicitante  
**Estado:** Pendiente  

**Inputs:** descripción, cantidades, especificaciones, motivo.

**Reglas / Candados:**

* Requisición obligatoria para iniciar cualquier compra.

**Output:** Requisición creada.

---

## 2. VALIDACIÓN TÉCNICA (VT)

**Actor:** Jefe de área  
**Estado:** Requisición validada  

**Acciones:**

* Confirmar necesidad real.
* Revisar especificaciones.
* Ajustar cantidades si corresponde.

**Candado crítico:**

* Aquí se **marca como CRÍTICA**.
* El sistema registra: responsable, motivo y urgencia operativa.
* Al marcar crítica se habilita:

  * OC preliminar (aunque haya precio final)
  * Entrega antes de autorización
  * Pago anticipado
  * Autorización retroactiva

**Output:** Requisición validada y marcada como crítica.

---

## 3. COTIZACIONES (OPCIONALES POR URGENCIA)

**Estado:** En cotización  

**Reglas:**

* En compra crítica, **NO se exige completar cotizaciones** antes de avanzar.
* Puede haber **1 cotización o incluso ninguna**.
* Como **SÍ existe precio final**, esa cotización puede ser la definitiva.

**Output:** Cotización(es) cargadas o justificación de urgencia.

---

## 4. ORDEN DE COMPRA PRELIMINAR (OC PRELIMINAR)

**Estado:** OC preliminar emitida  

**Características:**

* Obligatoria en compra crítica incluso cuando sí hay precio.
* Permite separar mercancía o acelerar servicio.
* **No permite facturar.**
* Debe convertirse después en OC normal.

**Output:** OC preliminar generada.

---

## 5. PROVEEDOR EXIGE ANTICIPO / PAGO

**Estado:** Solicitud de pago  

**Reglas:**

* En crítico + contado, el proveedor normalmente exige anticipo o pago total **antes** de entregar.

**Output:** Exigencia de pago registrada.

---

## 6. PAGO ANTICIPADO O TOTAL

**Estado:** Pago registrado  

**Reglas:**

* Puede existir **pago sin conocer un precio estimado** en otros casos; pero aquí **sí existe precio final**, por lo que se paga con base en ese monto.
* **El pago NO cierra la compra.**

**Output:** Pago aplicado.

---

## 7. ENTREGA / SERVICIO

**Estado:** En recepción  

**Acciones:**

* Proveedor entrega bienes/servicios después del pago.

**Candado:**

* En contado **no hay entrega sin pago previo**.

**Output:** Entrega realizada.

---

## 8. RECEPCIÓN PRELIMINAR

**Estado:** Recepción preliminar registrada  

**Razones:**

* Aunque sí existe precio final, **todavía no existe OC normal** (solo OC preliminar).

**Reglas críticas:**

* La recepción preliminar es la única permitida mientras no exista OC normal.
* Se validan cantidades y conformidad básica, pero **no cierra ningún proceso**.

**Output:** Recepción preliminar registrada.

---

## 9. COMPLETAR COTIZACIONES O JUSTIFICAR EXCEPCIÓN

**Estado:** En validación documental  

**Reglas:**

* Si faltan cotizaciones, deben completarse.
* Si la urgencia lo justifica, se documenta la excepción (único proveedor, OEM, urgencia operativa, etc.).
* Se registra quién autorizó continuar sin todas las cotizaciones.

**Output:** Cotizaciones completas o excepción registrada.

---

## 10. AUTORIZACIÓN RETROACTIVA POR MONTOS

**Estado:** En autorización  

**Rangos Taller:**

* Hasta $20,000 → Jefe de Área  
* $20,001–$50,000 → Director de Área  
* Más de $50,000 → Director General  

**Reglas:**

* Aplica porque la compra es crítica.
* Como **sí existe precio final desde el inicio**, esta autorización es directa.

**Output:** Compra autorizada retroactivamente.

---

## 11. CONVERTIR A OC NORMAL

**Estado:** OC normal emitida  

**Condiciones:**

* Precio final registrado desde el inicio.
* Cotizaciones completas o justificadas.
* Autorización retroactiva aprobada.

**Output:** OC normal generada.

---

## 12. CONVERTIR RECEPCIÓN PRELIMINAR A RECEPCIÓN FORMAL

**Estado:** Recepción formal registrada  

**Acciones:**

* La recepción preliminar previa se valida ahora como **recepción formal**, pues ya existe OC normal y precio final.
* Se revisan cantidades, calidad y correspondencia.

**Output:** Recepción formal consolidada.

---

## 13. FACTURA

**Estado:** En espera de conciliación  

**Reglas:**

* Debe coincidir con:

  * OC normal
  * Recepción formal

* Diferencias detienen el flujo.

**Output:** Factura registrada.

---

## 14. PAGO COMPLEMENTARIO (SI APLICA)

**Estado:** Pago registrado  

**Reglas:**

* Como sí había precio final, normalmente **no hay diferencias**.
* Si existe ajuste posterior (caso excepcional), se registra pago complementario.

**Output:** Pago complementario registrado.

---

## 15. CONCILIACIÓN TRIPARTITA

**Estado:** En conciliación  

Debe coincidir:

* OC vs Recepción  
* OC vs Factura  
* Factura vs Pago (contado)  

**Candado maestro:**

* El pago **NO cierra** la compra.
* Solo la conciliación completa permite el cierre.

**Output:** Conciliación correcta.

---

## 16. CIERRE DE LA COMPRA

**Estado:** Cerrada  

La OC queda totalmente conciliada y sin pendientes.

**Output:** Compra cerrada y sin pendientes.

---

# RESUMEN ULTRA CLARO

1. Requisición  
2. Validación técnica (se marca crítica)  
3. Cotizaciones opcionales (ya existe precio final)  
4. OC preliminar (obligatoria en crítico)  
5. Proveedor exige anticipo/pago  
6. Pago anticipado o total (no cierra la compra)  
7. Entrega  
8. Recepción preliminar  
9. Completar cotizaciones o justificar excepción  
10. Autorización retroactiva por montos  
11. Convertir a OC normal  
12. Convertir recepción preliminar a recepción formal  
13. Factura  
14. Pago complementario (si aplica)  
15. Conciliación tripartita  
16. Cierre de la compra  

---

# DIAGRAMA MERMAID — FLUJO 7

```mermaid
flowchart TD

T["Flujo 7 - CRÍTICO + CONTADO - TALLER (CON PRECIO FINAL)"]

subgraph F7[" "]
direction TB

N1["1. Requisición  
Actor: Solicitante  
Estado: Pendiente"]

N2["2. Validación técnica (VT)  
Actor: Jefe de área  
Se marca CRÍTICA  
Habilita: OC preliminar, pago anticipado, entrega antes de autorización, autorización retroactiva"]

N3["3. Cotizaciones  
Opcionales por urgencia  
Puede haber 0 o 1  
Ya existe precio final"]

N4["4. OC PRELIMINAR  
Obligatoria en compra crítica  
Permite separar mercancía / servicio  
NO permite facturar"]

N5["5. Proveedor exige anticipo/pago  
Estado: Solicitud de pago"]

N6["6. Pago anticipado o total  
Estado: Pago registrado  
El pago NO cierra la compra"]

N7["7. Entrega / servicio  
Estado: En recepción  
En contado no hay entrega sin pago previo"]

N8["8. Recepción PRELIMINAR  
Solo permitida mientras exista OC preliminar  
Valida cantidades de forma básica  
NO cierra nada"]

N9["9. Completar cotizaciones / justificar excepción  
Estado: Validación documental"]

N10["10. Autorización RETROACTIVA por montos  
Rangos Taller:  
<= 20k: Jefe de área  
20k-50k: Director área  
> 50k: Director General"]

N11["11. Convertir a OC NORMAL  
Condiciones: precio final + cotizaciones completas/justificadas + autorización retroactiva"]

N12["12. Convertir recepción PRELIMINAR a FORMAL  
Ahora sí existe OC normal  
Recepción formal válida para conciliación"]

N13["13. Factura  
Debe coincidir con OC normal y recepción formal"]

N14["14. Pago complementario (si aplica)  
Solo si hay ajuste excepcional vs precio final"]

N15["15. Conciliación tripartita  
OC vs Recepción vs Factura vs Pago (contado)  
El pago NO cierra; solo la conciliación completa"]

N16["16. Cierre de la compra  
OC cerrada y sin pendientes"]
end

T --> N1
N1 --> N2
N2 --> N3
N3 --> N4
N4 --> N5
N5 --> N6
N6 --> N7
N7 --> N8
N8 --> N9
N9 --> N10
N10 --> N11
N11 --> N12
N12 --> N13
N13 --> N14
N14 --> N15
N15 --> N16
