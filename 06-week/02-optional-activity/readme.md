# Entrega Semana 6: Modelamiento de Datos (ERD, NoSQL y Normalización)

## 1. Diseño del Modelo Entidad-Relación (ERD)

**Caso elegido:** Sistema de Gestión de Pedidos e Inventario para Comercio Electrónico (*E-Commerce*).

### Descripción de Entidades y Campos

1. **`Clientes`**
* `cliente_id` (PK, INT, Auto-increment)
* `nombre` (VARCHAR)
* `email` (VARCHAR, Unique)
* `telefono` (VARCHAR)


2. **`Productos`**
* `producto_id` (PK, INT, Auto-increment)
* `nombre_producto` (VARCHAR)
* `precio_unitario` (DECIMAL)
* `stock` (INT)


3. **`Pedidos`**
* `pedido_id` (PK, INT, Auto-increment)
* `fecha_pedido` (DATETIME)
* `estado` (VARCHAR)
* `cliente_id` (FK, INT) $\rightarrow$ *Relación 1:N con Clientes*


4. **`Detalle_Pedidos`** *(Tabla intermedia para resolver la relación N:M entre Pedidos y Productos)*
* `detalle_id` (PK, INT, Auto-increment)
* `pedido_id` (FK, INT) $\rightarrow$ *Relación 1:N con Pedidos*
* `producto_id` (FK, INT) $\rightarrow$ *Relación 1:N con Productos*
* `cantidad` (INT)
* `precio_historico` (DECIMAL)



---

### Diagrama del Modelo ERD

```
  +------------------+         +--------------------+         +-----------------------+         +-------------------+
  |     Clientes     |         |      Pedidos       |         |   Detalle_Pedidos     |         |     Productos     |
  +------------------+         +--------------------+         +-----------------------+         +-------------------+
  | PK  cliente_id   |1       N| PK  pedido_id      |1       N| PK  detalle_id        |N       1| PK  producto_id   |
  |     nombre       |---------| FK  cliente_id     |---------| FK  pedido_id         |---------|     nombre_producto|
  |     email        |         |     fecha_pedido   |         | FK  producto_id       |         |     precio_unitario|
  |     telefono     |         |     estado         |         |     cantidad          |         |     stock         |
  +------------------+         +--------------------+         |     precio_historico  |         +-------------------+
                                                              +-----------------------+

```

* **Relación Clientes $\rightarrow$ Pedidos:** Un cliente puede realizar múltiples pedidos ($1:N$).
* **Relación Pedidos $\leftrightarrow$ Productos:** Un pedido puede contener varios productos y un producto puede figurar en varios pedidos ($N:M$). Se resuelve mediante la tabla intermedia `Detalle_Pedidos`.

---

## 2. Justificación: Enfoque Relacional (SQL) vs. NoSQL

**Decisión:** Se selecciona un **enfoque Relacional (SQL)** (ej. PostgreSQL o MySQL).

**Justificación:**

1. **Consistencia Transaccional (ACID):** En un sistema de ventas e inventario, operaciones como procesar un pago y descontar stock deben ocurrir de forma atómica. Si falla un paso, todo debe revertirse para evitar inconsistencias de inventario.
2. **Estructura Tabular Definida:** Las entidades (`Clientes`, `Productos`, `Pedidos`) tienen atributos fijos y relaciones claras entre sí.
3. **Integridad Referencial:** Las claves foráneas (`FK`) garantizan que no existan pedidos huérfanos sin un cliente válido o productos inexistentes en un pedido.

---

## 3. Aplicación de Normalización

Se aplicaron las reglas de normalización hasta la **Tercera Forma Normal (3FN)**:

* **Primera Forma Normal (1FN):** Todos los valores en las columnas son atómicos (un solo dato por celda). Se evita almacenar listas de productos separadas por comas dentro de la tabla `Pedidos`.
* **Segunda Forma Normal (2FN):** Se eliminó la dependencia parcial creando la tabla intermedia `Detalle_Pedidos`. Los atributos `cantidad` y `precio_historico` dependen de la combinación específica de un `pedido_id` y un `producto_id`.
* **Tercera Forma Normal (3FN):** Se eliminaron las dependencias transitivas. Los datos personales del cliente (`nombre`, `email`) residen exclusivamente en la tabla `Clientes` y no se repiten en cada pedido realizado.

**¿Qué se evitó repetir?**

* **Redundancia de datos del cliente:** Evita duplicar el nombre y teléfono del cliente en cada compra.
* **Redundancia de datos del producto:** Evita repetir la descripción o precio base del producto en cada ítem vendido.
* **Anomalías de actualización/eliminación:** Si un cliente cambia su teléfono, solo se actualiza un registro en `Clientes` en lugar de actualizar decenas de filas de historial de pedidos.