# Descripción del Proyecto: Ubicación Óptima para el Desarrollo de Nuevos Pozos Petroleros

## Introducción

El propósito de este proyecto es identificar la región más rentable y de menor riesgo para desarrollar nuevos pozos petroleros para la empresa minera **OilyGiant**. El proyecto tiene como objetivo utilizar modelos predictivos, análisis de datos y técnicas de bootstrapping para evaluar tres regiones geográficas potenciales: **geo_0**, **geo_1** y **geo_2**. El objetivo es determinar qué región ofrece el mejor equilibrio entre reservas de petróleo altas, ganancias sustanciales y un riesgo mínimo. La empresa busca maximizar las ganancias mientras minimiza la posibilidad de pérdidas en sus esfuerzos de exploración y producción de petróleo.

### Descripción de los Datos

El proyecto utiliza conjuntos de datos que representan tres regiones, cada una con información sobre las reservas de petróleo predichas en barriles (STB) para un conjunto de pozos petroleros. Cada conjunto de datos consta de 100,000 observaciones, con tres columnas: **ID**, **Volumen de Reservas Predicho (STB)** y **Volumen de Reservas Real (STB)**. Los datos fueron limpiados eliminando columnas redundantes o irrelevantes, y se aplicó una división estándar de entrenamiento-prueba (75% para entrenamiento y 25% para prueba). Los principales objetivos son:

- Predecir las reservas de petróleo utilizando un modelo de regresión lineal.
- Estimar las ganancias en función de las reservas predichas.
- Evaluar los riesgos de pérdidas en cada región.
- Comparar las tres regiones para determinar la ubicación óptima para el desarrollo.

## Metodología

### Preprocesamiento de los Datos

- **División de Datos**: El conjunto de datos fue dividido en un conjunto de entrenamiento (75%) y un conjunto de prueba (25%).
- **Estandarización de Características**: Las características numéricas fueron estandarizadas para asegurar que el modelo de aprendizaje automático tuviera un rendimiento óptimo.
- **Selección de Modelo**: Se utilizó un **Algoritmo de Regresión Lineal** para predecir las reservas de petróleo en función de las características disponibles en el conjunto de datos.

### Técnicas Analíticas Clave

- **Regresión Lineal**: Utilizada para predecir el volumen de reservas en cada región basada en los datos de entrenamiento.
- **Bootstrapping**: Técnica estadística utilizada para calcular la distribución de ganancias mediante el muestreo de los datos de prueba 1,000 veces para estimar la variabilidad de las predicciones.
- **Cálculo de Ganancias**: Se creó una función personalizada para calcular las ganancias en función del volumen de reservas predicho utilizando un costo por barril y un costo de capital dado.
- **Análisis de Riesgo**: El riesgo de pérdida se calculó determinando el porcentaje de muestras de bootstrapping que resultaron en ganancias negativas.

### Métricas de Evaluación

- **R² (Coeficiente de Determinación)**: Para evaluar la calidad del ajuste del modelo.
- **RMSE (Raíz del Error Cuadrático Medio)**: Para medir el error en la predicción de reservas.
- **MAE (Error Absoluto Medio)**: Para evaluar el error promedio en la predicción.
- **Bootstrapping**: Utilizado para evaluar la distribución de ganancias, intervalos de confianza y el riesgo de pérdidas.

## Resultados

### Desempeño del Modelo por Región

1. **Geo_0**:
   - **R²**: -1.62 (Indica un mal ajuste del modelo, posiblemente debido a valores atípicos en los datos).
   - **RMSE**: 37.58 (Error alto, lo que sugiere que el modelo tiene dificultades para predecir con precisión en esta región).
   - **MAE**: 30.92 (Indica un error significativo promedio en las predicciones).

2. **Geo_1**:
   - **R²**: 0.9996 (Indica un excelente ajuste del modelo, lo que sugiere que esta región es altamente predecible).
   - **RMSE**: 0.89 (Error bajo, lo que indica que el modelo proporciona predicciones precisas).
   - **MAE**: 0.72 (Muy bajo, confirmando predicciones precisas).

