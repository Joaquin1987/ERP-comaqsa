flowchart TD

subgraph F1["Flujo #1 — NORMAL + CRÉDITO — TALLER"]
direction TB

R1[1. Requisición\nActor: Solicitante\nEstado: Pendiente]
R2{2. Validación Técnica\nActor: Jefe de área\n¿Es crítica?}
Rcrit[Se va al flujo crítico]
R3[3. Cotizaciones\n≤5k=1, 5–15k=2, >15k=3]
R4[4. Autorización por montos\n≤20k Jefe área; 20–50k Director; >50k Dir. Gral.]
R5[5. OC Normal\nPrecio final definido]
R6[6. Entrega del proveedor]
R7[7. Recepción formal\nValidación de cantidad/calidad]
R8[8. Factura\nDebe coincidir con OC y recepción]
R9[9. Programación de Pago (CxP)]
R10[10. Conciliación tripartita\nOC vs Recepción vs Factura vs CxP]
R11[11. Cierre de OC\nSolo con conciliación completa]

end

R1 --> R2
R2 -->|No crítica| R3
R2 -->|Crítica| Rcrit
R3 --> R4
R4 --> R5
R5 --> R6
R6 --> R7
R7 --> R8
R8 --> R9
R9 --> R10
R10 --> R11
