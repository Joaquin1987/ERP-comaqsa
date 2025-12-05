```mermaid
flowchart TD

    %% TÍTULO
    T["TALLER – FLUJO MAESTRO COMPLETO"]

    %% CICLO INICIAL COMÚN
    R["Requisición"]
    VT["Validación técnica"]
    COT["Cotizaciones<br/>según monto"]
    AUT["Autorización por montos<br/><br/>
    Hasta 20,000 → Jefe de área<br/>
    20,001 a 50,000 → Director de área<br/>
    Más de 50,000 → Director general"]

    T --> R --> VT --> COT --> AUT

    %% DECISIÓN: ¿COMPRA CRÍTICA?
    CRIT{"¿Compra crítica?"}
    AUT --> CRIT

    %% =====================================
    %% RAMA NORMAL (Taller)
    %% =====================================
    OC_N["OC normal"]

    CRIT -->|No| OC_N

    P_N{"¿Crédito o contado?"}
    OC_N --> P_N

    %% Normal + CRÉDITO
    N_ENT["Entrega"]
    N_REC["Recepción formal"]
    N_FAC["Factura"]
    N_PROG["Programar pago CxP"]

    P_N -->|Crédito| N_ENT
    N_ENT --> N_REC --> N_FAC --> N_PROG

    %% Normal + CONTADO
    N_PAGO["Pago de contado<br/>(no cierra la compra)"]
    N_ENT_C["Entrega"]
    N_REC_C["Recepción formal"]
    N_FAC_C["Factura"]

    P_N -->|Contado| N_PAGO
    N_PAGO --> N_ENT_C --> N_REC_C --> N_FAC_C

    %% =====================================
    %% RAMA CRÍTICA (Taller)
    %% =====================================
    OC_PRE["OC preliminar<br/>(compra crítica)"]
    CRIT -->|Sí| OC_PRE

    P_C{"¿Crédito o contado?"}
    OC_PRE --> P_C

    %% ---- Crítico + CRÉDITO ----
    CC_ENT["Entrega sin pago"]
    CC_REC["Recepción preliminar"]
    CC_PREC["Definir precio final"]
    CC_AUT["Autorización retroactiva<br/>por montos"]
    CC_OCN["Convertir a OC normal"]
    CC_FAC["Factura"]
    CC_PROG["Programar pago CxP"]

    P_C -->|Crédito| CC_ENT
    CC_ENT --> CC_REC --> CC_PREC --> CC_AUT --> CC_OCN --> CC_FAC --> CC_PROG

    %% ---- Crítico + CONTADO ----
    CT_EXIGE["Proveedor exige<br/>anticipo o pago"]
    CT_PAGO_ANT["Pago anticipado o total<br/>(no cierra la compra)"]
    CT_ENT["Entrega / servicio"]
    CT_REC["Recepción preliminar o formal"]
    CT_PREC["Definir precio final"]
    CT_AUT["Autorización retroactiva<br/>por montos"]
    CT_OCN["Convertir a OC normal"]
    CT_PAGO_COMP["Pago complementario<br/>(si aplica)"]
    CT_FAC["Factura"]

    P_C -->|Contado| CT_EXIGE
    CT_EXIGE --> CT_PAGO_ANT --> CT_ENT --> CT_REC --> CT_PREC --> CT_AUT --> CT_OCN --> CT_PAGO_COMP --> CT_FAC

    %% =====================================
    %% CONCILIACIÓN Y CIERRE (COMÚN A TODO)
    %% =====================================
    CONC["Conciliación tripartita<br/>OC vs Recepción vs Factura vs Pago/CxP"]
    CIERRE["Cierre de compra"]

    %% Todas las rutas llegan a la misma conciliación
    N_PROG --> CONC
    N_FAC_C --> CONC
    CC_PROG --> CONC
    CT_FAC --> CONC

    CONC --> CIERRE

    %% NOTA: QUÉ IMPLICA MARCAR CRÍTICA
    NOTA_CRIT["Al marcar una compra como CRÍTICA el sistema permite:<br/>
    - Generar OC preliminar<br/>
    - Recibir con recepción preliminar<br/>
    - Entregar o pagar antes de autorización completa<br/>
    - Hacer autorización por montos de forma retroactiva"] -.-> OC_PRE
```

    P_C -->|Crédito| F3
    P_C -->|Contado| F4

    %% REGLAS DE AUTORIZACIÓN POR MONTOS
    REGLAS["Autorización por montos (Taller)<br/><br/>
    Hasta 20,000 → Jefe de área<br/>
    20,001 a 50,000 → Director de área<br/>
    Más de 50,000 → Director general"]
    VT --> REGLAS

    %% NOTA: QUÉ IMPLICA MARCAR COMO CRÍTICA
    NOTA_CRIT["Al marcar compra CRÍTICA se habilita:<br/>
    - OC preliminar<br/>
    - Recepción preliminar<br/>
    - Operación/pagos de urgencia según flujo<br/>
    - Autorización retroactiva por montos"] -.-> CRIT_R

    %% CIERRE COMÚN
    CONC["Conciliación tripartita"]
    CIERRE["Cierre de compra"]

    F1 --> CONC
    F2 --> CONC
    F3 --> CONC
    F4 --> CONC
    CONC --> CIERRE
```
