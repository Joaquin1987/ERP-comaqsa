# COMAQSA – Módulo de Compras (ERP)
**Documento Oficial del Flujo de Compras — Integrado para Taller y Obra**

Este documento define **toda la lógica operativa y técnica** del Módulo de Compras del ERP COMAQSA, incluyendo:

- Verdades absolutas del sistema  
- Tipos de OC y recepciones  
- Cotizaciones y autorizaciones  
- Flujos normales y críticos  
- Variantes por Taller y Obra  
- Regla de cierre por conciliación tripartita  
- Los **8 flujos maestros completos**, con todas sus ramificaciones  

---

# 1. Principio Rector del Sistema

## 🚦 Conciliación Tripartita (único mecanismo de cierre)

Toda compra solo puede cerrarse cuando coinciden:

1. **OC vs Recepción**  
2. **OC vs Factura**  
3. **Factura vs Pago (contado) o CxP (crédito)**  

➡️ El pago NO cierra.  
➡️ La conciliación completa SÍ cierra.

---

# 2. Ciclo Base del Proceso

1. Requisición  
2. Validación técnica  
3. Cotizaciones  
4. Autorización económica  
5. OC (normal o preliminar)  
6. Entrega o servicio  
7. Recepción (preliminar o formal)  
8. Factura  
9. Pago / CxP  
10. Conciliación  
11. Cierre  

---

# 3. Tipos de OC

| Tipo | Uso |
|------|-----|
| **OC Normal** | Uso estándar con precio final definido. |
| **OC Preliminar** | Obligatoria en compras críticas, sin precio final. |

---

# 4. Tipos de Recepción

| Tipo | Uso |
|------|-----|
| **Recepción Preliminar** | Sin precio final, entrega sin autorización, compra crítica, anticipo. |
| **Recepción Formal** | Con OC normal, precio final, factura consistente. |

---

# 5. Reglas de Cotización

| Monto | Requisito |
|-------|-----------|
| Hasta $5,000 | 1 cotización |
| $5,001–$15,000 | 2 cotizaciones |
| > $15,000 | 3 cotizaciones + comparativo |

👉 En compras críticas pueden omitirse al inicio, pero deben completarse o justificarse **antes de convertir a OC normal**.

---

# 6. Autorizaciones Económicas

## 6.1 Taller (y Obra no presupuestada)
| Monto | Autorización |
|-------|--------------|
| Hasta $20,000 | Jefe de Área |
| $20,001–$50,000 | Director de Área |
| > $50,000 | Director General |

## 6.2 Obra — Concepto Presupuestado

Obra **no usa montos**, sino:

- Validación de **PU real ≤ PU presupuestado**  
- Validación de **saldo suficiente del concepto**  

Si NO cumple:

- PU > PU presupuestado → autoriza Área de Obra  
- Saldo insuficiente → aplica sobreejercicio (20k / 50k / DG)

---

# 7. LOS 8 FLUJOS MAESTROS COMPLETOS  
*(contenidos exactamente como los solicitaste)*

---

# 1️⃣ TALLER — Normal + Crédito

### **Requisición**
- Solicitud formal de bienes o servicios.  
- Incluye cantidades, especificaciones y motivo.  
- Estado: *Pendiente → Requisición validada.*

### **Validación técnica**
- El jefe de área verifica que la necesidad es correcta.  
- Puede ajustar modelo, medida o cantidad.  
- Aquí **NO** se marca crítica (si lo fuera, se desvía al flujo crítico).

### **Cotizaciones según monto**
- Hasta $5,000 → 1 cotización.  
- $5,001–$15,000 → 2 cotizaciones.  
- >$15,000 → 3 cotizaciones + comparativo.  
- Obligatorio en Taller.  
- No se puede avanzar sin completar.

### **Autorización por montos**
- Hasta $20,000 → Jefe de Área.  
- $20,001–$50,000 → Director de Área.  
- >$50,000 → Director General.  
- Se valida el **monto total** de la OC.

### **OC normal**
- Precio final definido y bloqueado.  
- Cualquier cambio requiere reautorizar.

### **Entrega**
- Solo puede ocurrir después de generar una OC normal.

### **Recepción formal**
- Cantidades y artículos deben coincidir con la OC.  
- Se valida calidad y cumplimiento.

### **Factura**
- Debe coincidir con recepción y OC en precio, cantidad e impuestos.

### **Programar pago (CxP)**
- Se genera documento por pagar.  
- Entra en calendario de pagos.

### **Conciliación**
- OC vs Recepción  
- OC vs Factura  
- Factura vs CxP

### **Cierre**
- Solo tras conciliación completa.

---

# 2️⃣ TALLER — Normal + Contado

1. Requisición  
2. Validación técnica  
3. Cotizaciones según monto (obligatorias)  
4. Autorización por montos  
5. OC normal  
6. **Pago de contado**
   - Total o parcial.  
   - Ocurre ANTES de la entrega.  
   - El pago **NO** cierra la OC.
7. Entrega  
8. Recepción formal  
9. Factura  
10. Conciliación  
11. Cierre  

*Es igual al Normal + Crédito, excepto por el pago anticipado.*

---

# 3️⃣ TALLER — Crítico + Crédito

### **Requisición**

