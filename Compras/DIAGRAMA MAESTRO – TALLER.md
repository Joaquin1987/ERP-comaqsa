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
    &gt; 50,000 → Director general"]

    T --> R --> VT --> COT --> AUT

    %% DECISIÓN: ¿COMPRA CRÍTICA?
    CRIT{"¿Compra crítica?"}
    AUT --> CRIT

    %% RAMAS DE LA DECISIÓN (SOLO DOS FLECHAS)
    NORM["Compra NORMAL"]
    COMP_CRIT["Compra CRÍTICA"]

    CRIT -->|"No"| NORM
    CRIT -->|"Sí"| COMP_CRIT

    %% NOTA: QUÉ IMPLICA MARCAR COMO CRÍTICA (PEGADA A COMPRA CRÍTICA)
    NOTA_CRIT["Al marcar una compra como CRÍTICA el sistema permite:<br/>
    - Generar OC preliminar<br/>
    - Recibir con recepción preliminar<br/>
    - Entregar o pagar antes de autorización completa<br/>
    - Hacer autorización por montos de forma retroactiva"] -.-> COMP_CRIT

    %% =====================================
    %% RAMA NORMAL (TALLER)
    %% =====================================

    OC_N["OC normal"]
    NORM --> OC_N

    P_N{"¿Crédito o contado?"}
    OC_N --> P_N

    %% Normal + CRÉDITO
    NC_ENT["Entrega"]
    NC_REC["Recepción formal"]
    NC_FAC["Factura"]
    NC_PROG["Programar pago CxP"]

    P_N -->|"Crédito"| NC_ENT
    NC_ENT --> NC_REC --> NC_FAC --> NC_PROG

    %% Normal + CONTADO
    NCT_PAGO["Pago de contado<br/>(no cierra la compra)"]
    NCT_ENT["Entrega"]
    NCT_REC["Recepción formal"]
    NCT_FAC["Factura"]

    P_N -->|"Contado"| NCT_PAGO
    NCT_PAGO --> NCT_ENT --> NCT_REC --> NCT_FAC

    %% =====================================
    %% RAMA CRÍTICA (TALLER)
    %% =====================================

    OC_PRE["OC preliminar<br/>(compra crítica)"]
    COMP_CRIT --> OC_PRE

    P_C{"¿Crédito o contado?"}
    OC_PRE --> P_C

    %% Crítico + CRÉDITO
    CC_ENT["Entrega sin pago"]
    CC_REC["Recepción preliminar"]
    CC_PREC["Definir precio final"]
    CC_AUT["Autorización retroactiva<br/>por montos"]
    CC_OCN["Convertir a OC normal"]
    CC_FAC["Factura"]
    CC_PROG["Programar pago CxP"]

    P_C -->|"Crédito"| CC_ENT
    CC_ENT --> CC_REC --> CC_PREC --> CC_AUT --> CC_OCN --> CC_FAC --> CC_PROG

    %% Crítico + CONTADO
    CT_EXIGE["Proveedor exige<br/>anticipo o pago"]
    CT_PAGO_ANT["Pago anticipado o total<br/>(no cierra la compra)"]
    CT_ENT["Entrega / servicio"]
    CT_REC["Recepción preliminar o formal"]
    CT_PREC["Definir precio final"]
    CT_AUT["Autorización retroactiva<br/>por montos"]
    CT_OCN["Convertir a OC normal"]
    CT_PAGO_COMP["Pago complementario<br/>(si aplica)"]
    CT_FAC["Factura"]

    P_C -->|"Contado"| CT_EXIGE
    CT_EXIGE --> CT_PAGO_ANT --> CT_ENT --> CT_REC --> CT_PREC --> CT_AUT --> CT_OCN --> CT_PAGO_COMP --> CT_FAC

    %% =====================================
    %% CONCILIACIÓN Y CIERRE (COMÚN A TODO)
    %% =====================================

    CONC["Conciliación tripartita<br/>OC vs Recepción vs Factura vs Pago/CxP"]
    CIERRE["Cierre de compra"]

    NC_PROG --> CONC      %% Normal + crédito
    NCT_FAC --> CONC      %% Normal + contado
    CC_PROG --> CONC      %% Crítico + crédito
    CT_FAC --> CONC       %% Crítico + contado

    CONC --> CIERRE
```
