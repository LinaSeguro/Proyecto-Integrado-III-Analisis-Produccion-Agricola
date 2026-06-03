# Proyecto-Integrado-III-Analisis-Produccion-Agricola
# 🌾 Análisis de la Producción Agrícola en Colombia (EVA 2019-2024)

## 🎯 I. Definición del Problema de Negocio

### 📝 Descripción del Problema
La producción agrícola en Colombia presenta variaciones significativas entre diferentes regiones y tipos de cultivo. Estas diferencias pueden afectar la planificación y la toma de decisiones en el sector agro, ya que no se tiene claridad sobre qué cultivos son más productivos ni en qué zonas se obtienen mejores resultados.

### ❓ Pregunta de Investigación
> **¿De qué manera varía el rendimiento agrícola (t/ha) en Colombia según el tipo de cultivo y la región en el periodo 2019–2024, y en qué medida el rendimiento del café en la región andina supera el promedio nacional de este cultivo?**

---

## 📊 II. Métricas de Éxito

Para evaluar el éxito del análisis se utilizarán las siguientes métricas:

* **📈 Rendimiento Agrícola (t/ha):** Es la métrica principal de eficiencia productiva. Se define mediante la fórmula:
    
    $$Rendimiento = \frac{Producción (t)}{Área Cosechada (ha)}$$

    *El éxito del análisis se medirá mediante la identificación de los **5 departamentos con mayor rendimiento promedio**, segmentados por tipo de cultivo.*

* **📦 Producción Total (t) y 🗺️ Área Cosechada (ha):** Variables base fundamentales para el cálculo del rendimiento y la magnitud de la actividad.

* **📍 Promedio de Rendimiento por Departamento:** Métrica que permite realizar comparaciones geográficas y segmentar el comportamiento productivo según el tipo de cultivo.

---

## 🚀 III. Objetivo del Análisis
2019–2024 mediante el uso del rendimiento (t/ha), con el fin de identificar las zonas de mayor eficiencia productiva y evaluar el comportamiento del cultivo de café en la región andina frente al promedio nacional.

Este análisis permitirá comprender las diferencias en el desempeño agrícola según el tipo de cultivo y la región, facilitando la toma de decisiones basada en datos en el sector agropecuario.

---
## 🧠 IV. Hipótesis