### **Validación técnica**
Aquí el jefe de área marca **CRÍTICA**.  
El sistema registra:
- responsable,  
- motivo,  
- urgencia operativa,  
- riesgo operativo.

### **Cotizaciones iniciales (opcionales)**
- El flujo puede avanzar con 1 cotización o incluso 0 si el tiempo lo exige.

### **OC preliminar**
- Obligatoria en compra crítica.  
- Puede no tener precio final.  
- Permite separar mercancía o solicitar servicio inmediato.

### **Entrega sin pago**

### **Recepción preliminar**
- Debe validarse en <72 horas.

### **Precio final**

### **Completar / justificar cotizaciones**

### **Autorización retroactiva por montos**
- Con rangos del Taller.

### **Convertir a OC normal**

### **Factura**

### **Programar pago (CxP)**

### **Conciliación**

### **Cierre**

---

# 4️⃣ TALLER — Crítico + Contado

1. Requisición  
2. Validación técnica → se marca CRÍTICA  
3. Cotizaciones opcionales  
4. OC preliminar  
5. Proveedor exige anticipo o pago  
6. **Pago anticipado o total**  
   - No cierra la OC  
7. Entrega  
8. Recepción preliminar o formal  
9. Precio final  
10. Completar / justificar cotizaciones  
11. Autorización retroactiva por montos  
12. Convertir a OC normal  
13. Pago complementario (si aplica)  
14. Factura  
15. Conciliación  
16. Cierre  

---

# 5️⃣ OBRA — Normal + Crédito

La bifurcación de obra es CLAVE: primero se determina si hay **concepto presupuestado**.

---

## 🔵 **Si ES concepto presupuestado**

1. Requisición  
2. Validación técnica  
3. Cotizaciones obligatorias  
4. Validación económica del concepto  
   - Validar PU real ≤ PU presupuestado  
   - Validar saldo del concepto ≥ monto requerido  
   - Si ambos se cumplen → autorización automática del ERP  
   - PU > PU presupuestado → autoriza área de obra  
   - Saldo insuficiente → sobreejercicio (20k / 50k / DG)
5. OC normal  
6. Entrega  
7. Recepción formal  
8. Factura  
9. Programar pago (CxP)  
10. Conciliación  
11. Cierre  

---

## 🔴 **Si NO es concepto presupuestado (opera como Taller)**

1. Requisición  
2. Validación técnica  
3. Cotizaciones según monto  
4. Autorización por montos  
5. OC normal  
6. Entrega  
7. Recepción formal  
8. Factura  
9. CxP  
10. Conciliación  
11. Cierre  

---

# 6️⃣ OBRA — Normal + Contado

Flujo igual al Normal + Crédito, excepto:

- **Pago anticipado antes de entrega (no cierra la OC)**

### Bifurcación:

#### Si ES concepto presupuestado:
- Validación PU + saldo  
- Autorización automática o por área de obra  
- Resto del flujo igual a normal + crédito  

#### Si NO es concepto:
- Opera como Taller  

---

# 7️⃣ OBRA — Crítico + Crédito

Al marcar CRÍTICA, obra obtiene los permisos de urgencia pero **mantiene control económico por PU + saldo**.

### Paso a paso:

1. Requisición  
2. Validación técnica (marca crítica — registra responsable, motivo, urgencia)  
3. ¿Concepto presupuestado?
   - Si es → validar PU estimado + saldo  
   - Si no es → aplicar montos como Taller  
4. Cotizaciones opcionales  
5. OC preliminar  
6. Entrega sin pago  
7. Recepción preliminar  
8. Precio final  
9. Validación económica final  
   - Si es concepto → PU final + saldo  
   - Si no es → rangos del Taller  
10. Completar o justificar cotizaciones  
11. Autorización retroactiva  
12. Convertir a OC normal  
13. Factura  
14. CxP  
15. Conciliación  
16. Cierre  

---

# 8️⃣ OBRA — Crítico + Contado

1. Requisición  
2. Validación técnica (marca crítica)  
3. Validación económica inicial (concepto o no concepto)  
4. Cotizaciones opcionales  
5. OC preliminar  
6. Pago anticipado  
7. Entrega  
8. Recepción preliminar o formal  
9. Precio final  
10. Validación económica final  
11. Completar / justificar cotizaciones  
12. Autorización retroactiva  
13. OC normal  
14. Pago complementario  
15. Factura  
16. Conciliación  
17. Cierre  

---

# 8. Estados del Sistema

- Pendiente  
- Requisición validada  
- En cotización  
- En autorización  
- OC preliminar  
- OC normal  
- En recepción  
- En espera de factura  
- En conciliación  
- Cerrada  

---

# 9. Reglas del Motor del ERP

El ERP debe permitir:

- OC preliminar sin precio  
- Recepción preliminar sin OC normal  
- Autorización retroactiva  
- Anticipos + pagos complementarios  
- Varias recepciones  
- Varias facturas  
- Servicios y refacciones mezclados  
- Cualquier cambio de precio en OC normal → requiere reautorizar  
- Conversión obligatoria de OC preliminar → OC normal  

---

# 10. Documento Fuente

- Proceso de Compras COMAQSA (GPT)  
- Particularidades de Compra Crítica  
- Diagramas maestros de Taller, Obra y flujos Normal/Crítico  

---

# Equipo de Desarrollo ERP – COMAQSA
