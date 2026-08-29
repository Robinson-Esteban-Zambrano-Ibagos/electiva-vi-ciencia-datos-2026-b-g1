# Actividad calificable · Corte 1

## Diagnóstico de datos de un proceso industrial

**Programa:** Ingeniería Mecatrónica
**Asignatura:** Electiva VI – Ciencia de Datos
**Corte:** 1
**Semana:** 4
**Tema:** Diagnóstico de datos para mantenimiento predictivo de una máquina industrial
## 1. Problema y pregunta de datos

### 1.1 Problema

En los procesos industriales, las máquinas y equipos son fundamentales para garantizar la continuidad y eficiencia de la producción. Sin embargo, las fallas inesperadas pueden ocasionar paradas no programadas, retrasos en la producción, aumento de los costos de mantenimiento y pérdidas económicas para la empresa.

Una máquina industrial genera continuamente información relacionada con su funcionamiento mediante sensores, sistemas de control y registros operativos. Variables como la temperatura, vibración, presión, velocidad y consumo de energía pueden proporcionar información importante sobre el estado del equipo.

El problema se presenta cuando estos datos no son recopilados, organizados y analizados de manera adecuada. En este escenario, una falla puede ser detectada únicamente después de que el equipo presenta un daño o deja de funcionar correctamente.

Por esta razón, se propone utilizar técnicas de ciencia de datos para analizar el comportamiento de la máquina, identificar patrones relacionados con condiciones anormales y anticipar posibles fallas. Esto permitiría apoyar la planificación del mantenimiento y reducir la probabilidad de paradas inesperadas.

### 1.2 Pregunta de datos

**¿Cómo podemos utilizar los datos generados por una máquina industrial para identificar patrones de funcionamiento, detectar condiciones anormales y anticipar posibles fallas con el propósito de mejorar las decisiones de mantenimiento?**

### 1.3 Objetivo

El objetivo es analizar los datos generados durante la operación de una máquina industrial para identificar patrones y condiciones asociadas con posibles fallas, proporcionando información que permita tomar mejores decisiones de mantenimiento y contribuir a la reducción de paradas no programadas.



# 2. Inventario de datos

Para realizar el diagnóstico del proceso se requiere recopilar información proveniente de diferentes fuentes. La siguiente tabla presenta un inventario de datos que podrían utilizarse para analizar el comportamiento de la máquina.

| Nº | Fuente o campo de datos    | Descripción                                                            | Tipo de dato     | Utilidad                                                          |
| -- | -------------------------- | ---------------------------------------------------------------------- | ---------------- | ----------------------------------------------------------------- |
| 1  | Temperatura                | Temperatura registrada en el motor o en componentes de la máquina      | Estructurado     | Identificar posibles sobrecalentamientos                          |
| 2  | Vibración                  | Nivel de vibración producido durante el funcionamiento                 | Estructurado     | Detectar desbalanceos, desgaste o problemas mecánicos             |
| 3  | Presión                    | Presión registrada durante el proceso de operación                     | Estructurado     | Identificar condiciones anormales de funcionamiento               |
| 4  | Velocidad                  | Velocidad de operación de la máquina                                   | Estructurado     | Comparar el comportamiento del equipo bajo diferentes condiciones |
| 5  | Consumo de energía         | Cantidad de energía utilizada durante la operación                     | Estructurado     | Detectar cambios anormales en el consumo                          |
| 6  | Fecha y hora               | Momento en el que se registra cada medición                            | Estructurado     | Analizar la evolución de las variables a través del tiempo        |
| 7  | Registros del PLC          | Estados, alarmas y eventos generados por el sistema de control         | Semiestructurado | Identificar eventos y condiciones de operación                    |
| 8  | Historial de mantenimiento | Reparaciones, cambios de componentes y mantenimientos realizados       | Estructurado     | Relacionar intervenciones anteriores con fallas posteriores       |
| 9  | Fotografías de componentes | Imágenes de piezas o componentes antes y después de una falla          | No estructurado  | Apoyar la identificación visual de daños                          |
| 10 | Videos de inspección       | Grabaciones realizadas durante inspecciones o revisiones de la máquina | No estructurado  | Analizar visualmente el estado y comportamiento de componentes    |

### 2.1 Clasificación de los datos

**Datos estructurados:**
Son datos que pueden organizarse fácilmente en filas y columnas dentro de una tabla. En este proyecto corresponden principalmente a las mediciones de temperatura, vibración, presión, velocidad, consumo de energía, fecha y hora, y registros históricos de mantenimiento.

**Datos semiestructurados:**
Son datos que poseen cierta organización interna, pero que no necesariamente siguen la estructura tradicional de una tabla. En este caso, los registros generados por un PLC pueden almacenarse mediante formatos como JSON, XML o registros de eventos que contienen información organizada sobre estados y alarmas.

**Datos no estructurados:**
Son datos que no presentan una estructura tabular definida. En este proyecto corresponden principalmente a fotografías y videos de inspección de los componentes de la máquina.

