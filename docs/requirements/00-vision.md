# Visión del Proyecto — Aplicación de Control Financiero Personal

## 1) Propósito
Construir una aplicación web de **control financiero personal** que permita a cada usuario **registrar, organizar y analizar** sus finanzas (ingresos, gastos, presupuestos y otros movimientos), con el objetivo de **mejorar la toma de decisiones** y fomentar hábitos financieros saludables.

La solución debe ser **simple para uso diario**, pero lo suficientemente flexible para adaptarse a distintos estilos de vida (gastos fijos/variables, metas, categorías personalizadas, múltiples fuentes de ingreso, etc.).

---

## 2) Problema a resolver
Muchas personas llevan su control en notas o en hojas de cálculo dispersas, lo que provoca:
- Falta de consistencia al registrar movimientos.
- Dificultad para visualizar “en qué se va el dinero”.
- Presupuestos que no se cumplen por no tener alertas o seguimiento.
- Duplicidad de información en múltiples herramientas (apps + Excel).
- Reportes y resúmenes manuales que consumen tiempo.

---

## 3) Visión (en una frase)
Una aplicación que permita a cualquier persona **registrar sus finanzas en segundos** y tener una vista clara de su situación mediante **presupuestos, categorías y reportes**, con opción de **sincronización con una hoja de cálculo personal en Google Drive** para mayor portabilidad y respaldo.

---

## 4) Público objetivo (usuarios)
- Personas que quieren iniciar un hábito de control financiero personal.
- Usuarios que hoy usan Excel/Google Sheets, pero desean una experiencia más guiada.
- Usuarios que quieren mantener un “respaldo” o “vista” de sus datos en Google Drive.
- Estudiantes, empleados, freelancers o cualquier persona con ingresos/gastos recurrentes.

---

## 5) Objetivos del producto
### Objetivos principales
- **Registro rápido** de ingresos y gastos (fecha, monto, categoría, descripción, método de pago, etc.).
- **Clasificación** por categorías y etiquetas para análisis y reportes.
- **Presupuestos** por período (mensual/semanal) y por categoría.
- **Balance y resumen** por período: ingresos vs gastos, ahorro estimado, top categorías, etc.
- **Exportación/Sincronización** con una hoja de cálculo del usuario (Google Sheets en Google Drive).

### Objetivos secundarios (deseables)
- Metas de ahorro (ej. “viaje”, “emergencia”).
- Recordatorios o alertas cuando se alcance cierto % de presupuesto.
- Panel de tendencias (mes a mes).
- Importación desde CSV/Sheet (si aplica).

---

## 6) Alcance inicial (MVP)
El MVP se enfoca en entregar valor rápido con funciones base y una integración mínima con Google:

### Funcionalidades MVP
1. **Autenticación con Google (OAuth)** para acceder de forma segura a la cuenta del usuario.
2. **CRUD de movimientos**:
   - Ingresos
   - Gastos
   - Campos mínimos: fecha, monto, tipo (ingreso/gasto), categoría, nota.
3. **Categorías básicas** (predefinidas) y opción de personalización simple (si aplica).
4. **Presupuesto mensual**:
   - Presupuesto total mensual y/o por categoría (definir en alcance detallado).
5. **Dashboard básico**:
   - Total de ingresos (mes)
   - Total de gastos (mes)
   - Balance del mes
   - Top categorías de gasto
6. **Google Sheets (1 por usuario)**:
   - La app crea o asocia un Spreadsheet por usuario
   - Escritura de movimientos en una hoja (tab) dedicada
   - Lectura para validar/mostrar (si aplica)
   - La hoja queda disponible en Drive del usuario

---

## 7) Fuera de alcance (por ahora)
- Conexión automática a bancos o tarjetas (open banking).
- Multi-moneda avanzada y conversiones en tiempo real.
- Compartición de finanzas con múltiples miembros (familia/pareja) como co-editores.
- Automatizaciones complejas (reglas inteligentes por proveedor/merchant).
- Facturación, contabilidad formal o soporte fiscal.

---

## 8) Principios de diseño y experiencia (UX)
- **Fricción mínima**: registrar un gasto/ingreso en pocos pasos.
- **Claridad**: reportes simples y entendibles.
- **Consistencia**: categorías y periodos bien definidos.
- **Confianza**: el usuario entiende qué datos se guardan y cómo se usan.
- **Portabilidad**: los datos pueden vivir y verse también en Google Sheets del usuario.

---

## 9) Suposiciones y decisiones clave
- La **fuente de verdad** de los datos será **MongoDB**.
- Cada usuario tendrá **su propio Google Sheet** para sincronización/visualización.
- La autenticación e integración con Google será vía **OAuth de usuarios**.
- Se buscará pedir **scopes mínimos necesarios** para operar con Drive/Sheets.

---

## 10) Métricas de éxito (indicativas)
- % de usuarios que registran al menos 1 movimiento al día/semana.
- Retención (usuarios que vuelven semanalmente).
- Movimientos registrados por usuario por mes.
- % de usuarios que activan y usan sincronización con Google Sheets.
- Tiempo promedio para registrar un movimiento (objetivo: muy bajo).

---

## 11) Entregables del repositorio
- `frontend/`: interfaz de usuario.
- `backend/`: API Node.js/Express con MongoDB + integración Google.
- `docs/`: documentación viva (requisitos, arquitectura, contratos API, ADRs, runbooks).

---

## 12) Próximos pasos recomendados
- Definir el **modelo de datos** (movimientos, categorías, presupuestos, metas).
- Establecer el **contrato API** inicial (`docs/architecture/api-contracts/openapi.yaml`).
- Definir reglas de sincronización con Google Sheets:
  - ¿Cuándo se escribe? (al crear/editar movimiento)
  - ¿Se permite edición desde Sheet hacia la app? (fase futura o no)
- Aterrizar el backlog de user stories del MVP (`docs/requirements/02-user-stories.md`).