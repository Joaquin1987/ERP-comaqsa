```mermaid
flowchart TD

    %% ==== NODOS PRINCIPALES ====

    A["Requisición"] --> B["Validación técnica"] --> C["Cotizaciones según monto"] --> 
    D["Autorización por montos"] --> E["Orden de compra normal"] --> 
    F["Entrega"] --> G["Recepción formal"] --> H["Factura"] --> 
    I["Programar pago (CxP)"] --> J["Conciliación tripartita"] --> K["Cierre de compra"]

    %% ==== CÓDIGOS FUERA DEL RECUADRO (esquina superior izquierda) ====

    AC[REQ_NC]:::code --> A
    BC[VT_NC]:::code --> B
    CC[COT_NC]:::code --> C
    DC[AUT_NC]:::code --> D
    EC[OC_NC]:::code --> E
    FC[ENT_NC]:::code --> F
    GC[REC_NC]:::code --> G
    HC[FAC_NC]:::code --> H
    IC[PROG_NC]:::code --> I
    JC[CONC_NC]:::code --> J
    KC[CIERRE_NC]:::code --> K

    %% ==== NOTAS LATERALES NECESARIAS ÚNICAMENTE ====

    subgraph NotaValidacion[" "]
        NVT["Aquí el jefe del área define si la compra es <b>CRÍTICA</b>.<br/>Esto rompe candados del flujo normal,<br/>por eso este paso es clave."]
    end
    NVT -.-> B

    subgraph NotaConc[" "]
        NCO["Conciliación tripartita:<br/>OC vs Recepción vs Factura.<br/><b>Solo aquí puede cerrarse la compra.</b>"]
    end
    NCO -.-> J

    %% ==== ESTILOS ====
    classDef code fill=#ffffff,stroke=#ffffff,color=#444,font-size=10px;
```
