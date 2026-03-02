# Predicción de Producción Mensual en Pozos No Convencionales (Argentina)

Como ingeniero vinculado a la industria Oil & Gas, uno de los desafíos más frecuentes es estimar el comportamiento productivo de un pozo a lo largo del tiempo.  Este proyecto nace como parte de mi proceso de formación en Ciencia de Datos, con la intención de explorar cómo técnicas de Machine Learning pueden complementar el análisis tradicional de producción.

## Objetivo

Desarrollar un modelo capaz de estimar la producción mensual de petróleo por pozo, utilizando información geológica, operativa y el comportamiento histórico del mismo. El enfoque está orientado a generar una herramienta que pueda apoyar el análisis operativo y la detección temprana de desvíos productivos.

## Enfoque  técnico:

El proyecto incluye:

- Análisis Exploratorio de Datos (EDA) completo
- Depuración de valores atípicos y revisión de inconsistencias
- Ingeniería de variables con memoria temporal (lags, acumulados y tendencia)
- Transformación logarítmica del target debido a la alta asimetría de los datos
- Separación de entrenamiento y prueba por pozo (GroupShuffleSplit), garantizando que un mismo pozo no aparezca en ambos conjuntos

### Modelo seleccionado: Random Forest Regressor

Se eligió Random Forest debido a:

- Capacidad para capturar relaciones no lineales
- Robustez frente a ruido y outliers
- Buen desempeño como modelo base en problemas tabulares
- Capacidad de modelar interacciones entre variables geológicas y operativas

## Resultados

El desempeño del modelo fue evaluado utilizando R² y RMSE en escala real, luego de revertir la transformación logarítmica aplicada al target. Se obtuvo un R² = 0.9435, lo que indica que el modelo explica aproximadamente el 94% de la variabilidad observada en la producción mensual de petróleo. Esto refleja una buena capacidad para capturar la dinámica productiva general de los pozos, especialmente considerando la alta dispersión y heterogeneidad del dataset.

El RMSE fue de 203.96 unidades de producción mensual, medido en escala real. Esta métrica permite dimensionar el error promedio de predicción en términos operativos. Dado que el dataset presenta una fuerte concentración de producción en ciertos pozos y presencia de valores extremos, este nivel de error resulta coherente con la escala y variabilidad natural del sistema.

Más allá de las métricas globales, se realizó un análisis detallado mediante:

- Comparación real vs predicho
- Análisis de los mayores errores absolutos
- Visualización de curvas mensuales individuales por pozo

El modelo reproduce adecuadamente la tendencia productiva y la continuidad mensual de los pozos. Los mayores errores se observan en valores extremos (picos o caídas abruptas), donde pueden intervenir factores operativos no modelados o comportamientos atípicos que el modelo tiende a suavizar.

## Aplicaciones potenciales

- Pronóstico mensual de producción
- Detección temprana de anomalías
- Comparación de desempeño por formación y tipo de extracción
- Integración futura en dashboards operativos
  
## Nota final

Este proyecto representa uno de mis primeros desarrollos aplicando Machine Learning a datos reales del sector energético.  
Es el inicio de un camino que busca integrar la ciencia de datos con el conocimiento técnico en campo.
