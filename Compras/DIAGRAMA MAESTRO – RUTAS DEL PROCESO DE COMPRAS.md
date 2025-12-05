```mermaid
flowchart LR

    %% INICIO COMÚN
    INI["Requisición"]

    AREA{"¿Taller u Obra?"}

    INI --> AREA

    %% =====================================
    %% LADO IZQUIERDO: TALLER
    %% =====================================
    subgraph TALLER["Taller"]
        T_VT["Validación técnica (Taller)"]
        T_CRIT{"¿Compra crítica?"}
        T_NORM["Compra NORMAL (Taller)"]
        T_CRIT_R["Compra CRÍTICA (Taller)"]

        T_PAGO_N{"¿Crédito o contado?"}
        T_PAGO_C{"¿Crédito o contado?"}

        T_F1["Flujo 1<br/>NORMAL + CRÉDITO<br/>(ver DIAGRAMA 1)"]
        T_F2["Flujo 2<br/>NORMAL + CONTADO<br/>(ver DIAGRAMA 2)"]
        T_F3["Flujo 3<br/>CRÍTICO + CRÉDITO<br/>(ver DIAGRAMA 3)"]
        T_F4["Flujo 4<br/>CRÍTICO + CONTADO<br/>(ver DIAGRAMA 4)"]

        T_RULES["Autorización por montos<br/><br/>
        ≤ 20,000 → Jefe de Área<br/>
        20,001–50,000 → Director de Área<br/>
        &gt; 50,000 → Director General"]

        AREA -->|Taller| T_VT
        T_VT --> T_CRIT

        T_CRIT -->|No| T_NORM
        T_CRIT -->|Sí| T_CRIT_R

        T_NORM --> T_PAGO_N
        T_CRIT_R --> T_PAGO_C

        T_PAGO_N -->|Crédito| T_F1
        T_PAGO_N -->|Contado| T_F2

        T_PAGO_C -->|Crédito| T_F3
        T_PAGO_C -->|Contado| T_F4

        %% Reglas de montos aplican a todas las compras de Taller
        T_VT --> T_RULES
    end

    %% =====================================
    %% LADO DERECHO: OBRA
    %% =====================================
    subgraph OBRA["Obra"]
        O_VT["Validación técnica (Obra)"]

        OB_TIPO{"¿Concepto presupuestado?"}
        OB_P["Concepto presupuestado<br/>Validación PU + saldo"]
        OB_N["Obra sin concepto<br/>Sigue reglas de Taller<br/>(autorización por montos)"]

        O_CRIT{"¿Compra crítica?"}
        O_NORM["Compra NORMAL (Obra)"]
        O_CRIT_R["Compra CRÍTICA (Obra)"]

        O_PAGO_N{"¿Crédito o contado?"}
        O_PAGO_C{"¿Crédito o contado?"}

        O_F1["Flujo 1<br/>NORMAL + CRÉDITO<br/>(ver DIAGRAMA 1)"]
        O_F2["Flujo 2<br/>NORMAL + CONTADO<br/>(ver DIAGRAMA 2)"]
        O_F3["Flujo 3<br/>CRÍTICO + CRÉDITO<br/>(ver DIAGRAMA 3)"]
        O_F4["Flujo 4<br/>CRÍTICO + CONTADO<br/>(ver DIAGRAMA 4)"]

        O_RULES["Autorización por montos<br/>(obra sin concepto)<br/><br/>
        ≤ 20,000 → Jefe de Área<br/>
        20,001–50,000 → Director de Área<br/>
        &gt; 50,000 → Director General"]

        AREA -->|Obra| O_VT

        O_VT --> OB_TIPO
        OB_TIPO -->|Sí| OB_P
        OB_TIPO -->|No| OB_N

        %% En Obra, ambas (con concepto y sin concepto) pueden ser normales o críticas
        OB_P --> O_CRIT
        OB_N --> O_CRIT

        O_CRIT -->|No| O_NORM
        O_CRIT -->|Sí| O_CRIT_R

        O_NORM --> O_PAGO_N
        O_CRIT_R --> O_PAGO_C

        O_PAGO_N -->|Crédito| O_F1
        O_PAGO_N -->|Contado| O_F2

        O_PAGO_C -->|Crédito| O_F3
        O_PAGO_C -->|Contado| O_F4

        %% Solo OBRA SIN CONCEPTO usa montos
        OB_N --> O_RULES
    end

    %% =====================================
    %% FINAL COMÚN: CONCILIACIÓN Y CIERRE
    %% =====================================
    CONC["Conciliación tripartita<br/>OC vs Recepción vs Factura vs Pago/CxP"]
    CIERRE["Cierre de compra"]

    T_F1 --> CONC
    T_F2 --> CONC
    T_F3 --> CONC
    T_F4 --> CONC

    O_F1 --> CONC
    O_F2 --> CONC
    O_F3 --> CONC
    O_F4 --> CONC

    CONC --> CIERRE