La integración de estos diferentes tipos de datos permitiría obtener una visión más completa del comportamiento y estado de la máquina industrial.



# 3. Tipo de analítica

Para el diagnóstico del proceso se pueden aplicar los diferentes niveles de analítica de datos: descriptiva, diagnóstica, predictiva y prescriptiva. Cada una responde a una pregunta diferente y aporta información para avanzar desde la comprensión del pasado hasta la toma de decisiones.

## 3.1 Analítica descriptiva

La analítica descriptiva permite responder:

**¿Qué ha ocurrido?**

En este proyecto se utilizaría para analizar el comportamiento histórico de la máquina. Por ejemplo, se podría determinar el número de fallas ocurridas durante un periodo, calcular la temperatura promedio, identificar los niveles máximos de vibración y conocer las horas de funcionamiento del equipo.

Los resultados podrían presentarse mediante tablas y gráficos para identificar tendencias y comportamientos generales.

## 3.2 Analítica diagnóstica

La analítica diagnóstica permite responder:

**¿Por qué ocurrió?**

Se utilizaría para analizar las relaciones entre las diferentes variables y buscar posibles causas de las fallas. Por ejemplo, se podría estudiar si los aumentos de temperatura y vibración se presentan antes de determinadas fallas mecánicas.

Este análisis permitiría identificar patrones relacionados con las condiciones de operación y los eventos de falla registrados.

## 3.3 Analítica predictiva

La analítica predictiva permite responder:

**¿Qué podría ocurrir?**

Esta será la principal estrategia analítica del proyecto. A partir de los datos históricos y actuales de la máquina, se podría desarrollar un modelo que identifique condiciones asociadas con una posible falla futura.

Por ejemplo, si en los registros históricos se observa que determinados niveles de vibración y temperatura aparecen antes de una falla, un modelo predictivo podría identificar una situación similar durante el funcionamiento actual del equipo.

## 3.4 Analítica prescriptiva

La analítica prescriptiva permite responder:

**¿Qué deberíamos hacer?**

Después de identificar una posible falla, este tipo de analítica permitiría generar recomendaciones para apoyar la toma de decisiones. Algunas acciones podrían ser programar una inspección, realizar mantenimiento preventivo, revisar un componente específico o detener temporalmente el equipo cuando exista un nivel elevado de riesgo.

## 3.5 Analítica seleccionada

La **analítica predictiva** será la principal estrategia utilizada porque el objetivo del proyecto es anticipar posibles fallas antes de que ocurran. Sin embargo, las cuatro etapas de analítica se complementan entre sí: la descriptiva permite comprender qué ocurrió, la diagnóstica ayuda a determinar por qué ocurrió, la predictiva permite estimar qué podría ocurrir y la prescriptiva ayuda a establecer qué acción debería tomarse.

---

# 4. ¿Es un caso de Big Data?

Este proyecto **puede presentar características de Big Data** cuando se recopilan grandes cantidades de información generada continuamente por sensores y se integran múltiples fuentes de datos.

Para justificarlo se utilizan las principales características conocidas como las **5 V de Big Data**.

## 4.1 Volumen

Los sensores de una máquina pueden generar grandes cantidades de mediciones durante periodos prolongados de operación. Si se analizan varias máquinas simultáneamente, el volumen de información puede aumentar considerablemente.

## 4.2 Velocidad

Los datos pueden generarse continuamente y, en algunos casos, prácticamente en tiempo real. Por ejemplo, los sensores pueden registrar variables como temperatura y vibración cada segundo o con una frecuencia aún mayor.

## 4.3 Variedad

El proyecto integra diferentes tipos de información, como valores numéricos provenientes de sensores, registros del PLC, historiales de mantenimiento, fotografías y videos de inspección.

## 4.4 Veracidad

La calidad y confiabilidad de los datos son fundamentales para obtener resultados correctos. Por esta razón, es necesario identificar sensores defectuosos, valores atípicos, datos faltantes, errores de registro y posibles inconsistencias.

## 4.5 Valor

El análisis de los datos puede generar beneficios para la empresa, como reducir las paradas inesperadas, disminuir costos de mantenimiento, mejorar la disponibilidad de los equipos y apoyar una mejor planificación de las actividades de mantenimiento.

### Conclusión sobre Big Data

El caso puede adquirir características de Big Data cuando se trabaja con múltiples máquinas, grandes volúmenes de información, datos generados a alta velocidad y diferentes fuentes y formatos. Sin embargo, una única máquina con un volumen reducido de datos no necesariamente constituye por sí sola un problema de Big Data. Por esta razón, la consideración como Big Data dependerá de la escala real del sistema de recopilación y análisis.



# 5. Ciclo de vida del proyecto de datos

El proyecto seguirá el ciclo de vida definido en la actividad:

**Pregunta → Obtener → Limpiar → Analizar → Visualizar → Decidir**

## 5.1 Pregunta

Se define el problema que se desea resolver:

**¿Cómo utilizar los datos de la máquina para detectar condiciones anormales y anticipar posibles fallas?**

