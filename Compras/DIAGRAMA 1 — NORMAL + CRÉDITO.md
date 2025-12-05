```mermaid
flowchart TD

    %% ==== NODOS PRINCIPALES ====

    A[Requisición] --> B[Validación técnica]
    B --> C[Cotizaciones según monto]
    C --> D[Autorización por montos]
    D --> E[Orden de compra normal]
    E --> F[Entrega]
    F --> G[Recepción formal]
    G --> H[Factura]
    H --> I[Programar pago (CxP)]
    I --> J[Conciliación tripartita]
    J --> K[Cierre de compra]

    %% ==== CÓDIGOS FUERA DEL RECUADRO (nodos pequeños arriba) ====

    AC((REQ_NC)) --> A
    BC((VT_NC)) --> B
    CC((COT_NC)) --> C
    DC((AUT_NC)) --> D
    EC((OC_NC)) --> E
    FC((ENT_NC)) --> F
    GC((REC_NC)) --> G
    HC((FAC_NC)) --> H
    IC((PROG_NC)) --> I
    JC((CONC_NC)) --> J
    KC((CIERRE_NC)) --> K

    %% ==== NOTAS LATERALES IMPORTANTES ====

    NVT["Aquí el jefe del área define si la compra es CRÍTICA. Esto rompe candados del flujo normal, por eso este paso es clave."] -.-> B

    NCO["Conciliación tripartita: OC vs Recepción vs Factura. Solo aquí puede cerrarse la compra."] -.-> J
```
