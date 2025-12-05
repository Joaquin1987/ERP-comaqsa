```mermaid
flowchart TD

    %% TÍTULO
    T["OBRA – FLUJO MAESTRO COMPLETO"]

    %% INICIO COMÚN
    R["Requisición"]
    VT["Validación técnica"]

    T --> R --> VT

    %% DECISIÓN: ¿COMPRA CRÍTICA?
    CRIT{"¿Compra crítica?"}
    VT --> CRIT

    NORM["Compra NORMAL"]
    COMP_CRIT["Compra CRÍTICA"]

    CRIT -->|"No"| NORM
    CRIT -->|"Sí"| COMP_CRIT

    %% =====================================
    %% RAMA NORMAL (OBRA)
    %% =====================================

    COT_N["Cotizaciones según monto<br/>(obligatorias)"]
    NORM --> COT_N

    TIPO_N{"¿Concepto presupuestado de obra?"}
    COT_N --> TIPO_N

    ECON_CP_N["Validación económica (concepto presupuestado)<br/><br/>
    - Validar PU real vs PU presupuestado<br/>
    - Validar saldo del concepto<br/><br/>
    Si PU real ≤ PU presupuestado y saldo suficiente → autoriza sistema<br/>
    Si PU real > PU presupuestado → autoriza área de obra<br/>
    Si saldo insuficiente → sobreejercicio (rangos 20k / 50k / DG)"]

    ECON_NOCP_N["Validación económica (sin concepto)<br/><br/>
    Sigue reglas de Taller:<br/>
    - Autorización por montos<br/>
    Hasta 20,000 → Jefe de área<br/>
    20,001 a 50,000 → Director de área<br/>
    &gt; 50,000 → Director general"]

    TIPO_N -->|"Sí, es concepto"| ECON_CP_N
    TIPO_N -->|"No, no es concepto"| ECON_NOCP_N

    OC_N["OC normal"]

    ECON_CP_N --> OC_N
    ECON_NOCP_N --> OC_N

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
    %% RAMA CRÍTICA (OBRA)
    %% =====================================

    %% Cotizaciones opcionales por urgencia
    COT_C["Cotizaciones<br/>(opcionales por urgencia)"]
    COMP_CRIT --> COT_C

    OC_PRE["OC preliminar<br/>(compra crítica)"]
    COT_C --> OC_PRE

    P_C{"¿Crédito o contado?"}
    OC_PRE --> P_C

    %% -------- Crítico + CRÉDITO --------
    CC_ENT["Entrega sin pago"]
    CC_REC["Recepción preliminar"]
    CC_PREC["Definir precio final"]

    %% Validación económica y completar cotizaciones ANTES de autorizar
    CC_ECON["Validación económica de obra<br/><br/>
    - Si es concepto: validar PU final y saldo del concepto<br/>
    - Si no es concepto: aplicar rangos de montos (Taller)<br/><br/>
    Además:<br/>
    - Completar cotizaciones pendientes o justificar excepción"]

    CC_AUT["Autorización retroactiva<br/>por montos"]
    CC_OCN["Convertir a OC normal"]
    CC_FAC["Factura"]
    CC_PROG["Programar pago CxP"]

    P_C -->|"Crédito"| CC_ENT
    CC_ENT --> CC_REC --> CC_PREC --> CC_ECON --> CC_AUT --> CC_OCN --> CC_FAC --> CC_PROG

    %% -------- Crítico + CONTADO --------
    CT_EXIGE["Proveedor exige<br/>anticipo o pago"]
    CT_PAGO_ANT["Pago anticipado o total<br/>(no cierra la compra)"]
    CT_ENT["Entrega / servicio"]
    CT_REC["Recepción preliminar o formal"]
    CT_PREC["Definir precio final"]

    CT_ECON["Validación económica de obra<br/><br/>
    - Si es concepto: validar PU final y saldo del concepto<br/>
    - Si no es concepto: aplicar rangos de montos (Taller)<br/><br/>
    Además:<br/>
    - Completar cotizaciones pendientes o justificar excepción"]

    CT_AUT["Autorización retroactiva<br/>por montos"]
    CT_OCN["Convertir a OC normal"]
    CT_PAGO_COMP["Pago complementario<br/>(si aplica)"]
    CT_FAC["Factura"]

    P_C -->|"Contado"| CT_EXIGE
    CT_EXIGE --> CT_PAGO_ANT --> CT_ENT --> CT_REC --> CT_PREC --> CT_ECON --> CT_AUT --> CT_OCN --> CT_PAGO_COMP --> CT_FAC

    %% =====================================
    %% NOTA: QUÉ IMPLICA MARCAR COMO CRÍTICA EN OBRA
    %% =====================================
    NOTA_CRIT["Al marcar una compra como CRÍTICA el sistema permite:<br/>
    - Generar OC preliminar<br/>
    - Recibir con recepción preliminar<br/>
    - Entregar o pagar antes de autorización completa<br/>
    - Hacer autorización por montos de forma retroactiva<br/>
    (pero siempre validando PU y presupuesto de obra antes de convertir a OC normal)"] -.-> COMP_CRIT

    %% =====================================
    %% CONCILIACIÓN Y CIERRE (COMÚN)
    %% =====================================

    CONC["Conciliación tripartita<br/>OC vs Recepción vs Factura vs Pago/CxP"]
    CIERRE["Cierre de compra"]

    NC_PROG --> CONC
    NCT_FAC --> CONC
    CC_PROG --> CONC
    CT_FAC --> CONC

    CONC --> CIERRE