3. **Geo_2**:
   - **R²**: -3.06 (Ajuste del modelo extremadamente pobre, con una gran brecha entre las predicciones y las reservas reales).
   - **RMSE**: 40.03 (Error muy alto).
   - **MAE**: 32.79 (Gran error promedio, lo que sugiere una mala capacidad predictiva en esta región).

### Reservas Predichas y Ganancias

- **Geo_0**: El mayor volumen de reservas predicho de **29.60 MMSTB**, resultando en ganancias de **$33,208,260**.
- **Geo_1**: El mayor volumen de reservas predicho de **27.59 MMSTB**, con ganancias de **$24,150,866.97**.
- **Geo_2**: El mayor volumen de reservas predicho de **28.25 MMSTB**, generando ganancias de **$27,103,499.64**.

Se encontró que Geo_0 tiene el mayor volumen de reservas predicho y las mayores ganancias potenciales, lo que sugiere que esta es la región más prometedora desde el punto de vista de las reservas y las ganancias.

### Análisis de Bootstrapping: Distribución de Ganancias y Evaluación del Riesgo

- **Geo_0**:
  - Ganancia promedio: **$4,259,385.27**
  - Intervalo de confianza del 95%: **($4,087,322.07, $4,431,448.47)**
  - Riesgo de pérdidas: **6.00%**
  
- **Geo_1**:
  - Ganancia promedio: **$5,152,227.73**
  - Intervalo de confianza del 95%: **($5,016,214.76, $5,288,240.71)**
  - Riesgo de pérdidas: **1.00%**

- **Geo_2**:
  - Ganancia promedio: **$4,350,083.63**
  - Intervalo de confianza del 95%: **($4,174,535.52, $4,525,631.74)**
  - Riesgo de pérdidas: **6.40%**

Geo_1 mostró la ganancia promedio más alta de **$5.15 millones** con el menor riesgo de pérdida del **1.00%**, lo que lo convierte en la región más estable y rentable desde una perspectiva de riesgo y recompensa.

### Distribución de Ganancias (Bootstrapping)

- La técnica de bootstrapping reveló que **geo_1** generó consistentemente ganancias en el rango de **$50 millones a $52 millones**, con un riesgo de retorno negativo muy bajo.
- **Geo_0** y **Geo_2** demostraron más variabilidad en las ganancias, con un mayor riesgo de pérdidas potenciales.

## Conclusión

### Principales Hallazgos

- **Geo_1**: La región con el mejor rendimiento general en términos de ganancias y riesgo. Ofrece la mayor ganancia promedio y el menor riesgo de pérdida, lo que la convierte en la ubicación óptima para el desarrollo de nuevos pozos petroleros.
- **Geo_0**: Aunque tiene las mayores reservas predichas, el alto riesgo de pérdidas y el mal ajuste del modelo la convierten en una opción menos viable para el desarrollo.
- **Geo_2**: Similar a Geo_0, esta región tiene reservas predichas sustanciales, pero presenta un alto riesgo debido al bajo rendimiento del modelo y una mayor posibilidad de pérdidas.

### Recomendaciones

Basado en los hallazgos, se recomienda que **OilyGiant** enfoque sus esfuerzos en desarrollar nuevos pozos petroleros en **geo_1**. Esta región presenta la mejor combinación de reservas predichas, rentabilidad y riesgo mínimo. El bajo riesgo de pérdidas y el potencial de ganancias sustanciales hacen que **geo_1** sea la opción óptima para la siguiente fase de desarrollo de la empresa.

Geo_0 y Geo_2, aunque muestran algunas reservas prometedoras, conllevan demasiado riesgo e incertidumbre, lo que hace que los beneficios potenciales no justifiquen estos riesgos. Se aconseja no invertir en estas regiones en este momento debido a sus perfiles de riesgo desfavorables.

### Recomendación Final:
**Invertir en Geo_1** para el desarrollo de nuevos pozos petroleros a fin de maximizar las ganancias mientras se minimizan los riesgos potenciales.
