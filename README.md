![Portada animada](./assets/Grupo4GIF.gif)
## 👥 Integrantes del grupo

- **Bonilla Alejandro Sergia**  
- **Franco Nieto Carlos**  
- **Reyes Peñafiel Fátima**  
- **Rodas Cruz Mia**
---
- ## 🎯 Objetivo
Analizar el comportamiento de precios, distancias y demanda en servicios de transporte (Uber y Lyft), considerando la influencia de las condiciones climáticas.  
El propósito es descubrir patrones, relaciones entre variables e insights que permitan comprender cómo el clima y el horario afectan el costo de los viajes.

## 🧩 1. Exploración inicial del dataset
Se trabajó con dos archivos:

| Dataset | Filas | Columnas | Descripción |
|----------|--------|-----------|-------------|
| `PFDA_rides.csv` | 693,071 | 10 | Información de viajes (tipo de cab, distancia, precio, hora, etc.) |
| `PFDA_weather.csv` | 6,276 | 8 | Condiciones meteorológicas (temperatura, lluvia, humedad, viento, etc.) |

**Columnas principales:**
- `distance`, `cab_type`, `time_stamp`, `price`, `surge_multiplier`
- `temp`, `rain`, `humidity`, `clouds`, `wind`
## 🧹 2. Evaluación de calidad de datos

| Aspecto | Resultado |
|----------|------------|
| Duplicados | 0 registros |
| Valores nulos | 55,095 en `price` (≈ 7.95%) |
| Outliers | Detectados en `price` y `distance` |
| Limpieza sugerida | Tratar nulos en clima y ajustar valores extremos |

> 📌 El dataset tiene buena calidad general, pero requiere limpieza ligera para asegurar precisión.

## 🧮 3. Creación de nuevas variables

Se generaron **tres variables derivadas** para facilitar el análisis:

| Variable nueva | Descripción | Método |
|----------------|--------------|---------|
| `hora` | Hora del día del viaje | `dt.hour` |
| `dia_semana` | Día de la semana | `dt.day_name()` |
| `categoria_precio` | Clasificación en **Bajo**, **Medio**, **Alto** | `pd.cut(price, bins=[0,10,25,100])` |

## 📊 4. Visualizaciones principales
### 🔹 1. Distribución del Precio
📈 **Pregunta:** ¿Cómo se distribuyen los precios de los viajes?

![Histograma de precios](assets/hist_price.png)  
> La mayoría de los viajes presentan **precios bajos**, con pocos valores extremos.
### 🔹 2. Distancia por Tipo de Cab
📊 **Pregunta:** ¿Existen diferencias de distancia entre Uber y Lyft?

![Boxplot distancia por cab](assets/boxplot_distance.png)  
> **Uber** tiende a cubrir **mayores distancias promedio** que **Lyft**.

### 🔹 3. Categoría de Precio por Empresa
📉 **Pregunta:** ¿Qué empresa domina cada categoría de precios?

![Barras categoría precio](assets/bar_price_category.png)  
> Lyft concentra más viajes en **“Bajo”**, mientras que Uber lidera en **“Medio”**.

## 🔍 5. Diagnóstico general

| Observación | Detalle |
|--------------|----------|
| Estructura de datos | Coherente y combinada correctamente |
| Faltantes | Variables climáticas con muchos nulos |
| Outliers | En precios y distancias |
| Unión datasets | Realizada por índice (para simplificar) |
| Tamaño final | (693,071 filas × 21 columnas) |
## 🧠 6. Propuestas de análisis futuras

| Nº | Tema de análisis | Pregunta de investigación |
|----|------------------|---------------------------|
| 1️⃣ | Clima vs Precio | ¿Suben los precios cuando llueve o hace frío? |
| 2️⃣ | Demanda vs Hora | ¿Las horas pico incrementan significativamente el precio? |


## ✅ 7. Conclusión general
El análisis exploratorio permitió identificar la **estructura y calidad de los datos** y reconocer patrones entre **Uber y Lyft**.  
Se observan **diferencias claras** en precios y distancias, posiblemente influenciadas por el **clima y el horario**.

> Se recomienda manejar los valores faltantes y outliers antes de aplicar modelos predictivos o análisis más avanzados.



