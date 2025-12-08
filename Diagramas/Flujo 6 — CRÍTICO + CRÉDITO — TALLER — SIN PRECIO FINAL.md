# Flujo 6 — CRÍTICO + CRÉDITO — TALLER — SIN PRECIO FINAL

(Explicación + Diagrama listo para GitHub)

Este flujo describe el proceso de compras cuando la requisición es **crítica**, pertenece al **Taller**, el método de pago es **crédito** y **no existe precio final al inicio**.

Los elementos clave de este flujo son:

- Se puede avanzar **sin precio final**
- Se usa **OC preliminar** (obligatoria)
- El proveedor puede **entregar sin pago**
- Existe **recepción preliminar**
- La autorización por montos es **retroactiva**
- La compra solo se cierra con **Conciliación Tripartita**:

  - OC vs Recepción  
  - OC vs Factura  
  - Factura vs CxP  

---

## **1. Requisición**

El solicitante genera una requisición con descripción, cantidades, especificaciones y motivo.  
La requisición inicia en estado **Pendiente**.

---

## **2. Validación técnica (se marca CRÍTICA)**

El Jefe de Área revisa la solicitud y aquí la compra se marca como **CRÍTICA**.  
El sistema registra:

- Responsable que marcó crítica  
- Motivo  
- Urgencia operativa  

Esto habilita:

- OC preliminar  
- Recepción preliminar  
- Entrega sin autorización completa  
- Autorización retroactiva  

---

## **3. Cotizaciones (opcionales por urgencia)**

Como la compra es crítica, el sistema **NO exige** cotizaciones completas al inicio.  
Puede haber:

- 0 cotizaciones  
- 1 cotización  
- Varias  

Las faltantes se completan más adelante o se justifican.

---

## **4. Orden de Compra (OC) preliminar**

Se genera una **OC preliminar** porque **NO existe precio final**.  
Por reglas COMAQSA:

- No puede existir OC normal sin precio final  
- La OC preliminar **no permite facturar**  
- Solo sirve para adelantar la operación  

---

## **5. Entrega sin pago (crédito)**

El proveedor entrega bienes/servicios **sin recibir pago previo**, porque la compra es crítica y a crédito.

Esto **solo está permitido en compras críticas**.

---

## **6. Recepción preliminar**

Se registra una recepción **preliminar**, porque:

- No existe precio final  
- No existe OC normal  

La recepción preliminar:

- Debe validarse máximo en **72 horas**  
- No sirve para conciliación hasta que se vuelva formal  

---

## **7. Definir precio final**

El proveedor confirma el **precio final real**.  
La OC preliminar se actualiza con el monto correcto.

Sin precio final **no puede ocurrir autorización retroactiva**.

---

## **8. Completar cotizaciones o justificar excepción**

Antes de autorizar retroactivamente, deben completarse cotizaciones o justificar por qué no fue posible:

- Urgencia crítica  
- OEM / único proveedor  
- Inventario inmediato  
- Riesgo operativo  

Se registra:

- Proveedor elegido  
- Motivo de excepción  
- Responsable que autorizó  

---

## **9. Autorización retroactiva por montos**

Como el monto real se conoció después, la autorización ocurre aquí.

**Rangos Taller:**

- ≤ 20,000 → Jefe de Área  
- 20,001–50,000 → Director  
- > 50,000 → Director General  

---

## **10. Convertir a OC normal**

Una vez autorizado retroactivamente:

- Se genera la **OC normal**  
- Se sustituye la OC preliminar  
- El precio final queda formalizado  

---

## **11. Recepción formal**

La recepción preliminar se convierte en **recepción formal**, vinculada ahora a la OC normal.

Validaciones:

- Cantidades  
- Calidad  
- Especificación técnica  

---

## **12. Factura**

El proveedor emite la factura y debe coincidir con:

- OC normal  
- Recepción formal  

Diferencias detienen el flujo.

---

## **13. Programar pago (CxP)**

Con factura válida, se genera la **Cuenta por Pagar**:

- Se agenda según condiciones de crédito  
- No puede existir CxP sin factura correcta  

---

## **14. Conciliación tripartita**

Para cerrar la compra deben coincidir:

1. OC vs Recepción  
2. OC vs Factura  
3. Factura vs CxP  

---

## **15. Cierre de la compra**

La OC se cierra **solo** cuando la conciliación está completa.  
El pago o la recepción **no cierran** la compra por sí solos.

---

# **Diagrama del flujo**

flowchart TD

T["Flujo 6 - CRITICO + CREDITO - TALLER - SIN PRECIO FINAL"]

subgraph F6[" "]  
direction TB

R1["1. Requisicion  
Actor: Solicitante  
Estado: Pendiente"]

R2["2. Validacion Tecnica  
Actor: Jefe de area  
Se marca CRITICA"]

R3["3. Cotizaciones (opcionales)  
En compra critica no son obligatorias  
Pueden ser 0, 1 o mas"]

R4["4. OC Preliminar  
No existe precio final  
No permite facturar"]

R5["5. Entrega sin pago  
Credito: proveedor entrega  
antes de recibir pago"]

R6["6. Recepcion preliminar  
No hay precio final ni OC normal  
Debe validarse < 72 horas"]

R7["7. Definir precio final  
Proveedor confirma monto real  
Se actualiza la OC preliminar"]

R8["8. Completar cotizaciones  
o justificar excepcion  
(urgencia, OEM, unico proveedor, etc.)"]

R9["9. Autorizacion retroactiva por montos  
<= 20k: Jefe de area  
20-50k: Director  
> 50k: Director General"]

R10["10. Convertir a OC Normal  
Precio final definido  
OC preliminar se sustituye"]

R11["11. Recepcion formal  
Se convierte la recepcion  
preliminar en formal"]

R12["12. Factura  
Debe coincidir con  
OC normal y recepcion formal"]

R13["13. Programar pago (CxP)  
Documento por pagar generado  
No existe CxP sin factura valida"]

R14["14. Conciliacion tripartita  
OC vs Recepcion  
OC vs Factura  
Factura vs CxP"]

R15["15. Cierre de OC  
Solo con conciliacion completa"]

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
R14 --> R15
