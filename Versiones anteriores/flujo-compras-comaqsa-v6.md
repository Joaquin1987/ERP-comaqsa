# Diagramas BPMN – Módulo de Compras COMAQSA

A continuación se incluyen diagramas Mermaid compatibles con GitHub.

---

## 1. Flujo Maestro Simplificado (Normal + Crítico)

```mermaid
flowchart TD

%% INICIO
A[Requisición creada] --> B{¿Crítica?}

%% RAMA CRÍTICA
B -->|Sí| C[Generar OC preliminar]
C --> D[Enviar OC preliminar al proveedor]
D --> E[Recepción preliminar]
E --> F[Instalación / servicio]
F --> G[Completar cotizaciones]
G --> H[Autorización retroactiva]

H --> I[Convertir a OC normal]

I --> J{¿Crédito o Contado?}

J -->|Crédito| KC[Flujo Crédito Crítico]
J -->|Contado| KD[Flujo Contado Crítico]

%% Detalle crédito crítico
subgraph KC [Crítico + Crédito]
KC1[Recepción formal] --> KC2[Factura]
KC2 --> KC3[Programar pago]
KC3 --> KC4[Cerrar OC al programar]
end

I --> KC1

%% Detalle contado crítico
subgraph KD [Crítico + Contado]
KD1[Validar pagos anticipados] --> KD2[Factura]
KD2 --> KD3[Cerrar OC al pagar]
end

I --> KD1

%% RAMA NORMAL
B -->|No| N1[Validación técnica]
N1 --> N2[Proceso de cotizaciones]

N2 --> N2A{Monto real}
N2A -->|<=5000| N2B[1 cotización]
N2A -->|5001-15000| N2C[2 cotizaciones]
N2A -->|>15000| N2D[3 cotizaciones + comparativo]

N2B --> N3[Generar OC normal]
N2C --> N3
N2D --> N3

N3 --> N4[Autorización por monto]
N4 --> N5{¿Crédito o Contado?}

%% Normal + Crédito
N5 -->|Crédito| NC1[Enviar OC al proveedor]
NC1 --> NC2[Recepción formal]
NC2 --> NC3[Factura]
NC3 --> NC4[Programar pago]
NC4 --> NC5[Cerrar OC al programar]

%% Normal + Contado
N5 -->|Contado| NT1[Pagar]
NT1 --> NT2[Enviar OC / liberar material]
NT2 --> NT3[Recepción formal]
NT3 --> NT4[Factura]
NT4 --> NT5[Cerrar OC al pagar]

