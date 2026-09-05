PARCIAL DE CIENCIA DE DATOS.

## Caso: Análisis de datos para el mantenimiento de una máquina industrial

### Introducción

En una empresa dedicada a procesos industriales, las máquinas generan información constantemente durante sus actividades de producción y mantenimiento. Esta información puede provenir de diferentes fuentes, como sensores, registros de producción, registros de mantenimiento y fotografías de los equipos.

El análisis de estos datos permite organizar la información disponible y obtener conocimientos útiles sobre el comportamiento de una máquina. Para ello, es importante reconocer que no todos los datos tienen la misma estructura. Algunos pueden organizarse fácilmente en tablas, mientras que otros requieren formatos diferentes para su almacenamiento y análisis.

En este caso se plantea una situación sencilla relacionada con el mantenimiento de una máquina industrial. Se identificarán cuatro tipos de datos y se clasificará cada uno como estructurado, semiestructurado o no estructurado. Posteriormente, se formulará una pregunta de analítica descriptiva y otra de analítica predictiva. Finalmente, se representará mediante un diagrama el flujo general de los datos desde su fuente hasta su visualización.

---

# 1. Identificación y clasificación de 4 tipos de datos

Para el caso de la máquina industrial se seleccionan cuatro tipos de información que una empresa podría recopilar durante sus actividades normales.

| N.º | Tipo de dato                       | Ejemplo                                                        | Clasificación        | Justificación                                                                                                                      |
| --: | ---------------------------------- | -------------------------------------------------------------- | -------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
|   1 | Registros de producción            | Fecha, cantidad producida, turno y horas de funcionamiento     | **Estructurado**     | Puede organizarse en filas y columnas, donde cada columna representa una variable y cada fila corresponde a un registro.           |
|   2 | Lecturas de sensores               | Temperatura, vibración, presión, velocidad y fecha de medición | **Estructurado**     | Si las mediciones se almacenan con campos definidos, pueden organizarse en una tabla con una estructura previamente establecida.   |
|   3 | Registros de mantenimiento en JSON | Fecha, máquina, técnico, actividad realizada y observaciones   | **Semiestructurado** | JSON utiliza elementos, nombres de campos y valores para organizar la información, pero no depende de una estructura tabular fija. |
|   4 | Fotografías de la máquina          | Imágenes de piezas, componentes o posibles daños               | **No estructurado**  | Una fotografía no presenta una estructura de filas y columnas ni un esquema tabular predefinido para representar su contenido.     |

### 1.1 Datos estructurados

Los **datos estructurados** son aquellos que tienen un formato o esquema definido y que normalmente pueden representarse mediante tablas compuestas por filas y columnas. Esto facilita su almacenamiento, consulta y análisis.

En el caso seleccionado, los registros de producción pueden contener campos como fecha, turno, cantidad producida y horas de funcionamiento. De manera similar, las lecturas de los sensores pueden registrarse mediante campos como fecha, hora, temperatura, vibración, presión y velocidad.

Por ejemplo, una tabla de lecturas podría tener la siguiente estructura:

| Fecha      | Hora  | Temperatura | Vibración | Presión | Velocidad |
| ---------- | ----- | ----------: | --------: | ------: | --------: |
| 01/09/2026 | 08:00 |       65 °C |  2,1 mm/s | 5,2 bar |  1500 rpm |
| 01/09/2026 | 09:00 |       67 °C |  2,3 mm/s | 5,1 bar |  1495 rpm |

La información anterior tiene campos definidos y puede organizarse fácilmente en una estructura tabular, por lo que en este caso se clasifica como **estructurada**. AWS señala que los datos estructurados suelen ajustarse a esquemas predefinidos y pueden organizarse mediante filas y columnas.

### 1.2 Datos semiestructurados

Los **datos semiestructurados** presentan algún nivel de organización mediante elementos como etiquetas, metadatos, campos o estructuras anidadas, pero no necesariamente utilizan un modelo relacional de filas y columnas.

En este caso se propone utilizar un **registro de mantenimiento en formato JSON**. Este podría contener información como la fecha del mantenimiento, la máquina intervenida, el técnico responsable, las actividades realizadas y las observaciones.

El formato JSON es un ejemplo reconocido de datos semiestructurados porque utiliza una estructura de campos y valores para organizar la información sin requerir una tabla relacional tradicional. AWS identifica JSON y XML, entre otros formatos, como ejemplos de datos semiestructurados.

### 1.3 Datos no estructurados

Los **datos no estructurados** no siguen un modelo de datos predefinido que permita representarlos directamente como una tabla convencional.

En el caso de la empresa industrial, las fotografías de la máquina corresponden a este tipo de datos. Una fotografía puede mostrar una pieza, un componente o un posible daño, pero su contenido visual no está organizado naturalmente mediante columnas y filas.

AWS incluye las imágenes entre los ejemplos de información no estructurada.

### Clasificación final

Por lo tanto, los cuatro datos seleccionados quedan clasificados de la siguiente manera:

* **Estructurados:** registros de producción y lecturas de sensores.
* **Semiestructurados:** registros de mantenimiento en formato JSON.
* **No estructurados:** fotografías de la máquina.

Esta clasificación permite observar que una misma empresa puede trabajar con diferentes formas de información y que cada una puede requerir diferentes métodos de almacenamiento y procesamiento.



# 2. Pregunta de analítica descriptiva y pregunta de analítica predictiva

La analítica permite estudiar los datos desde diferentes perspectivas. En este caso se utilizarán dos de ellas: **analítica descriptiva** y **analítica predictiva**.

