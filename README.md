# Movilidad urbana y productividad económica en ciudades de LATAM

## Contexto de negocio
¿En qué ciudades latinoamericanas conviene invertir en infraestructura de transporte? Este análisis evalúa cómo se relaciona la congestión vehicular con la productividad económica (PIB per cápita).

## Datos
- **TomTom Traffic Index:** 1,004,464 registros de tráfico, con 387 ciudades en 2024.
- **OECD Cities:** indicadores económicos de 15 ciudades latinoamericanas (2023–2024): PIB per cápita, desempleo, PM2.5 y población.

## Proceso
1. Estandarización de columnas a `snake_case` y conversión de fechas a `datetime`.
2. Limpieza de cifras numéricas en formato europeo (separadores de miles, comas decimales y símbolo %).
3. Filtro del año 2024 y promedio de las métricas de tráfico por ciudad.
4. Unión INNER por `city` y `year`: quedaron **15 ciudades de 7 países**.
5. Validación visual: boxplot de congestión, histograma de PIB per cápita y comparación por ciudad.

## Hallazgos
- Ciudad de México tiene el mayor retraso por congestión de las **387 ciudades** del dataset en 2024: **2,833 s** de `jams_delay` promedio, frente a Tokio (2,153), Nueva York (2,133) y Londres (2,051).
- Bogotá registra un `jams_delay` de 1,142 s, un índice de tráfico de 37.6 y 25.0 minutos por cada 10 km. Son valores más altos que los de Ciudad de México en índice de tráfico y en tiempo de viaje.
- No hay una relación clara entre PIB per cápita y congestión. Montevideo tiene el PIB más alto de la muestra (≈26,000) con congestión casi nula, mientras que Ciudad de México combina un PIB alto (≈21,000) con la mayor congestión.
- El PIB per cápita de Santiago (≈2,200) es atípico frente al resto y debería validarse.

## Recomendaciones
- Bogotá es candidata a prioridad: tiene congestión alta (PIB per cápita de 11,442, desempleo de 10.0%) y una base económica media-baja dentro de la muestra.
- Antes de decidir una inversión, calcular la correlación entre variables y validar los datos atípicos.

## Limitaciones
Muestra de solo 15 ciudades y un único año de análisis (2024).

## Herramientas
Python (pandas, NumPy, Matplotlib, Seaborn), Jupyter Notebook.
