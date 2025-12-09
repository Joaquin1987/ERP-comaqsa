# **#8 FLUJO COMPLETO — CRÍTICO + CONTADO — TALLER — SIN PRECIO FINAL**

> **Caso #8 del listado oficial:**  
> **Crítico + Contado – Taller – SIN precio final.**  
>  
> Como **NO existe precio final desde el inicio**, este flujo es el  
> **crítico completo**, con: OC preliminar obligatoria, anticipo estimado,  
> entrega urgente, recepción preliminar, definición posterior de precio,  
> autorización retroactiva, conversión a OC normal y conciliación tripartita.

---

## 1. REQUISICIÓN

**Actor:** Usuario solicitante  
**Estado del sistema:** Pendiente  

**Inputs:** descripción, cantidades, especificaciones, motivo.

**Reglas / Candados:**

- La requisición es obligatoria para iniciar cualquier compra.

**Output del sistema:** Requisición creada.

---

## 2. VALIDACIÓN TÉCNICA (VT)

**Actor:** Jefe de área  
**Estado del sistema:** Requisición validada  

**Acciones:**

- Confirmar necesidad real.  
- Revisar especificaciones.  
- Ajustar cantidades si corresponde.

**Candado crítico:**

- Aquí se **marca como CRÍTICA**.  
- El sistema registra: responsable, motivo y urgencia operativa.  
- Al marcar crítica se habilita:
  - OC preliminar  
  - Recepción preliminar  
  - Entrega antes de autorización completa  
  - Anticipos sin precio final  
  - Autorización retroactiva  

**Output del sistema:** Requisición validada técnicamente y marcada como crítica.

---

## 3. COTIZACIONES (OPCIONALES POR URGENCIA)

**Estado del sistema:** En cotización  

**Reglas:**

- En compra crítica, **NO se exige completar cotizaciones al inicio**.  
- Puede haber **1 cotización o incluso ninguna**.  
- Cotizaciones faltantes se completarán después o se justificarán.

**Output del sistema:** Cotizaciones cargadas o justificación de urgencia.

---

## 4. ORDEN DE COMPRA PRELIMINAR (OC PRELIMINAR)

**Estado del sistema:** OC preliminar emitida  

**Características:**

- Obligatoria en compra crítica.  
- **No existe precio final**, por eso **NO se puede emitir OC normal**.  
- Permite separar mercancía o solicitar servicio inmediato.  
- **No permite facturar**.

**Output del sistema:** OC preliminar generada.

---

## 5. ANTICIPO ESTIMADO (SOLICITUD + PAGO)

**Estado del sistema:** Solicitud de pago y pago registrado  

**Reglas:**

- En crítico + contado, el proveedor exige anticipo o pago total **antes de la entrega**.  
- Como **no existe precio final**, el anticipo se basa en un monto **estimado**.  
- El pago se registra contra la OC preliminar.  
- **El pago NO cierra la compra.**

**Output del sistema:** Pago anticipado estimado aplicado.

---

## 6. ENTREGA / SERVICIO

**Estado del sistema:** En recepción  

**Acciones:**

- El proveedor entrega bienes/servicios después del anticipo.

**Candado:**

- En contado **NO hay entrega sin pago previo** (aunque sea estimado).

**Output del sistema:** Entrega realizada.

---

## 7. RECEPCIÓN PRELIMINAR

**Estado del sistema:** Recepción preliminar registrada  

**Razones:**

- No existe precio final.  
- No existe OC normal.

**Reglas críticas:**

- La recepción preliminar **debe validarse en máximo 72 horas**.  
- Esta recepción **no es definitiva**.  
- Cuando se emita la OC normal, esta recepción **deberá convertirse en recepción formal**.

**Output del sistema:** Recepción preliminar concluida.

---

## 8. DEFINIR PRECIO FINAL

**Estado del sistema:** En ajuste de precio  

**Acciones:**

- El proveedor confirma el precio real final.  
- Se actualiza la OC preliminar con el precio final.

**Candados:**

- Sin precio final **no puede existir autorización retroactiva**.

**Output del sistema:** Precio final definido.

---

## 9. COMPLETAR COTIZACIONES O JUSTIFICAR EXCEPCIÓN

**Estado del sistema:** En validación documental  

**Reglas:**

- Para autorizar retroactivamente se deben completar cotizaciones mínimas **o** justificar por qué no fue posible:
  - Urgencia crítica  
  - Único proveedor con inventario  
  - OEM  
  - Riesgo operativo  

**Registro obligatorio:**

- Proveedor elegido  
- Motivo de excepción  
- Responsable que autorizó  

**Output del sistema:** Cotizaciones completas o excepción registrada.

---

## 10. AUTORIZACIÓN RETROACTIVA POR MONTOS (TALLER)

**Estado del sistema:** En autorización  

**Rangos Taller:**

- Hasta $20,000 → Jefe de Área  
- $20,001–$50,000 → Director de Área  
- Más de $50,000 → Director General  

**Reglas:**

- La compra es crítica y el precio final se conoció después, por eso la autorización ocurre aquí.  
- Se aplican los mismos rangos que en flujo normal, pero de forma **retroactiva**.

**Output del sistema:** Compra autorizada retroactivamente.

