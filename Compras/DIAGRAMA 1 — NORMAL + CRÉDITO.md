```mermaid
flowchart TD

    %% ==== NODOS PRINCIPALES ====

    A[Requisición]
    B[Validación técnica]
    C[Cotizaciones según monto]
    D[Autorización por montos]
    E[Orden de compra normal]
    F[Entrega]
    G[Recepción formal]
    H[Factura]
    I[Programar pago CxP]
    J[Conciliación tripartita]
    K[Cierre de compra]

    A --> B --> C --> D --> E --> F --> G --> H --> I --> J --> K

    %% ==== ÍNDICES COMO TEXTO SUELTO ARRIBA DEL NODO ====

    AC["REQ_NC"]:::invisible --- A
    BC["VT_NC"]:::invisible --- B
    CC["COT_NC"]:::invisible --- C
    DC["AUT_NC"]:::invisible --- D
    EC["OC_NC"]:::invisible --- E
    FC["ENT_NC"]:::invisible --- F
    GC["REC_NC"]:::invisible --- G
    HC["FAC_NC"]:::invisible --- H
    IC["PROG_NC"]:::invisible --- I
    JC["CONC_NC"]:::invisible --- J
    KC["CIERRE_NC"]:::invisible --- K

    %% ==== NOTAS LATERALES DE VALIDACIÓN Y CONCILIACIÓN ====

    NVT["Aquí el jefe del área define si la compra es CRÍTICA.<br/>Esto rompe candados del flujo normal."] -.-> B

    NCO["Conciliación tripartita:<br/>OC vs Recepción vs Factura.<br/><b>Solo aquí se puede cerrar la compra.</b>"] -.-> J

    %% ==== NOTA DE AUTORIZACIÓN (MONTOS / RESPONSABLES) ====

    NAUT["Rangos de autorización:<br/><br/>
    • &lt; $20,000 → Encargado / Coordinador<br/>
    • $20,000 – $50,000 → Jefe / Gerente de área<br/>
    • &gt; $50,000 → Director General"] -.-> D

    %% ==== ESTILO DEL NODO INVISIBLE ====
    classDef invisible fill=none,stroke=none,color=#333,font-size=10px;
```
