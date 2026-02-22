# 📄 Requerimientos del Sistema

## 1. Lista general de requerimientos

El sistema de Bankify tiene los siguientes requerimientos (descripción a alto nivel):

### 1.1 Requerimientos funcionales

El sistema de Bankify debe tener la capacidad de:

1. Crear, actualizar, activar y desactivar cuentas bancarias.
2. Generar reportes para la declaracion de renta del cliente.
3. Generar reporte tributario de declaración de renta de todas las cuentas para la DIAN por parte del gerente financiero.
4. Consultar el estado del saldo.
5. Realizar despositos y retiros de las cuentas bancarias.

### 1.2 Requerimientos no funcionales

El sistema de Bankify debe tener:

1. Los números de cuenta deben tener exactamente 10 digitos.
2. Las cuentas deben pertenecer a un banco para ser validas.
3. El sistema debe garantizar que los datos financieros no puedan ser modificados sin autorización.
4. Toda la información sensible debe almacenarse encriptada.
5. La interfaz debe ser usable por un usuario sin entrenamiento en menos de 10 minutos.

## 2. Diagramas de caso de uso

### 2.1 Requerimiento Funcional 1

| Campo | Descripción |
|------|-------------|
| **ID** | RF-01 |
| **Nombre del requerimiento** | Módulo de gestión de cuentas bancarias |
| **Descripción** | El sistema permite crear, actualizar, activar y desactivar cuentas bancarias. |
| **Precondiciones** | El banco existe en el sistema; el actor está autenticado y autorizado. |
| **Actor** | `Customer` (titular), `BankEmployee`, `Admin`, `System` |
| **Flujo principal** | 1. El actor solicita crear/actualizar/activar/desactivar una cuenta con datos válidos. 2. El sistema valida formato y pertenencia al banco. 3. El sistema crea/actualiza el registro `account` y registra auditoría. 4. El sistema devuelve confirmación al actor. |
| **Flujos alternos** | A1: Validación falla → mostrar errores y abortar. A2: Número de cuenta duplicado → solicitar otro número. A3: Usuario no autorizado → rechazar acción y registrar intento. |
| **Diagrama de caso de uso** | *imagen y link* |
| **Criterios de aceptación / Poscondiciones** | Cuenta creada/actualizada; `account_number` único y con 10 dígitos; estado correcto; auditoría registrada. |


### 2.2 Requerimiento Funcional 2

| Campo | Descripción |
|------|-------------|
| **ID** | RF-02 |
| **Nombre del requerimiento** | Generar reporte tributario para la DIAN (consolidado) |
| **Descripción** | Permitir al gerente financiero generar reportes tributarios consolidados para la DIAN, agregando datos de múltiples cuentas y clientes según el periodo fiscal. |
| **Precondiciones** | Usuario autenticado con rol `FinancialManager` o `Admin`; existen transacciones y datos de cuentas para el periodo solicitado. |
| **Actor** | `FinancialManager`, `Admin` |
| **Flujo principal** | 1. El actor solicita generar un reporte indicando periodo y filtros. 2. El sistema valida permisos, consolida movimientos y cálculos fiscales. 3. El sistema genera el `tax_report`, presenta vista previa y permite exportar en el formato requerido por la DIAN. |
| **Flujos alternos** | A1: Datos incompletos → mostrar advertencia y permitir generar informe parcial o cancelar. A2: Formato de exportación no soportado → ofrecer formatos alternativos (CSV/JSON/PDF). |
| **Diagrama de caso de uso** | *imagen y link* |
| **Criterios de aceptación / Poscondiciones** | Reporte consolidado generado y disponible para exportación; registro de la operación en auditoría; cumplimiento de reglas de privacidad y validación de datos. |

### 2.3 Requerimiento Funcional 3

| Campo | Descripción |
|------|-------------|
| **ID** | RF-03 |
| **Nombre del requerimiento** | Consultar estado del saldo |
| **Descripción** | Permitir que usuarios autorizados (titulares o personal autorizado) consulten el saldo actual de una o varias cuentas bancarias. |
| **Precondiciones** | Cuenta existente; actor autenticado y con permisos para la(s) cuenta(s) consultada(s). |
| **Actor** | `Customer` (titular), `Teller`, `Auditor` |
| **Flujo principal** | 1. El actor solicita la consulta indicando la cuenta. 2. El sistema valida permisos y estado de la cuenta. 3. El sistema devuelve el saldo actual (desde `account.balance`) y registra la consulta en auditoría si aplica. |
| **Flujos alternos** | A1: Cuenta inactiva/cerrada → informar al actor y mostrar estado. A2: Permisos insuficientes → denegar acceso y registrar intento. |
| **Diagrama de caso de uso** | *imagen y link* |
| **Criterios de aceptación / Poscondiciones** | Se muestra el saldo correcto y actualizado; auditoría de la consulta registrada si la política lo requiere. |

## 3. Preguntas

---

### Respuestas a las preguntas (a–d)

a) ¿Identifica algún requerimiento que deba detallarse más? ¿cuál(es)?

- **RF-02 (reportes por cliente):** especificar formato de salida (PDF/CSV/JSON), campos obligatorios, filtros, periodo, frecuencia y requisitos legales para presentación.
- **RF-05 (depósitos y retiros):** definir límites, reglas de autorización, manejo de sobregiros, comisiones y pautas de concurrencia/consistencia de saldos.
- **No funcionales de seguridad/encriptación:** detallar qué datos se encriptan, dónde (aplicación o BD), gestión de claves y requisitos de auditoría.
- **Regla del número de cuenta (10 dígitos):** aclarar si permite ceros a la izquierda, si es generado por el sistema y políticas de validación.

b) ¿Existen requerimientos que se contradigan entre sí? ¿cuál(es)?

- **Cifrado total vs. generación de reportes:** cifrar todos los campos sin mecanismos de desencriptado controlado dificulta agregaciones y reportes consolidados.
- **"Datos no modificables sin autorización" vs. operaciones financieras:** es necesario especificar qué roles o procesos pueden realizar ajustes y cómo quedan registrados en auditoría.
- **"La cuenta debe pertenecer a un banco" vs. flujo de creación:** si no se define quién crea/valida bancos, la creación de cuentas puede verse bloqueada; deben definirse precondiciones claras.

c) Si tuviera que dar una prioridad, ¿cuáles 2 implementar primero?

1. **RF-01 (gestión de cuentas)** — fundacional: sin cuentas no hay sistema operativo.
2. **RF-05 (depósitos y retiros)** — operativo: permite mover dinero y validar saldos.

d) ¿Existe algún requerimiento que no debería realizarse?

- No eliminar ninguno, pero **posponer** implementaciones complejas hasta iteraciones posteriores: la exportación completa a DIAN (RF-03) y cifrado avanzado por campo, hasta definir formatos legales y política de claves.

## 4. Mokup de la interfaz
https://www.figma.com/design/bXwg9GOvW6O4xLVcchuowc/mukup-bankfy?node-id=0-1&m=dev&t=kj2MQR6OOyyevAiP-1
