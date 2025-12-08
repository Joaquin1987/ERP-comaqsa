flowchart TD

%% ======================================================
%% FLUJO #1 — NORMAL + CRÉDITO — TALLER
%% ======================================================

subgraph F1["Flujo #1 — NORMAL + CRÉDITO — TALLER"]
direction TB

R1[1. REQUISICIÓN
Actor: Usuario solicitante
Estado: Pendiente
Output: Requisición creada]

R2{2. VALIDACIÓN TÉCNICA (VT)
Actor: Jefe de área
Estado: Requisición validada
¿Se marca como CRÍTICA?}

Rcrit[Salir a flujo
CRÍTICO – TALLER
(no cubierto aquí)]

R3[3. COTIZACIONES SEGÚN MONTO
Estado: En cotización
Reglas:
- ≤ $5,000 → 1 cotización
- $5,001–$15,000 → 2
- > $15,000 → 3 + comparativo
Output: Cotizaciones cargadas]

R4[4. AUTORIZACIÓN POR MONTOS
Estado: En autorización
Rangos Taller:
- ≤ $20,000 → Jefe de Área
- $20,001–$50,000 → Director
- > $50,000 → Director Gral.
Candado:
No hay OC sin esta autorización
Output: Compra autorizada]

R5[5. OC NORMAL
Estado: OC normal emitida
Características:
- Precio final definido
- Documento formal/contractual
- Cambios de precio requieren
  nueva autorización
Output: OC generada]

R6[6. ENTREGA
Estado: En recepción
Acciones:
- Proveedor entrega bienes/servicio
Candado:
- No hay entrega antes de la OC normal
Output: Material/servicio entregado]

R7[7. RECEPCIÓN FORMAL
Estado: Recepción formal registrada
Requisitos:
- OC normal vigente
- Precio final
- Entrega coincidente
Validaciones:
- Cantidad, calidad, especificación
Output: Recepción concluida]

R8[8. FACTURA
Estado: En espera de conciliación
Reglas:
- Debe coincidir con OC y recepción
- Diferencias detienen el flujo
  hasta corregir/justificar
Output: Factura aceptada]

R9[9. PROGRAMAR PAGO (CxP)
Estado: Documento por pagar generado
Acciones:
- Crear CxP con base en la factura
- Agendar según días de crédito
Candado:
- No se programa pago sin factura
  válida ligada a OC y recepción
Output: CxP registrada y programada]

R10[10. CONCILIACIÓN TRIPARTITA
Estado: En conciliación
Debe coincidir:
- OC vs Recepción
- OC vs Factura
- Factura vs CxP
Candado maestro:
- Ni la OC, ni la recepción, ni la
  programación de pago cierran el flujo]

R11[11. CIERRE DE LA OC
Estado: Cerrada
Condición:
- Solo tras conciliación completa
(no existe "cierre al pagar")]

end

%% FLUJO DE TRANSICIONES

R1 --> R2
R2 -->|No crítica| R3
R2 -->|Marcada crítica| Rcrit
R3 --> R4
R4 --> R5
R5 --> R6
R6 --> R7
R7 --> R8
R8 --> R9
R9 --> R10
R10 --> R11
