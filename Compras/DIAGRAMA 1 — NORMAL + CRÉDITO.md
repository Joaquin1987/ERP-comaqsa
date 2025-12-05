```mermaid
flowchart TD
    %% =====================================
    %%              TÍTULO
    %% =====================================
    T["<b>FLUJO NORMAL + CRÉDITO</b>"]:::title

    %% =====================================
    %%         NODOS PRINCIPALES
    %% =====================================
    A["<b>REQ_NC</b><br/>Requisición"]
    B["<b>VT_NC</b><br/>Validación técnica"]
    C["<b>COT_NC</b><br/>Cotizaciones según monto"]
    D["<b>AUT_NC</b><br/>Autorización por montos"]
    E["<b>OC_NC</b><br/>Orden de compra normal"]
    F["<b>ENT_NC</b><br/>Entrega"]
    G["<b>REC_NC</b><br/>Recepción formal"]
    H["<b>FAC_NC</b><br/>Factura"]
    I["<b>PROG_NC</b><br/>Programar pago CxP"]
    J["<b>CONC_NC</b><br/>Conciliación tripartita"]
    K["<b>CIERRE_NC</b><br/>Cierre de compra"]

    %% Flujo
    T --> A --> B --> C --> D --> E --> F --> G --> H --> I --> J --> K

    %% =====================================
    %%           NOTAS LATERALES
    %% =====================================

    %% Validación técnica — donde se define si la compra es CRÍTICA
    NVT["Aquí el jefe del área determina si la compra es <b>CRÍTICA</b>.<br/>Esto rompe candados del flujo normal."] -.-> B

    %% Autorización por montos — versión oficial según documentos
    NAUT["<b>Rangos oficiales de autorización COMAQSA:</b><br/><br/>
    • ≤ $20,000 → <b>Jefe de Área</b><br/>
    • $20,001 – $50,000 → <b>Director de Área</b><br/>
    • > $50,000 → <b>Director General</b><br/><br/>
    *En Obra presupuestada no aplican montos: se autoriza por PU y saldo del concepto.*"] -.-> D

    %% Conciliación tripartita — cierre solo aquí
    NCO["Conciliación tripartita:<br/>OC vs Recepción vs Factura.<br/><b>Solo aquí puede cerrarse la compra.</b>"] -.-> J

    %% =====================================
    %%               ESTILOS
    %% =====================================
    classDef title fill=none,stroke=none,color=#000,font-size=20px,font-weight=bold;
```
