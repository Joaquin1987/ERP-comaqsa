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
   * Solicitud formal de bienes o servicios.
   * Incluye cantidades, especificaciones y motivo de compra.
2. Validación técnica
   * Jefe de área confirma que lo solicitado es correcto.
   * Puede ajustar especificaciones antes de cotizar.
3. Cotizaciones (según monto)
   * Hasta $5,000 → 1 cotización
   * $5,001 a $15,000 → 2 cotizaciones
   * Más de $15,000 → 3 cotizaciones + comparativo
   * Se selecciona proveedor con mejor costo/beneficio.
4. Autorización por montos
   * La OC no puede generarse sin esta aprobación.
5. OC normal
   * Documento formal con precio final y condiciones pactadas.
   * Bloquea cambios de precio sin volver a autorizar.
6. Entrega
   * El proveedor entrega materiales o ejecuta el servicio.
   * Únicamente puede ocurrir después de la OC normal.
7. Recepción formal
   * Confirmación de cantidades, calidad y cumplimiento.
   * Debe coincidir exactamente con la OC.
8. Factura
   * Debe coincidir con la OC y con la recepción formal.
   * Cualquier diferencia obliga a corrección antes de avanzar.
9. Programar pago (CxP)
   * Se genera el documento por pagar.
   * Se integra al calendario de pagos según créditos pactados.
10. Conciliación
* Solo cuando los tres coinciden se puede cerrar.
11. Cierre
* La OC queda completamente conciliada y sin pendientes.


### **2️⃣ Normal + Contado**
1. Requisición
   * Solicitud formal del usuario interno.
   * Debe incluir toda la información para cotizar correctamente.
2. Validación técnica
   * Confirmación de necesidad, modelo correcto, medida, etc.
   * Por jefe de área.
3. Cotizaciones (según monto)
   * Mismos rangos obligatorios que en crédito.
   * Se arma comparativo si excede $15,000.
4. Autorización por montos
   * Requiere aprobación antes de emitir la OC.
   * Evita compras no autorizadas o fuera del presupuesto.
5. OC normal
   * Documento formal con precio final y condiciones pactadas.
   * Se autoriza antes de pagar.
6. Pago (contado)
   * Ocurre ANTES de la entrega.
   * Puede ser total o parcial según lo pactado.
   * Este pago no cierra la OC.
7. Entrega
   * El proveedor entrega bienes/servicios tras confirmar el pago.
8. Recepción formal
   * Validación física y documental de lo recibido.
   * Debe coincidir con lo pactado en la OC.
9. Factura
   * Coincide con OC y recepción.
   * Si hay diferencias, se detiene el flujo hasta corregir.
10. Conciliación
   * Se valida que lo pagado coincide exactamente con lo facturado.
11. Cierre


### **3️⃣ Crítico + Crédito**
1. Requisición
   * Emisor solicita el bien/servicio.
   * No requiere aún precio final.
2. Validación técnica
   * Se revisa la necesidad real.
   * Aquí se determina que es CRÍTICA.
   * El sistema registra:
     • responsable que marcó “crítico”,
     • motivo,
     • riesgo operativo,
     • justificación de urgencia.
3. (Cotizaciones — opcional por urgencia)
   * En compra crítica, NO se exige completar cotizaciones al inicio.
   * El sistema permite continuar con 1 cotización o incluso 0 si el tiempo es determinante.
4. OC preliminar
   * Obligatoria en compra crítica.
   * Puede no tener precio final.
   * Permite separar mercancía o pedir atención inmediata.
   * No se puede facturar aún.
5. Entrega sin pago
   * El proveedor entrega antes de autorización de montos.
6. Recepción preliminar
   * Porque no hay precio final o la entrega ocurrió sin autorización.
   * Debe validarse < 72 horas.
7. Precio final
   * El proveedor confirma el monto real.
   * Se actualiza la OC preliminar.
8. Completar cotizaciones o justificar por qué NO se completan
   * Ruta 1: completar cotizaciones después.
   * Ruta 2: justificar excepción (urgencia, OEM, único con inventario).
   * Ruta 3: combinación.
   * Registro obligatorio de proveedor elegido, motivo y aprobador.
9. Autorización retroactiva por montos
   * Aplican rangos normales.
10. Convertir a OC normal
11. Factura
12. Programar pago (CxP)
13. Conciliación
14. Cierre
 
### **4️⃣ Crítico + Contado**
1. Requisición
   * Solicitud formal del bien/servicio.
2. Validación técnica
   * Se confirma la necesidad técnica.
   * Aquí se determina que es CRÍTICA.
   * Registro de motivo, responsable y urgencia operativa.
3. (Cotizaciones — opcional por urgencia)
   * Pueden faltar al inicio.
   * Se completan después o se justifican.
4. OC preliminar
   * Sin precio final o con precio estimado.
5. Proveedor exige anticipo o pago
6. Pago anticipado o total
   * Puede ocurrir sin conocer el precio final.
   * Este pago NO cierra la OC.
7. Entrega / servicio
8. Recepción preliminar o formal
   * Preliminar: si no hay precio final ni OC normal.
   * Formal: si ya existe precio final y OC normal.
9. Precio final
   * Ajustes, diferencias, servicios extra o adicionales.
   * Se actualiza la OC preliminar.
10. Completar cotizaciones o justificar por qué NO se completan
11. Autorización retroactiva por montos
12. Convertir a OC normal
13. Pago complementario (si aplica)
* Si el precio final supera el anticipo.
14. Factura
15. Conciliación
16. Cierre
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
