```mermaid
flowchart TD

    T["TALLER – MAPA MAESTRO"]

    R["Requisición"]
    VT["Validación técnica"]

    T --> R --> VT

    CRIT{"¿Compra crítica?"}
    VT --> CRIT

    NORM["Compra NORMAL – Taller"]
    C_RUTA["Compra CRÍTICA – Taller"]

    CRIT -->|No| NORM
    CRIT -->|Sí| C_RUTA

    P_N{"¿Crédito o contado?"}
    P_C{"¿Crédito o contado?"}

    NORM --> P_N
    C_RUTA --> P_C

    F1["Flujo 1<br/>NORMAL + CRÉDITO"]
    F2["Flujo 2<br/>NORMAL + CONTADO"]
    F3["Flujo 3<br/>CRÍTICO + CRÉDITO"]
    F4["Flujo 4<br/>CRÍTICO + CONTADO"]

    P_N -->|Crédito| F1
    P_N -->|Contado| F2

    P_C -->|Crédito| F3
    P_C -->|Contado| F4

    REGLAS["Autorización por montos<br/><br/>
    Hasta 20,000 → Jefe de área<br/>
    20,001 a 50,000 → Director de área<br/>
    Más de 50,000 → Director general"]

    VT --> REGLAS

    CONC["Conciliación tripartita"]
    CIERRE["Cierre de compra"]

    F1 --> CONC
    F2 --> CONC
    F3 --> CONC
    F4 --> CONC
    CONC --> CIERRE
