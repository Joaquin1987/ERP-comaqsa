# Proceso de compras COMAQSA - Diagrama Mermaid

Este documento muestra el flujo oficial del proceso de compras de COMAQSA,
incluyendo los 4 flujos maestros y la regla de conciliacion tripartita
(Recepcion + Factura + Pago/CxP) antes del cierre de la OC.

> Nota: Se usan solo caracteres sin acentos para evitar problemas de compatibilidad.

```mermaid
flowchart TD
  %% Proceso de Compras COMAQSA - basado en documento oficial

  start((Inicio))
  start --> R1[Requisicion]
  R1 --> VT[Validacion tecnica]
  VT --> G_tipo{Compra critica?}

  %% ---------- FLUJO NORMAL ----------
  G_tipo -->|No, normal| N_COT[Cotizaciones segun monto]
  N_COT --> N_AUT[Autorizacion por montos]
  N_AUT --> N_OC[OC normal]
  N_OC --> G_pago_normal{Credito o contado?}

  %% Normal + Credito
  G_pago_normal -->|Credito| N_CR_ENT[Entrega]
  N_CR_ENT --> N_CR_REC[Recepcion formal]
  N_CR_REC --> N_CR_FAC[Factura]
  N_CR_FAC --> N_CR_PAGO[Programar pago (CxP)]
  N_CR_PAGO --> N_CR_CONC[Conciliacion tripartita]
  N_CR_CONC --> N_CR_CIERRE[Cierre de la OC]

  %% Normal + Contado
  G_pago_normal -->|Contado| N_CO_PAGO[Pago]
  N_CO_PAGO --> N_CO_ENT[Entrega]
  N_CO_ENT --> N_CO_REC[Recepcion formal]
  N_CO_REC --> N_CO_FAC[Factura]
  N_CO_FAC --> N_CO_CONC[Conciliacion tripartita]
  N_CO_CONC --> N_CO_CIERRE[Cierre de la OC]

  %% ---------- FLUJOS CRITICOS ----------
  G_tipo -->|Si, critica| C_REQ[Requisicion critica]
  C_REQ --> C_OC_PRE[OC preliminar]
  C_OC_PRE --> G_anticipo{Proveedor exige anticipo o pago?}

  %% Critico + Credito (sin pago previo)
  G_anticipo -->|No (Credito)| CC_ENT[Entrega sin pago]
  CC_ENT --> CC_REC_PRE[Recepcion preliminar]
  CC_REC_PRE --> CC_PRECIO[Definir precio final]
  CC_PRECIO --> CC_AUT_RET[Autorizacion retroactiva]
  CC_AUT_RET --> CC_OC_NORM[Convertir a OC normal]
  CC_OC_NORM --> CC_FAC[Factura]
  CC_FAC --> CC_PROG[Programar pago (CxP)]
  CC_PROG --> CC_CONC[Conciliacion tripartita]
  CC_CONC --> CC_CIERRE[Cierre de la OC]

  %% Critico + Contado (con anticipo/pago)
  G_anticipo -->|Si (Contado)| C_PAGO_ANT[Pago anticipado o total]
  C_PAGO_ANT --> C_ENT[Entrega / servicio]
  C_ENT --> C_REC[Recepcion preliminar o formal]
  C_REC --> C_PRECIO[Definir precio final]
  C_PRECIO --> C_AUT_RET[Autorizacion retroactiva]
  C_AUT_RET --> C_OC_NORM2[Convertir a OC normal]
  C_OC_NORM2 --> C_PAGO_COMP[Pago complementario (si aplica)]
  C_PAGO_COMP --> C_FAC[Factura]
  C_FAC --> C_CONC[Conciliacion tripartita]
  C_CONC --> C_CIERRE[Cierre de la OC]
```
