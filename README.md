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
