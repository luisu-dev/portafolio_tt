# Selección de la mejor región para perforar pozos petroleros

> **Resumen:** Modelos de regresión lineal para predecir el volumen de reservas de pozos en 3 regiones, más análisis de ganancias y riesgo con bootstrap. **La región 2 es la única que cumple el límite de riesgo (0.7% < 2.5%)** y tiene la mayor ganancia promedio esperada (~4.5 M USD).

## Contexto del problema
Una compañía petrolera debe decidir en cuál de tres regiones perforar 200 nuevos pozos, con una inversión de 100 M USD. Cada región tiene datos de pozos con tres características (`f0`, `f1`, `f2`) y su volumen de reservas (`product`, en miles de barriles).

## Objetivo
- Predecir las reservas de cada pozo con un modelo de regresión.
- Elegir la región con mayor beneficio esperado, aceptando un **riesgo de pérdidas menor al 2.5%**.

## Datos
- **Fuente:** TripleTen (el dataset no se incluye por licencia).
- **Contenido:** 3 archivos (`geo_data_0/1/2.csv`) con `id`, `f0`, `f1`, `f2` y `product`.
- **Calidad:** sin valores nulos ni duplicados en ninguna región.

## Supuestos de negocio
- Inversión total: 100 M USD, 200 pozos → 500,000 USD por pozo.
- Ingreso: 4,500 USD por cada mil barriles.
- **Punto de equilibrio:** 111.1 mil barriles por pozo.
- Se estudian 500 pozos candidatos y se perforan los 200 con mayor predicción.

## Metodología
1. **Exploración y calidad de datos** de las tres regiones.
2. **Modelo:** regresión lineal por región (separación 75/25), evaluada con RMSE.
3. **Rentabilidad:** comparación de la producción media predicha contra el punto de equilibrio.
4. **Selección de pozos:** ganancia de los 200 mejores pozos según las predicciones.
5. **Riesgo con bootstrap:** 1,000 repeticiones de muestras de 500 pozos, seleccionando los 200 mejores en cada una; se calcula ganancia promedio, intervalo de confianza al 95% y probabilidad de pérdida.

## Resultados
| Región | RMSE (miles de barriles) | Producción media predicha | Ganancia media (bootstrap) | IC 95% | Riesgo de pérdida |
|---|---|---|---|---|---|
| 1 | 37.58 | 92.59 | 3.94 M USD | [-0.69 M, 9.15 M] | 6.1% |
| **2** | **0.89** | 68.77 | **4.55 M USD** | **[0.61 M, 8.56 M]** | **0.7%** |
| 3 | 39.96 | 95.09 | 3.54 M USD | [-1.63 M, 8.48 M] | 7.6% |

**Hallazgos principales:**
- Ninguna región alcanza el punto de equilibrio con su producción *promedio* (111.1), pero la rentabilidad depende de **elegir los mejores pozos**, no los promedio.
- La región 2 tiene un RMSE casi nulo (0.89), por lo que el modelo identifica con gran precisión sus mejores pozos.
- Las regiones 1 y 3 superan el límite de riesgo (6.1% y 7.6% vs 2.5%) y sus intervalos incluyen pérdidas.

## Conclusión y recomendación
Se recomienda **perforar en la región 2**: es la única con riesgo dentro del límite, con intervalo de confianza completamente positivo y la mayor ganancia esperada. La región 3, que parecía la mejor por producción media, resulta más riesgosa.

## Herramientas
Python, pandas, numpy, scikit-learn (LinearRegression), bootstrap.

## Cómo ejecutar
1. Coloca los archivos `geo_data_0.csv`, `geo_data_1.csv` y `geo_data_2.csv` en `data/`.
2. `pip install -r requirements.txt`
3. Abre `aprendizaje_automatico_negocios.ipynb` y ejecuta las celdas en orden.
