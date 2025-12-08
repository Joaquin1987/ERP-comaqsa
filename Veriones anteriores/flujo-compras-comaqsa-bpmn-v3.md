# Flujo de Compras COMAQSA – BPMN (Mermaid) – V3 (GitHub compatible)

Reglas clave integradas en este diagrama:

- En compras a **credito**, la OC se **cierra cuando el pago esta programado**.
- En compras **de contado**, la OC se **cierra cuando el pago ya se ejecuto**.

---

```mermaid
flowchart TD

A[Requisicion creada] --> B{Critico}

%% FLUJO CRITICO
B -->|SI equipo parado| C[Generar OC preliminar]
C --> D[Enviar OC preliminar al proveedor]
D --> E[Recepcion preliminar]
E --> F[Instalar pieza]
F --> G[Completar cotizaciones]
G --> H[Autorizacion retroactiva]

H --> I{Monto}
I -->|<= 20000| J[Autoriza jefe de area]
I -->|20001 - 50000| K[Autoriza director de area]
I -->|> 50000| L[Autoriza director general]

J --> M[Convertir a OC normal]
K --> M
L --> M

M --> N[Recepcion formal]
N --> O[Registrar factura]

O --> P{Credito o contado}
P -->|Credito| Q[Programar pago]
P -->|Contado| R[Pagar]

Q --> S[Cerrar OC cuando pago esta programado]
R --> T[Cerrar OC cuando pago esta ejecutado]

%% FLUJO NORMAL
B -->|NO critico| U[Validacion tecnica]
U --> V[Proceso de cotizaciones]
V --> W[Generar OC normal]

W --> X{Monto}
X -->|<= 20000| Y[Autoriza jefe de area]
X -->|20001 - 50000| Z[Autoriza director de area]
X -->|> 50000| AA[Autoriza director general]

Y --> AB[Enviar OC al proveedor]
Z --> AB
AA --> AB

AB --> AC[Recepcion formal]
AC --> AD[Registrar factura]

AD --> AE{Credito o contado}
AE -->|Credito| AF[Programar pago]
AE -->|Contado| AG[Pagar]

AF --> AH[Cerrar OC cuando pago esta programado]
AG --> AI[Cerrar OC cuando pago esta ejecutado]
```

---

## Notas

