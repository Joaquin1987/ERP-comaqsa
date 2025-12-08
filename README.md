# 🧭 Módulo de Compras — COMAQSA  
Documentación Oficial · Procesos · Flujos · Reglas de Operación

Este repositorio contiene la documentación oficial del **Módulo de Compras del ERP COMAQSA**, incluyendo procesos normalizados, reglas de negocio, criterios operativos y lineamientos técnicos para desarrollo y mantenimiento del sistema.

Su propósito es servir como:

- 🧱 Base documental para operación  
- ⚙️ Referencia técnica para desarrollo  
- 📚 Fuente única de verdad del proceso de compras  
- 🤖 Complemento del GPT especializado  

---

# 📘 Contenido Principal del Repositorio

## **Proceso Unificado de Compras COMAQSA**

El documento central del repositorio.  
Integra y normaliza:

- El proceso general de compras  
- Las reglas de negocio del sistema  
- La lógica de Taller y Obra  
- El modelo económico basado en PU + saldo  
- Las particularidades de las compras críticas  
- Los candados oficiales del ERP  
- La estructura que rige los 12 flujos oficiales  
- La conciliación tripartita como único cierre válido  

📄 Archivo principal:  
`/docs/proceso-unificado-compras-comaqsa.md`

---

# 🧩 Estructura del Módulo de Compras

El sistema se basa en 4 flujos maestros:

1. **Normal + Crédito**  
2. **Normal + Contado**  
3. **Crítico + Crédito**  
4. **Crítico + Contado**

Cada uno se divide en 12 flujos completos (Taller / Obra + Con precio / Sin precio).

Todos siguen principios clave:

- OC normal vs OC preliminar  
- Recepción formal vs preliminar  
- Validaciones de cotizaciones  
- Validación económica (montos o PU + saldo)  
- Autorización previa o retroactiva  
- Conciliación tripartita obligatoria  

---

# 🤖 Asistente Inteligente (GPT Oficial)

Para consultar reglas, flujos, validaciones, casos especiales o apoyo técnico en tiempo real, utiliza el **GPT oficial del Módulo de Compras COMAQSA**:

👉 **https://chatgpt.com/g/g-692f515c14608191ac5639d98c71f346-erp-compras**

Este GPT está configurado para:

- Explicar cualquier flujo del módulo  
- Resolver escenarios reales de operación  
- Guiar a desarrolladores (especialmente Brandon)  
- Detectar inconsistencias en propuestas de mejora  
- Validar reglas con base en el Proceso Unificado  
- Servir como manual viviente del sistema  

---

# 🎯 Objetivo del repositorio

### **1. Para Operación (Alonzo)**
- Garantizar coherencia del proceso  
- Auditar reglas y flujos  
- Facilitar capacitación y alineación interna  

### **2. Para Desarrollo (Brandon)**
- Implementar correctamente el módulo de compras  
- Consultar lógica de estados y transiciones  
- Acceder a reglas claras y no ambiguas  
- Desarrollar validaciones, triggers y candados  

### **3. Para el GPT**
- Mantener consistencia documental  
- Servir como base para respuestas técnicas  

---

# 🛠️ Cómo usar este repositorio

1. **Leer primero el Proceso Unificado**  
2. Consultar los flujos específicos cuando se requieran detalles  
3. Usar el GPT como soporte inteligente  
4. Validar todo cambio con el Protocolo de Revisión  
5. Mantener consistencia entre flujos, diagramas y reglas  

---

# 🚀 Contribución

Las actualizaciones deben:

1. Ser claras y documentadas  
2. Estar alineadas al Proceso Unificado  
3. Tener aprobación operativa  
4. Ser revisadas por el GPT o por el área correspondiente  
5. Incluir mensaje claro en el pull request  

---

# 🔒 Principios Fundamentales del Sistema

- **No existen cierres por pago**  
- **Toda compra cierra solo mediante conciliación tripartita**  
- **OC preliminar solo en compras críticas**  
- **Recepción formal solo con OC normal**  
- **Crítico permite avanzar sin completar cotizaciones**  
- **Tiempo > Precio en compras críticas**  
- **Obra valida por PU + saldo; Taller valida por montos**  

---

# 📞 Contacto

- **Operación:** Alonzo  
- **Desarrollo:** Brandon  
- **Asistente GPT:** ERP Compras COMAQSA  

---

# ✔️ Fin del README
