# PARTICULARIDADES DE UNA COMPRA CRÍTICA – COMAQSA

Este documento describe **todas las reglas, excepciones, candados y particularidades** de una compra crítica en COMAQSA, incluyendo el manejo correcto de **cotizaciones**, OC preliminar, autorizaciones retroactivas, recepciones, pagos, y la conversión a OC normal.

---

## 1. DEFINICIÓN DE COMPRA CRÍTICA

Una compra se considera **CRÍTICA** cuando:

- El equipo está parado.
- La operación está en riesgo inmediato.
- No existe alternativa temporal.
- El tiempo de respuesta determina evitar pérdidas mayores.

Al marcarla como CRÍTICA, el ERP ajusta reglas, abre candados y activa el flujo de urgencias.

---

## 2. CAMBIOS EN EL FLUJO POR SER CRÍTICA

Al marcar una requisición como **CRÍTICO**, el ERP permite:

- Avanzar con una sola cotización, o incluso SIN cotización.
- Generar **OC preliminar** aunque no haya precio final.
- Recibir artículos o servicios **antes de autorización**.
- Pagar anticipos sin conocer precio final.
- Realizar recepción preliminar sin OC normal.

Estos privilegios requieren:

- Registro obligatorio del responsable que marcó CRÍTICO.
- Registro de motivo.
- Autorización retroactiva obligatoria.

---

## 3. OC PRELIMINAR EN COMPRAS CRÍTICAS

En compras críticas, la **OC preliminar es obligatoria**.

Características:

- Puede generarse sin precio.
- Puede tener precio estimado.
- Permite separar mercancía o pedir atención inmediata.
- No permite facturación.
- No cierra el flujo.

La OC preliminar **SE DEBE** convertir a OC normal después.

---

## 4. RECEPCIÓN EN COMPRAS CRÍTICAS

### 4.1 Recepción preliminar

Ocurre cuando:

- No hay precio final.
- El proveedor entregó sin autorización.
- Hubo anticipo pero falta monto real.
- El servicio se realizó antes de completar el flujo.

Debe validarse en máximo **72 horas**.

### 4.2 Recepción formal

Ocurre cuando:

- Ya existe OC normal.
- Ya hay precio final.
- La factura coincide con lo recibido.

---

## 5. AUTORIZACIÓN POR MONTOS (RETROACTIVA)

En compras críticas, la autorización por montos puede ocurrir **después** de:

- La entrega
- El servicio
- La recepción preliminar
- Tener el precio final

Requisitos:

- Registro de qué aprobador autorizó.
- Registro de justificación.
- Aplicación de rangos de aprobación normales.

---

## 6. PAGO EN COMPRAS CRÍTICAS

### 6.1 Crítico + Crédito

- No se paga antes.
- Se entrega primero.
- Se obtiene precio final.
- Se autoriza retroactivo.
- Se factura.
- Se **programa pago**.

### 6.2 Crítico + Contado

Dos variantes:

#### A) Con precio final

- OC preliminar
- Autorización retroactiva
- Pago total
- Entrega

#### B) Sin precio final (caso común)

- OC preliminar
- Pago anticipado
- Servicio / entrega
- Precio final después
- Autorización retroactiva
- Pago complementario (si aplica)

En ambos casos:

- El primer pago **no cierra** la OC.
- La OC solo cierra tras **conciliación**.

---

## 7. CONCILIACIÓN TRIPARTITA (OBLIGATORIA)

La OC se cierra solo cuando:

### 7.1 OC vs Recepción

- Artículos coinciden
- Cantidades coinciden
- No hay pendientes

### 7.2 OC vs Factura

- Precios correctos
- Cantidades correctas
- Impuestos correctos

### 7.3 Factura vs Pago / CxP

- **Crédito:** debe existir un documento por pagar
- **Contado:** pagos ejecutados deben cubrir el total

Solo entonces la OC se cierra.

---

## 8. MANEJO DE COTIZACIONES EN COMPRAS CRÍTICAS

**Reglas normales:**

- Hasta $5,000 → 1 cotización
- $5,001 a $15,000 → 2 cotizaciones
- Más de $15,000 → 3 cotizaciones + comparativo

### PERO EN COMPRA CRÍTICA:

La prioridad **NO es el mejor precio**.
La prioridad es **el menor tiempo de entrega**.

Ejemplo típico:

- Matco responde primero
- Tiene entrega inmediata
- Es OEM
- Es más caro
- Pero es la única opción que cumple con la urgencia

### ¿Qué sucede con las cotizaciones?

1. El sistema **permite generar OC preliminar con 1 sola cotización**.
2. El sistema **solo exige completar cotizaciones al momento de convertir a OC NORMAL**.
3. Si la justificación indica urgencia / equipo parado:

   - **SE PUEDE** convertir a OC normal **con una sola cotización**,
   - siempre y cuando la justificación explique por qué.
4. El sistema registra:

   - Nombre del proveedor elegido.
   - Tiempo de entrega.
   - Motivo por el cual se ignoraron cotizaciones faltantes.
   - Responsable que autorizó la excepción.

### Casos aceptados para elegir al proveedor más caro:

- Único con entrega inmediata.
- OEM requerido.
- Garantía del equipo depende de usar esa marca.
- Riesgo operativo mayor por esperar más opciones.
- No existe sustituto.

### En estos casos la regla es:

**“Cotizaciones completas si el tiempo lo permite… excepto compras críticas justificadas.”**

El sistema debe permitir ambas rutas.

---

## 9. ¿CÓMO SE COMPLETAN LAS COTIZACIONES EN UNA COMPRA CRÍTICA?

Tres rutas válidas:

### Ruta 1 — Completar cotizaciones después

- Se compra de inmediato (OC preliminar)
- Se entrega
- Se recibe
- Se obtiene precio final
- Después se cargan las cotizaciones faltantes
- Se autoriza retroactivo
- Se convierte a OC normal

### Ruta 2 — Justificación para no completar

- OC preliminar
- Entrega inmediata
- No se pueden completar cotizaciones (tiempo crítico)
- Se deja registrado:

  - motivo,
  - proveedor elegido,
  - impacto operativo,
  - firma del aprobador por montos.
- Se convierte a OC normal con UNA sola cotización.

### Ruta 3 — Mezcla

- Se sube la cotización de Matco inmediatamente
- Se suben las demás en cuanto lleguen
- Se convierte a OC normal cuando se cumpla el mínimo
  o cuando ya esté justificada la excepción.

Todas las rutas son válidas.

---

## 10. RESUMEN EJECUTIVO

Una compra crítica permite:

- Avanzar sin autorizaciones previas
- OC preliminar sin precio
- Entrega antes de autorización
- Recepción preliminar
- Autorización retroactiva
- Pago anticipado
- Conversión posterior a OC normal
- Justificación formal de proveedor
- Excepciones en cotizaciones
- Conciliación como cierre final

Pero mantiene:

- Control
- Auditoría
- Registro
- Responsables
- Justificación obligatoria

FIN DEL DOCUMENTO
