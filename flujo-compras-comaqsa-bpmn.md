# Flujo de Compras COMAQSA – BPMN (Mermaid)

Este archivo contiene el flujo general de compras de COMAQSA, incluyendo:

- Requisición normal y crítica
- Órdenes de compra normales y preliminares
- Compras a crédito y de contado
- Autorizaciones por monto
- Recepciones preliminar y formal
- Facturación, pago y cierre de OC

---

```mermaid
flowchart TD

%% ==== INICIO: REQUISICIÓN ====
A[Requisición creada] --> B{¿Crítico?}

%% DECISIÓN CRÍTICO
B -->|Sí (equipo parado)| C[Generar OC Preliminar]
B -->|No| D[Validación técnica<br/>Jefe de área]

%% ==== FLUJO CRÍTICO (OC PRELIMINAR) ====
C --> E[Enviar OC Preliminar<br/>al proveedor<br/>(separar material)]
E --> F[Recepción Preliminar]
F --> G[Instalación de pieza<br/>Equipo vuelve a operar]
G --> H[Completar cotizaciones]
H --> I[Autorización retroactiva<br/>según monto]

%% AUTORIZACIÓN RETROACTIVA SEGÚN MONTO
I --> I1{Monto real}
I1 -->|≤ 20,000| I2[Autoriza Jefe de área]
I1 -->|20,001 - 50,000| I3[Autoriza Director de área]
I1 -->|> 50,000| I4[Autoriza Director General]

I2 --> J[Convertir a OC Normal<br/>AUTORIZADA]
I3 --> J
I4 --> J

J --> K[Convertir Recepción<br/>Preliminar en Formal]
K --> L[Registrar Factura]
L --> M{¿Crédito o Contado?}

M -->|Crédito| N[Programar Pago<br/>15/30 días]
M -->|Contado| O[Pago inmediato]

N --> P[Cerrar OC]
O --> P

%% ==== FLUJO NORMAL (OC NORMAL) ====
D --> Q[Proceso de Cotizaciones]
Q --> R[Generar OC Normal]

%% AUTORIZACIÓN PREVIA (FLUJO NORMAL)
R --> S{Monto real}
S -->|≤ 20,000| S1[Autoriza Jefe de área]
S -->|20,001 - 50,000| S2[Autoriza Director de área]
S -->|> 50,000| S3[Autoriza Director General]

S1 --> T[Enviar OC al proveedor]
S2 --> T
S3 --> T

T --> U[Recepción Formal]
U --> V[Registrar Factura]
V --> W{¿Crédito o Contado?}

W -->|Crédito| X[Programar Pago]
W -->|Contado| Y[Pago inmediato]

X --> Z[Cerrar OC]
Y --> Z
```

---

## Notas

- Este diagrama está pensado para visualizarse en GitHub, Notion, Obsidian o cualquier visor compatible con **Mermaid**.
- Solo necesitas subir este archivo a tu repositorio y abrirlo en GitHub para ver el flujo dibujado.
