```mermaid
flowchart TD

    %% TÍTULO
    T["FLUJO CRÍTICO + CRÉDITO"]

    %% NODOS PRINCIPALES
    A["<b>REQ_CC</b><br/>Requisición"]
    B["<b>VT_CC</b><br/>Validación técnica"]
    C["<b>COT_CC</b><br/>Cotizaciones opcional por urgencia"]
    D["<b>OC_PRE_CC</b><br/>OC preliminar"]
    E["<b>ENT_CC</b><br/>Entrega sin pago"]
    F["<b>REC_PRE_CC</b><br/>Recepción preliminar"]
    G["<b>PRECIO_CC</b><br/>Definir precio final"]
    H["<b>COT_CC_COMP</b><br/>Completar cotizaciones o justificar"]
    I["<b>AUT_RET_CC</b><br/>Autorización retroactiva por montos"]
    J["<b>OC_NORM_CC</b><br/>Convertir a OC normal"]
    K["<b>FAC_CC</b><br/>Factura"]
    L["<b>PROG_CC</b><br/>Programar pago CxP"]
    M["<b>CONC_CC</b><br/>Conciliación tripartita"]
    N["<b>CIERRE_CC</b><br/>Cierre de compra"]

    %% FLUJO PRINCIPAL
    T --> A --> B --> C --> D --> E --> F --> G --> H --> I --> J --> K --> L --> M --> N

    %% NOTA: VALIDACIÓN TÉCNICA (donde se marca CRÍTICA)
    NVT["Aquí el jefe del área determina que la compra es crítica.<br/>
    El sistema registra responsable, motivo y urgencia.<br/>
    Al marcar CRÍTICA se abren candados: se permite OC preliminar sin precio,<br/>
    entrega sin autorización previa y recepción preliminar."] -.-> B

    %% NOTA: OC PRELIMINAR (obligatoria en compra crítica)
    NOC["OC preliminar obligatoria en compra crítica:<br/>
    - Puede generarse sin precio o con precio estimado.<br/>
    - Permite separar mercancía o pedir atención inmediata.<br/>
    - No permite facturar.<br/>
    - Debe convertirse después a OC normal."] -.-> D

    %% NOTA: AUTORIZACIÓN RETROACTIVA POR MONTOS (rangos oficiales)
    NAUT["Autorización retroactiva por montos (aplican rangos normales):<br/><br/>
    - Hasta 20,000 → Jefe de Área<br/>
    - De 20,001 a 50,000 → Director de Área<br/>
    - Más de 50,000 → Director General<br/><br/>
    En compras críticas la aprobación es después de conocer el precio final<br/>
    pero los montos y responsables son los mismos."] -.-> I

    %% NOTA: CONCILIACIÓN
    NCO["Conciliación tripartita:<br/>
    - OC vs Recepción<br/>
    - OC vs Factura<br/>
    - Factura vs Documento por pagar CxP<br/><br/>
    Solo aquí puede cerrarse la compra crítica."] -.-> M