IBM distingue la analítica descriptiva como aquella orientada a comprender lo que ocurrió a partir de datos históricos, mientras que la analítica predictiva busca estimar resultados o comportamientos futuros utilizando información disponible.

## 2.1 Analítica descriptiva

### Pregunta

**¿Cuántas horas de funcionamiento tuvo la máquina y cuántos mantenimientos se realizaron durante el último mes?**

### Justificación

Esta pregunta corresponde a la **analítica descriptiva** porque busca conocer y resumir información que ya ocurrió.

Para responderla se pueden utilizar los registros históricos de producción y mantenimiento de la empresa. Por ejemplo, se podrían calcular las horas totales de funcionamiento de la máquina durante el mes y contar la cantidad de mantenimientos realizados en ese mismo período.

El objetivo no es determinar por qué ocurrieron los eventos ni predecir lo que sucederá posteriormente, sino describir el comportamiento registrado durante un período pasado.

Por esta razón, la pregunta responde principalmente a:

**¿Qué ocurrió?**

La analítica descriptiva se utiliza precisamente para revisar datos históricos, identificar tendencias y resumir acontecimientos anteriores.



## 2.2 Analítica predictiva

### Pregunta

**¿Cuál es la probabilidad de que la máquina presente una falla durante el próximo mes a partir de los datos de temperatura, vibración, presión y horas de funcionamiento?**

### Justificación

Esta pregunta corresponde a la **analítica predictiva** porque no se limita a describir acontecimientos pasados. Su objetivo es utilizar los datos disponibles para realizar una estimación sobre un posible acontecimiento futuro.

Para este caso podrían considerarse variables como la temperatura, la vibración, la presión y las horas de funcionamiento de la máquina. Estos datos podrían utilizarse para identificar patrones asociados con las fallas registradas anteriormente y generar una estimación sobre la posibilidad de que ocurra una falla posteriormente.

Por esta razón, la pregunta responde principalmente a:

**¿Qué podría ocurrir?**

La analítica predictiva utiliza información histórica y técnicas estadísticas o de modelado para realizar estimaciones sobre acontecimientos o comportamientos futuros.

# 3. Diagrama: Fuente → Almacenamiento → Análisis → Visualización

Para representar el proceso de datos de la máquina industrial se utilizará el siguiente flujo:

**Fuente → Almacenamiento → Análisis → Visualización**

El diagrama debe realizarse en **cuatro bloques principales conectados mediante flechas**, manteniendo exactamente el orden solicitado en la actividad.

### Diagrama propuesto

```text
┌─────────────────────────────┐
│           FUENTE            │
│                             │
│  • Sensores de la máquina   │
│  • Registros de producción  │
│  • Registros de mantenimiento│
│  • Fotografías              │
└──────────────┬──────────────┘
               │
               ▼
┌─────────────────────────────┐
│       ALMACENAMIENTO        │
│                             │
│  • Datos de producción      │
│  • Lecturas de sensores     │
│  • Archivos JSON            │
│  • Imágenes                 │
└──────────────┬──────────────┘
               │
               ▼
┌─────────────────────────────┐
│           ANÁLISIS          │
│                             │
│  • Limpieza de datos        │
│  • Analítica descriptiva    │
│  • Analítica predictiva     │
└──────────────┬──────────────┘
               │
               ▼
┌─────────────────────────────┐
│        VISUALIZACIÓN        │
│                             │
│  • Gráficas                 │
│  • Indicadores              │
│  • Resultados               │
└─────────────────────────────┘
```

### Explicación del diagrama

**Fuente:**
En esta primera etapa se encuentran los lugares donde se originan los datos. Para la máquina industrial, las fuentes pueden ser los sensores encargados de medir variables de funcionamiento, los registros de producción, los registros generados durante las actividades de mantenimiento y las fotografías tomadas a los componentes de la máquina.

**Almacenamiento:**
Después de ser recopilados, los datos deben almacenarse para poder utilizarlos posteriormente. Dependiendo de su tipo, pueden conservarse en diferentes formatos. Los registros estructurados pueden almacenarse como datos tabulares, los registros semiestructurados pueden conservarse en archivos JSON y las fotografías pueden mantenerse como archivos de imagen.

**Análisis:**
En esta etapa se preparan y estudian los datos. La limpieza permite trabajar con información organizada y adecuada para el análisis. Posteriormente se pueden realizar análisis descriptivos para comprender el comportamiento histórico de la máquina y análisis predictivos para realizar estimaciones sobre posibles acontecimientos futuros.

**Visualización:**
Finalmente, los resultados obtenidos pueden representarse mediante gráficas, indicadores y otros elementos visuales. La visualización facilita la interpretación de los resultados y permite observar de una manera más clara el comportamiento de las variables analizadas.



# 4. Difference between descriptive analytics and predictive analytics

**Descriptive analytics analyzes historical data to understand what happened.**

**Predictive analytics uses historical and current data to estimate what may happen in the future.**

Las dos frases resumen la diferencia principal entre ambos tipos de analítica: la analítica descriptiva se concentra en comprender acontecimientos pasados, mientras que la analítica predictiva utiliza los datos disponibles para realizar estimaciones sobre posibles acontecimientos futuros. Esta distinción coincide con la clasificación de los tipos de analítica presentada por IBM.

# Referencias
Amazon Web Services (AWS). (s. f.). *¿Qué son los datos estructurados?* AWS. https://aws.amazon.com/es/what-is/structured-data/

IBM. (s. f.). *What is Predictive Analytics?* IBM Think. https://www.ibm.com/think/topics/predictive-analytics

National Institute of Standards and Technology (NIST). (s. f.). *Data Science*. NIST Computer Security Resource Center Glossary. https://csrc.nist.gov/glossary/term/data_science
