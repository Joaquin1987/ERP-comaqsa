# COMAQSA – Módulo de Compras (ERP)  
Asistente Oficial del Flujo de Compras

Este repositorio documenta el funcionamiento, reglas operativas y lógica técnica del **Módulo de Compras del ERP COMAQSA**, basado íntegramente en el documento oficial **Proceso de Compras COMAQSA (GPT)**.

---

## Objetivo del Sistema
Garantizar que todas las compras —normales o críticas, de contado o crédito— sigan un flujo uniforme, controlado y auditable, terminando siempre en una **Conciliación Tripartita**:

1. **OC vs Recepción**  
2. **OC vs Factura**  
3. **Factura vs Pago / CxP**

> Ninguna Orden de Compra puede cerrarse sin esta conciliación completa.

---

## Ciclo Base del Proceso de Compras

1. Requisición  
2. Validación técnica  
3. Cotizaciones según monto  
4. Autorización por montos  
5. OC (normal o preliminar)  
6. Entrega o servicio  
7. Recepción (preliminar o formal)  
8. Factura  
9. Pagos o Programación de pago  
10. Conciliación  
11. Cierre de OC

---

## Reglas de Cotizaciones

| Monto | Requisito |
|------|-----------|
| Hasta $5,000 | 1 cotización |
| $5,001 – $15,000 | 2 cotizaciones |
| Más de $15,000 | 3 cotizaciones + comparativo |

---

## Rangos de Autorización

| Monto | Autoriza |
|-------|----------|
| Hasta $20,000 | Jefe de Área |
| $20,001 – $50,000 | Director de Área |
| Más de $50,000 | Director General |

---

## Tipos de Recepción

### **Recepción Preliminar**
- Sin precio final  
- Compras críticas  
- Entregas sin autorización previa  
- Pagos anticipados sin monto definitivo  
- Debe validarse en máximo **72 horas**

### **Recepción Formal**
- OC normal autorizada  
- Precio final conocido  
- Factura coincide con lo recibido  

---

## 🔄 Los 4 Flujos Maestros

### **1️⃣ Normal + Crédito**
1. Requisición  
2. Validación técnica  
3. Cotizaciones  
4. Autorización por montos  
5. OC normal  
6. Entrega  
7. Recepción formal  
7. Factura  
9. Programar pago (CxP)  
10. Conciliación  
11. Cierre  

### **2️⃣ Normal + Contado**
1. Requisición  
2. Validación técnica  
3. Cotizaciones  
4. Autorización  
5. OC normal  
6. Pago  
7. Entrega  
8. Recepción formal  
9. Factura  
10. Conciliación  
11. Cierre  

### **3️⃣ Crítico + Crédito**
1. Requisición  
2. Validación técnica (crítica)  
3. OC preliminar  
4. Entrega sin pago  
5. Recepción preliminar  
6. Precio final  
7. Autorización retroactiva  
8. Convertir a OC normal  
9. Factura  
10. Programar pago  
11. Conciliación  
12. Cierre  

### **4️⃣ Crítico + Contado**
1. Requisición  
2. Validación técnica (crítica)  
3. OC preliminar  
4. Proveedor exige anticipo o pago  
5. Pago anticipado o total  
6. Entrega / servicio  
7. Recepción preliminar o formal  
8. Precio final  
9. Autorización retroactiva  
10. Convertir a OC normal  
11. Pago complementario (si aplica)  
12. Factura  
13. Conciliación  
14. Cierre  

---

## Lógica del Sistema (para desarrolladores)

### **Estados que debe manejar una OC**
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

### **El sistema debe permitir**
- OC preliminar sin precio  
- Autorización retroactiva  
- Cambios de monto antes de autorizar  
- Varias recepciones  
- Varias facturas  
- Pagos anticipados + pagos complementarios  
- Servicios y refacciones mezclados  
- Recepción preliminar sin OC normal  

---

## Regla Maestra de Cierre

Una Orden de Compra **solo puede cerrarse** si existe conciliación completa entre:

1. OC vs Recepción  
2. OC vs Factura  
3. Factura vs Pago (contado)  
4. Factura vs CxP (crédito)

---

## Sobre este Asistente (GPT)

Este repositorio incluye al **Asistente ERP COMAQSA Compras**, un modelo diseñado para:

- Explicar el proceso  
- Validar flujos operativos  
- Ayudar en la implementación del ERP  
- Guiar al desarrollador  
- Corregir flujos incorrectos  
- Proveer lógica, pseudocódigo, validaciones y estados  

---

## Archivo Fuente Principal
Todo el contenido está basado en el documento interno:  
**Proceso de Compras COMAQSA (GPT)**

---

## Contacto  
**Equipo de Desarrollo ERP COMAQSA**
