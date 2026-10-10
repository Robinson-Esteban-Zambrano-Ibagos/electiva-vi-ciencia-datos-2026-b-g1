Markdown
# Entrega Semana 07 - Consultas SQL y pandas
**Asignatura:** Ciencia de Datos  
**Unidad:** Unidad 2 · Modelamiento, transformación y conexión de datos  
**Periodo:** 2026-B  

---

## Dataset de Referencia

Para responder a las consultas de esta actividad se utiliza un esquema relacional básico compuesto por dos tablas:

* **`clientes`**: `cliente_id`, `nombre`, `ciudad`
* **`ventas`**: `venta_id`, `cliente_id`, `monto`, `fecha`

---

## 1. Tres Consultas SQL

### Consulta 1: Filtro con `WHERE`
```sql
SELECT venta_id, cliente_id, monto, fecha
FROM ventas
WHERE monto > 100;
Consulta 2: Relación de tablas con JOIN
SQL
SELECT v.venta_id, c.nombre AS cliente, v.monto, c.ciudad
FROM ventas v
INNER JOIN clientes c ON v.cliente_id = c.cliente_id;
Consulta 3: Agregación con GROUP BY
SQL
SELECT cliente_id, COUNT(venta_id) AS total_compras, SUM(monto) AS total_monto
FROM ventas
GROUP BY cliente_id;
2. Equivalente de GROUP BY en pandas
Python
import pandas as pd

# Reproducción de la Consulta 3 (GROUP BY) en pandas
df_resultado = (
    df_ventas.groupby("cliente_id")
    .agg(total_compras=("venta_id", "count"), total_monto=("monto", "sum"))
    .reset_index()
)

print(df_resultado)
3. Explicación de cada consulta
Consulta 1 (WHERE): Filtra la tabla ventas para extraer únicamente las transacciones individuales en las que el valor de la columna monto supera los $100. Responde a la pregunta: ¿Cuáles fueron las compras superiores a $100?

Consulta 2 (JOIN): Combina la tabla ventas con la tabla clientes vinculando la clave primaria/foránea cliente_id. Responde a la pregunta: ¿Qué cliente y de qué ciudad realizó cada una de las ventas registradas?

Consulta 3 (GROUP BY en SQL) y su equivalente en pandas: Agrupa todos los registros por el identificador del cliente (cliente_id), calculando el conteo total de transacciones y la suma del monto acumulado. Responde a la pregunta: ¿Cuántas compras ha realizado cada cliente en total y cuánto dinero ha gastado?