Esta etapa establece el objetivo del análisis y determina qué información será necesaria.

## 5.2 Obtener

Se recopilan los datos provenientes de sensores, PLC, sistemas de monitoreo, registros históricos de mantenimiento y procesos de inspección.

## 5.3 Limpiar

Se revisa la calidad de los datos antes de realizar el análisis. En esta etapa se pueden eliminar registros duplicados, corregir errores, tratar datos faltantes, identificar valores atípicos y verificar que las mediciones sean coherentes.

## 5.4 Analizar

Se aplican técnicas estadísticas y de ciencia de datos para identificar tendencias, relaciones y patrones relacionados con las condiciones de operación y las fallas de la máquina.

## 5.5 Visualizar

Los resultados se representan mediante gráficos, tablas y paneles de información. Por ejemplo, se pueden utilizar gráficos de temperatura y vibración a través del tiempo para observar cambios en el comportamiento de la máquina.

## 5.6 Decidir

Los resultados obtenidos se utilizan para apoyar decisiones relacionadas con el mantenimiento. Por ejemplo, se puede programar una inspección, realizar mantenimiento preventivo o revisar un componente específico antes de que ocurra una falla.

### Representación del ciclo de vida


┌─────────────────────────┐
│        PREGUNTA         │
│ ¿Cuándo puede fallar    │
│      la máquina?        │
└────────────┬────────────┘
             ↓
┌─────────────────────────┐
│         OBTENER         │
│ Sensores, PLC y         │
│ registros históricos   │
└────────────┬────────────┘
             ↓
┌─────────────────────────┐
│         LIMPIAR         │
│ Corregir errores,       │
│ faltantes y duplicados  │
└────────────┬────────────┘
             ↓
┌─────────────────────────┐
│         ANALIZAR        │
│ Identificar patrones    │
│ y condiciones de falla  │
└────────────┬────────────┘
             ↓
┌─────────────────────────┐
│       VISUALIZAR        │
│ Gráficos, tablas y      │
│ resultados              │
└────────────┬────────────┘
             ↓
┌─────────────────────────┐
│         DECIDIR         │
│ Programar acciones de   │
│ mantenimiento            │
└─────────────────────────┘
```

Este ciclo es iterativo, ya que después de tomar una decisión se pueden continuar recopilando nuevos datos para evaluar los resultados, mejorar el análisis y actualizar las estrategias de mantenimiento.



## Problem & data

The industrial machine can experience unexpected failures that affect production and increase maintenance costs. The main objective is to use machine data to identify abnormal operating conditions and anticipate possible failures. The required data includes temperature, vibration, pressure, speed, energy consumption, maintenance records, and machine status. This information can be collected from sensors, PLC systems, maintenance reports, photographs, and inspection videos. The data must be cleaned and analyzed to identify patterns associated with previous failures and abnormal operating conditions. Predictive analytics will be the main approach because it can help estimate possible future failures and support maintenance planning. The results can be visualized through charts and dashboards to help technicians and managers make better decisions.


## Conclusión

El análisis de datos aplicado al mantenimiento de una máquina industrial permite transformar los datos generados durante la operación en información útil para la toma de decisiones. La integración de datos estructurados, semiestructurados y no estructurados permite obtener una visión más completa del estado y comportamiento del equipo.

La utilización de analítica descriptiva, diagnóstica, predictiva y prescriptiva permite avanzar desde la comprensión de los eventos históricos hasta la anticipación de posibles fallas y la recomendación de acciones de mantenimiento. En particular, la analítica predictiva representa una estrategia adecuada para disminuir el riesgo de fallas inesperadas y mejorar la planificación del mantenimiento.

Finalmente, el ciclo de vida del proyecto permite organizar el proceso de datos desde la definición de la pregunta hasta la toma de decisiones. De esta manera, la información obtenida de los equipos puede convertirse en conocimiento útil para mejorar la confiabilidad, disponibilidad y eficiencia de los procesos industriales.

# Referencias

1. IBM. (2025). *What is prescriptive analytics?* IBM Think.
   https://www.ibm.com/think/topics/prescriptive-analytics

2. IBM. (2025). *What is diagnostic analytics?* IBM Think.
   https://www.ibm.com/think/topics/diagnostic-analytics

3. IBM. (2026). *What is predictive analytics?* IBM Think.
   https://www.ibm.com/think/topics/predictive-analytics

4. IBM. (2025). *Structured vs. unstructured data: What’s the difference?* IBM Think.
   https://www.ibm.com/think/topics/structured-vs-unstructured-data 

5. National Institute of Standards and Technology (NIST). (2019). *NIST Big Data Interoperability Framework: Volume 1, Definitions*. NIST Special Publication 1500-1r2.
   https://www.nist.gov/publications/nist-big-data-interoperability-framework-volume-1-definitions

6. Microsoft. (2026). *What is big data?* Microsoft Fabric.
   https://www.microsoft.com/en-us/microsoft-fabric/resources/data-101/what-is-big-data.