---

## 11. CONVERTIR A OC NORMAL

**Estado del sistema:** OC normal emitida  

**Condiciones:**

- Precio final definido.  
- Autorización retroactiva aprobada.  
- Cotizaciones completas o justificadas.

**Acciones automáticas del sistema:**

- La OC preliminar se convierte en **OC normal**.  
- La recepción preliminar asociada se **convierte automáticamente en recepción formal**:
  - Misma cantidad y artículos.  
  - Ya con precio final amarrado a la OC normal.  
- A partir de aquí, la **recepción formal** es la que se usa en conciliación.

**Output del sistema:** OC normal generada y recepción formal creada.

---

## 12. PAGO COMPLEMENTARIO (SI APLICA)

**Estado del sistema:** Pago registrado  

**Reglas:**

- Si el precio final es mayor al anticipo estimado, se genera un **pago complementario**.  
- Si el precio final resulta menor, el sistema registra saldo a favor o nota de crédito.  
- Todos los pagos (anticipo + complementarios) se asocian a la misma OC normal.

**Output del sistema:** Pago(s) complementarios aplicados.

---

## 13. FACTURA

**Estado del sistema:** En espera de conciliación  

**Reglas:**

- La factura debe coincidir con:
  - OC normal  
  - Recepción **formal** (antes preliminar)  
  - Precio final  
- Diferencias detienen el flujo hasta corregir o justificar.

**Output del sistema:** Factura registrada.

---

## 14. CONCILIACIÓN TRIPARTITA

**Estado del sistema:** En conciliación  

Debe coincidir estrictamente:

- **OC vs Recepción formal**  
- **OC vs Factura**  
- **Factura vs Pago** (anticipo + complementarios)

**Candado maestro:**

- Ni los pagos ni la recepción preliminar ni la recepción formal, por sí solos, cierran la compra.  
- **Solo la conciliación completa puede cerrarla.**

**Output del sistema:** Conciliación correcta.

---

## 15. CIERRE DE LA COMPRA

**Estado del sistema:** Cerrada  

**Condiciones:**

- Conciliación tripartita completada y sin diferencias pendientes.

**Output del sistema:** Compra cerrada y sin pendientes.

---

# RESUMEN DEL FLUJO (FORMATO ESTÁNDAR)

1. Requisición  
2. Validación técnica (se marca CRÍTICA)  
3. Cotizaciones opcionales por urgencia  
4. OC preliminar  
5. Anticipo estimado (solicitud + pago)  
6. Entrega  
7. Recepción preliminar  
8. Definir precio final  
9. Completar cotizaciones o justificar excepción  
10. Autorización retroactiva por montos  
11. Convertir a OC normal **y convertir recepción preliminar en recepción formal**  
12. Pago complementario (si aplica)  
13. Factura  
14. Conciliación tripartita  
15. Cierre de la compra  

---

# DIAGRAMA MERMAID (RENDERIZABLE EN GITHUB)

```mermaid
flowchart TD

F8["Flujo 8 - CRÍTICO + CONTADO - TALLER - SIN PRECIO FINAL"]

subgraph CRIT_CONT_TALLER_8[" "]
direction TB

N1["1. Requisición  
Actor: Solicitante  
Estado: Pendiente"]

N2["2. Validación Técnica  
Actor: Jefe de área  
Requisición marcada como CRÍTICA  
Se habilita:  
- OC preliminar  
- Recepción preliminar  
- Entrega antes de autorización  
- Anticipos sin precio final  
- Autorización retroactiva"]

N3["3. Cotizaciones opcionales  
(NO obligatorias al inicio)"]

N4["4. OC PRELIMINAR  
No hay precio final  
No se puede facturar"]

N5["5. Anticipo ESTIMADO  
Pago de contado basado en monto estimado  
Registrado contra OC preliminar  
El pago NO cierra la compra"]

N6["6. Entrega del proveedor  
Después del anticipo  
En contado no hay entrega sin pago"]

N7["7. Recepción PRELIMINAR  
No hay precio final ni OC normal  
Debe validarse en máximo 72 h  
No es definitiva"]

N8["8. Definir precio final  
Proveedor confirma monto real  
Se actualiza la OC preliminar"]

N9["9. Completar cotizaciones  
o registrar excepción  
(Urgencia, OEM, único proveedor, etc.)"]

N10["10. Autorización RETROACTIVA por montos  
Taller:  
<=20k Jefe área  
20-50k Director  
>50k Director General"]

N11["11. Convertir a OC NORMAL  
Convertir recepción PRELIMINAR  
en recepción FORMAL  
Recepción formal será la base de conciliación"]

N12["12. Pago complementario (si aplica)  
Si precio final > anticipo → pago extra  
Si precio final < anticipo → saldo a favor / nota de crédito"]

N13["13. Factura  
Debe coincidir con OC normal  
y recepción formal  
Diferencias detienen el flujo"]

N14["14. Conciliación tripartita  
OC vs Recepción formal  
OC vs Factura  
Factura vs Pago (anticipo + complementarios)"]

N15["15. Cierre de la compra  
Solo con conciliación completa  
Ni pago ni recepción cierran por sí solos"]

end

F8 --> N1
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
