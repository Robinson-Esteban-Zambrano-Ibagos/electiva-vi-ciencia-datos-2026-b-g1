# Entrega Semana 8 · Diseña un pipeline ETL 
**Asignatura:** Ciencia de Datos  
**Unidad:** Unidad 2 · Modelamiento, transformación y conexión de datos  

---

## 1. Diagrama del Pipeline ETL

```text
[ Fuentes de Datos ]
       │
       ├─ API Pública (JSON / REST)
       └─ Base de Datos Transaccional (PostgreSQL)
       │
       ▼
[ 1. Extraer (Extraction) ]
       │ Herramienta: Apache Airflow + Python (requests / psycopg2)
       ▼
[ 2. Transformar (Transformation) ]
       │ Herramienta: Python (Pandas / PySpark)
       ▼
[ 3. Cargar (Loading) ]
       │ Herramienta: Snowflake / PostgreSQL (Data Warehouse)
       ▼
[ 4. BI (Business Intelligence) ]
       │ Herramienta: Power BI / Tableau

```

### Herramientas por etapa

* **Fuentes:** API pública y base de datos transaccional PostgreSQL.
* **Extraer:** Apache Airflow y scripts de Python (librerías `requests` y `psycopg2`).
* **Transformar:** Python utilizando `Pandas` (para volúmenes estándar) o `PySpark` (para grandes volúmenes).
* **Cargar:** Snowflake o PostgreSQL actuando como Data Warehouse central.
* **BI:** Power BI o Tableau para la generación de reportes y tableros interactivos.

---

## 2. Justificación Batch / Streaming

* **Batch (En Lote):**
* **Ubicación en el pipeline:** Extracción desde PostgreSQL, transformaciones complejas en Pandas/PySpark y carga final hacia el Data Warehouse y Power BI.
* **Justificación:** Los datos para reportes estratégicos e industriales no requieren actualizarse segundo a segundo. Ejecutar el proceso de manera programada (por ejemplo, una vez al día durante la noche) optimiza el uso de recursos computacionales y reduce costos operativos.


* **Streaming (En Tiempo Real):**
* **Ubicación en el pipeline:** Consumo continuo de eventos desde la API pública hacia el sistema de ingesta.
* **Justificación:** Se utiliza exclusivamente para métricas que requieren monitoreo inmediato, alertas en tiempo real o análisis de eventos al instante.



---

## 3. Consumo de API Pública en Python

```python
import requests

# Consumo de API pública (JSONPlaceholder)
API_URL = "[https://jsonplaceholder.typicode.com/posts](https://jsonplaceholder.typicode.com/posts)"

response = requests.get(API_URL)
data = response.json()

# Mostrar 3 registros
for registro in data[:3]:
    print(f"ID: {registro['id']}")
    print(f"Título: {registro['title']}")
    print(f"Cuerpo: {registro['body']}")
    print("-" * 40)

```

```

```