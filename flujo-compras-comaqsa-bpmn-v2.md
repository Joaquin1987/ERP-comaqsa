# Flujo de Compras COMAQSA – BPMN (Mermaid) – Version Actualizada

Esta versión incorpora la regla correcta:

**➡ Las OC a crédito se cierran cuando el pago está PROGRAMADO, no cuando se paga.**

---

```mermaid
flowchart TD

A[Requisicion creada] --> B{Critico}

%% FLUJO CRITICO
B -->|SI equipo parado| C[Generar OC Preliminar]
C --> D[Enviar OC Preliminar al proveedor]
D --> E[Recepcion Preliminar]
E --> F[Instalar pieza]
F --> G[Completar cotizaciones]
G --> H[Autorizacion retroactiva]

H --> I{Monto}
I -->|<=20000| J[Autoriza Jefe de area]
I -->|20001-50000| K[Autoriza Director de area]
I -->|>50000| L[Autoriza Director General]

J --> M[Convertir a OC Normal Autorizada]
K --> M
L --> M

M --> N[Recepcion Formal]
N --> O[Registrar Factura]

O --> P{Credito o Contado}
P -->|Credito| Q[Programar pago<br/>CxP]
P -->|Contado| R[Pagar]

Q --> S[Cerrar OC<br/>(cuando pago esta programado)]
R --> S

%% FLUJO NORMAL
B -->|NO| T[Validacion tecnica]
T --> U[Proceso de Cotizaciones]
U --> V[Generar OC Normal]

V --> W{Monto}
W -->|<=20000| X[Autoriza Jefe de area]
W -->|20001-50000| Y[Autoriza Director de area]
W -->|>50000| Z[Autoriza Director General]

X --> AA[Enviar OC al proveedor]
Y --> AA
Z --> AA

AA --> AB[Recepcion Formal]
AB --> AC[Registrar Factura]

AC --> AD{Credito o Contado}
AD -->|Credito| AE[Programar pago<br/>CxP]
AD -->|Contado| AF[Pagar]

AE --> AG[Cerrar OC<br/>(cuando pago esta programado)]
AF --> AG
```

---

## Notas
- En compras a crédito, la OC se **cierra cuando el pago está PROGRAMADO**, no cuando se paga.
- La factura queda en módulo de **CxP** hasta liquidación.
- El BPMN es 100% compatible con GitHub.
