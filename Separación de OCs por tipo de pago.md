# ERP Obras - Control de Contratos y Estimaciones

## Objetivo

Permitir el control de obras subcontratadas mediante contratos,
estimaciones, pagos y finiquitos.

---

## Entidades

### Obra

### OC Madre

### OC Auxiliar

### Estimación

### Pago

---

## Reglas de Negocio

RN-001
Al crear una obra se genera una OC Madre.

RN-002
La OC Madre conserva permanentemente el monto original contratado.

RN-003
La obra puede tener múltiples estimaciones.

RN-004
Las estimaciones pueden pagarse mediante distintos tipos de pago.

RN-005
Por cada tipo de pago utilizado se genera una OC Auxiliar.

...

RN-020
La obra únicamente se considera cerrada cuando existe un finiquito registrado.

---

## Estados

Alta
En ejecución
Con estimaciones
Con pagos
En proceso de finiquito
Finiquitada
Cerrada

---

## Flujo Operativo

(diagrama Mermaid)

---

## Casos Especiales

Finiquito menor al contrato original.

Finiquito mayor al contrato original.

Pagos mixtos.

Pagos posteriores al finiquito.

Cancelación de estimaciones.