- 🌱 El rendimiento agrícola promedio (t/ha) del cultivo de café en los departamentos de la región andina es superior al promedio nacional para ese mismo cultivo durante el periodo 2019–2024.
----
📂 **Fuente de Datos**
El dataset utilizado proviene de las **Evaluaciones Agropecuarias Municipales (EVA)**, publicadas por el Ministerio de Agricultura y Desarrollo Rural de Colombia a través del portal de Datos Abiertos.
* **Dataset:** [Evaluaciones Agropecuarias Municipales (EVA)](https://www.datos.gov.co/Agricultura-y-Desarrollo-Rural/Evaluaciones-Agropecuarias-Municipales-EVA-2019-20/uejq-wxrr/about_data)
* **Periodo:** 2019 - 2024

---
## 🛠️ **V. Diagnóstico y Preparación de Datos (EDA)**

Para garantizar la fiabilidad del análisis descriptivo, se ejecutó un proceso de auditoría de datos sobre los 141,073 registros:

* **Limpieza de Tipos:** Conversión de variables de `object` a `float` para habilitar el cálculo matemático.
* **Integridad:** * **Duplicados:** Se verificó la existencia de registros idénticos para evitar sobrecostos en las métricas.
    * **Valores Nulos:** Identificación y tratamiento de vacíos para no sesgar los promedios.
    * **Ceros:** Validación de valores en 0.00, determinando que corresponden a escalas de minifundio y no a errores de sistema.
* **Análisis Estadístico:** * **Resumen:** Generación de medias, desviaciones y cuartiles (Media nacional: 10.60 t/ha).
    * **Distribuciones:** Análisis de la forma de los datos para entender la dispersión de la producción.
    * **Correlaciones:** Evaluación de la relación entre el Área Cosechada y la Producción Total para validar la lógica del rendimiento calculado.

## 📈 **VI. Hallazgos Principales**

1.  **Consistencia:** Existe una correlación lógica fuerte entre área y producción, lo que valida la calidad de la fuente EVA.
2.  **Representatividad:** El dataset permite analizar tanto grandes productores como pequeñas parcelas, manteniendo la diversidad del agro colombiano.
3.  **Viabilidad de la Hipótesis:** El segmento de café presenta datos limpios y suficientes para proceder con la comparación de la Región Andina frente al resto del país.

---

## 🛠️ Procesamiento y Limpieza de Datos (ETL)

Sobre un volumen de **141,073 registros**, se aplicaron las siguientes transformaciones para asegurar la integridad del análisis:

### 1. Depuración y Tipado
* **Ajuste de Tipos:** Conversión de variables críticas a `float` para habilitar cálculos de rendimiento.
* **Eliminación de Redundancia:** Se removieron columnas de códigos internos (DANE) para optimizar el peso del dataset.
* **Manejo de Nulos/Ceros:** Validación de valores en 0.00, confirmando que corresponden a escalas de pequeña producción (minifundio) y no a errores de captura.

### 2. Ingeniería de Datos (Nuevas Variables)
* **`Ubicacion_Unica`**: Concatenación de *Departamento + Municipio* para corregir la duplicidad de nombres de municipios entre regiones.
* **Regionalización Natural**: Creación de la columna `Region` mediante el mapeo de los 32 departamentos en las **5 regiones naturales de Colombia** (Andina, Caribe, Pacífico, Orinoquía y Amazonía).
* **Métrica de Rendimiento**: Cálculo automatizado de `Rendimiento = Producción (t) / Área Cosechada (ha)`.

### 3. Estructura del Repositorio 📂
### 📂 Estructura del Repositorio

```text
Proyecto-Integrado-III/
├── 📁 data/
│   ├── 📄 EVA_Datos_Crudos.zip    # Dataset original comprimido (>25MB)
│   ├── 📄 df_limpio_global.csv    # Dataset depurado y regionalizado
│   └── 📄 df_cafe_final.csv       # Dataset optimizado para análisis de café
├── 📁 docs/                       # Documentación y reportes
│   └── 📄 Reporte_Final.pdf       # Informe ejecutivo del análisis final
├── 📄 Analisis_Produccion.ipynb   # Notebook de Google Colab con el código ETL
└── 📄 README.md                   # Documentación principal del proyecto

```
----
## 🔍 Análisis de Datos

Para validar la hipótesis del proyecto se analizaron las variables **rendimiento (t/ha)**, **producción**, **área cosechada**, **región**, **departamento** y **año**. La variable principal fue el rendimiento, ya que permite medir la eficiencia productiva del cultivo de café y realizar comparaciones entre diferentes regiones del país.

El análisis regional mostró que la **Región Andina** obtuvo un rendimiento promedio de **1.07 t/ha**, mientras que el **promedio nacional** fue de **1.05 t/ha** durante el periodo 2019–2024. Esta diferencia representa aproximadamente un **2.1 %** a favor de la Región Andina.

A nivel departamental, **Huila, Quindío y Antioquia** se destacaron por registrar algunos de los mayores rendimientos promedio del país, evidenciando una alta eficiencia productiva en estos territorios.

El análisis temporal permitió observar el comportamiento del rendimiento cafetero entre 2019 y 2024, identificando patrones consistentes en la productividad del cultivo a lo largo del periodo estudiado.

Los resultados obtenidos respaldan la hipótesis planteada al inicio del proyecto, demostrando que la **Región Andina presenta un rendimiento promedio superior al promedio nacional** para el cultivo de café en Colombia.
## Conclusión

El análisis realizado permitió validar la hipótesis planteada al inicio del proyecto, evidenciando que la Región Andina presentó un rendimiento promedio superior al promedio nacional en el cultivo de café durante el periodo 2019–2024.

A través de la limpieza, transformación y visualización de los datos, se identificaron diferencias regionales en la productividad cafetera y se destacó el aporte de departamentos como Huila, Quindío y Antioquia. La variable **rendimiento (t/ha)** fue fundamental para medir la eficiencia productiva y realizar comparaciones objetivas entre regiones.

Los resultados obtenidos demuestran la utilidad de la analítica de datos para comprender el comportamiento del sector agrícola colombiano y generar información que contribuya a la toma de decisiones basada en datos.

----
## 📄 Documentación Final

Para una revisión detallada de la metodología, gráficas y conclusiones del proyecto, consulta el informe ejecutivo:

[👉 Haz clic aquí para ver el Informe Final en PDF](./docs/Reporte_Final.pdf)

---

*Este proyecto fue desarrollado como parte del Proyecto Integrado III.*

