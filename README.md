# Movilidad urbana y productividad económica en ciudades de LATAM

Análisis de la relación entre la congestión vehicular y el PIB per cápita en 15 ciudades latinoamericanas, para identificar dónde convendría priorizar la inversión en infraestructura de transporte.

## Contexto de negocio
¿En qué ciudades latinoamericanas conviene invertir en infraestructura de transporte? Este análisis evalúa cómo se relaciona la congestión con la productividad económica de cada ciudad.

## Datos
- **TomTom Traffic Index:** 1,004,464 registros de tráfico, con 387 ciudades en 2024.
- **OECD Cities:** indicadores económicos de 15 ciudades latinoamericanas (2023–2024): PIB per cápita, desempleo, PM2.5 y población.

Los datasets fueron proporcionados en el programa de TripleTen.

## Proceso
1. Estandarización de columnas a `snake_case` y conversión de fechas a `datetime`.
2. Limpieza de cifras numéricas en formato europeo (separadores de miles, comas decimales y símbolo %).
3. Filtro del año 2024 y promedio de las métricas de tráfico por ciudad.
4. Unión INNER por `city` y `year`: quedaron **15 ciudades de 7 países** (Argentina, Brasil, Chile, Colombia, México, Perú y Uruguay).
5. Validación visual: boxplot de congestión, histograma de PIB per cápita y comparación por ciudad.

## Hallazgos
- Ciudad de México tiene el mayor retraso por congestión de las **387 ciudades** del dataset en 2024: **2,833 s** de `jams_delay` promedio, frente a Tokio (2,153), Nueva York (2,133) y Londres (2,051).
- Bogotá registra un `jams_delay` de 1,142 s, un índice de tráfico de 37.6 y 25.0 minutos por cada 10 km, valores más altos que los de Ciudad de México en índice de tráfico y tiempo de viaje.
- No hay una relación clara entre PIB per cápita y congestión. Montevideo tiene el PIB más alto de la muestra (≈26,000) con congestión casi nula, mientras que Ciudad de México combina un PIB alto (≈21,000) con la mayor congestión.
- El PIB per cápita de Santiago (≈2,200) es atípico frente al resto y debería validarse.

## Recomendaciones
- Bogotá es candidata a prioridad: tiene congestión alta, PIB per cápita de 11,442 y desempleo de 10.0%, es decir, alta necesidad y una base económica media-baja dentro de la muestra.
- Antes de decidir una inversión, calcular la correlación entre variables y validar los datos atípicos.

## Limitaciones
Muestra de solo 15 ciudades y un único año de análisis (2024).

## Herramientas
Python (pandas, NumPy, Matplotlib, Seaborn), Jupyter Notebook.

## Cómo reproducirlo
1. Abre `notebooks/mobility_economy_analysis.ipynb`.
2. Ejecuta las celdas en orden. El notebook original carga los datos desde `/datasets/`, así que necesitarás los archivos `tomtom_traffic.csv` y `oecd_city_economy.csv`.
3. El resultado limpio está en `data/ladb_mobility_economy_2024_clean.csv`.
