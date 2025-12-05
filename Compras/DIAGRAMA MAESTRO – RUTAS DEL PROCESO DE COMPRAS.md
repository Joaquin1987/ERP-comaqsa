```mermaid
flowchart TD

    %% ===========================
    %% TÍTULO
    %% ===========================
    T["MAPA MAESTRO DEL PROCESO DE COMPRAS COMAQSA"]

    %% ===========================
    %% CICLO INICIAL
    %% ===========================
    R["Requisición"]
    VT["Validación técnica"]

    T --> R --> VT

    %% Desde validación técnica se abren DOS EJES:
    %% 1) Tipo de operación: Taller / Obra (y si obra, concepto o no)
    %% 2) Naturaleza de la compra: Normal / Crítica

    %% ===========================
    %% EJE 1: TALLER vs OBRA
    %% ===========================
    TIPO_ORIGEN{"¿Taller u Obra?"}
    VT --> TIPO_ORIGEN

    TALLER["Taller<br/>Control por monto y jerarquía"]
    OBRA["Obra<br/>Control por concepto y presupuesto"]

    TIPO_ORIGEN -->|Taller| TALLER
    TIPO_ORIGEN -->|Obra| OBRA

    %% OBRA: ¿Concepto presupuestado?
    OBRA_TIPO{"¿Concepto presupuestado?"}
    OBRA --> OBRA_TIPO

    OBRA_PRE["Obra con concepto<br/>presupuestado<br/>Validación de PU y saldo"]
    OBRA_NOPRE["Obra sin concepto<br/>Sigue reglas de Taller<br/>(autorización por montos)"]

    OBRA_TIPO -->|Sí| OBRA_PRE
    OBRA_TIPO -->|No| OBRA_NOPRE

    %% Ambas rutas (Taller y Obra no presupuestada) convergen en
    %% el mismo esquema de autorizaciones por monto.
    MONTOS["Autorización por montos<br/>Hasta 20,000 → Jefe de área<br/>20,001–50,000 → Director de área<br/>Más de 50,000 → Director general"]

    TALLER --> MONTOS
    OBRA_NOPRE --> MONTOS

    %% Obra con concepto presupuestado va por validación de PU/saldo,
    %% SIN autorización por montos (salvo sobreejercicio).
    OBRA_PRE --> VALID_OBRA["Validación PU + presupuesto<br/>(obra)"]

    %% Antes de ir a los 4 flujos, todo pasa por
    %% VT (ya lo hicimos) y por estas validaciones.

    %% ===========================
    %% EJE 2: NORMAL vs CRÍTICA
    %% ===========================
    TIPO_COMPRA{"¿Compra crítica?"}
    VT --> TIPO_COMPRA

    NORMAL["Ruta NORMAL"]
    CRITICA["Ruta CRÍTICA<br/>(se abren candados:<br/>OC preliminar, recepción preliminar, pagos urgentes)"]

    TIPO_COMPRA -->|No| NORMAL
    TIPO_COMPRA -->|Sí| CRITICA

    %% ===========================
    %% FORMA DE PAGO
    %% ===========================
    PAGO_N{"¿Crédito o contado?"}
    NORMAL --> PAGO_N

    PAGO_C{"¿Crédito o contado?"}
    CRITICA --> PAGO_C

    %% ===========================
    %% LOS 4 FLUJOS MAESTROS
    %% ===========================
    F1["<b>FLUJO 1</b><br/>Normal + Crédito<br/>Ver DIAGRAMA 1"]
    F2["<b>FLUJO 2</b><br/>Normal + Contado<br/>Ver DIAGRAMA 2"]
    F3["<b>FLUJO 3</b><br/>Crítico + Crédito<br/>Ver DIAGRAMA 3"]
    F4["<b>FLUJO 4</b><br/>Crítico + Contado<br/>Ver DIAGRAMA 4"]

    PAGO_N -->|Crédito| F1
    PAGO_N -->|Contado| F2

    PAGO_C -->|Crédito| F3
    PAGO_C -->|Contado| F4

    %% Conexión desde validaciones económicas hacia los flujos
    MONTOS --> F1
    MONTOS --> F2
    MONTOS --> F3
    MONTOS --> F4

    VALID_OBRA --> F1
    VALID_OBRA --> F2
    VALID_OBRA --> F3
    VALID_OBRA --> F4

    %% ===========================
    %% CIERRE ÚNICO DEL SISTEMA
    %% ===========================
    CONC["Conciliación tripartita<br/>OC vs Recepción vs Factura<br/>Factura vs Pago o CxP"]
    CIERRE["Cierre de compra<br/>OC completamente conciliada"]

    F1 --> CONC
    F2 --> CONC
    F3 --> CONC
    F4 --> CONC

    CONC --> CIERRE
