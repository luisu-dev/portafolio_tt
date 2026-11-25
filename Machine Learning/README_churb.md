# Predicción de abandono de clientes (Churn) en un banco

> **Resumen:** Modelo de clasificación para identificar clientes bancarios con riesgo de abandono. Comparé regresión logística (con y sin balance de clases) y Random Forest sobre 10,000 clientes; el mejor modelo alcanzó **AUC-ROC de 0.859** y **F1 de 0.573** en validación.

## Contexto del problema
Retener a un cliente cuesta menos que conseguir uno nuevo. El banco quiere anticipar qué clientes están por irse para poder ofrecerles acciones de retención a tiempo.

## Objetivo
Construir un modelo que prediga si un cliente abandonará el banco (`Exited`) y maximizar el F1, cuidando el recall de la clase que se va.

## Datos
- **Fuente:** TripleTen (el dataset no se incluye en el repo por licencia).
- **Tamaño:** 10,000 clientes, 14 columnas.
- **Variables:** puntaje de crédito, país, género, edad, antigüedad (`Tenure`), balance, número de productos, tarjeta de crédito, miembro activo y salario estimado.
- **Objetivo:** `Exited` (1 = abandonó). **Desbalance de clases:** 80% se queda, 20% se va.
- **Calidad de datos:** ~9% de nulos en `Tenure`, rellenados con la mediana.

## Metodología
1. **Preparación:** imputación de nulos y one-hot encoding de `Geography` y `Gender`; se eliminaron identificadores (`RowNumber`, `CustomerId`, `Surname`).
2. **Separación de datos:** entrenamiento y validación (75/25).
3. **Baseline:** regresión logística ignorando el desbalance, para mostrar por qué accuracy no basta.
4. **Manejo del desbalance:** regresión logística con `class_weight='balanced'`.
5. **Modelo final:** Random Forest con búsqueda de hiperparámetros (profundidad y número de árboles) optimizando F1.
6. **Evaluación:** accuracy, recall, F1 y curvas ROC / AUC.

## Resultados (conjunto de validación)
| Modelo | Accuracy | Recall | F1 | AUC-ROC |
|---|---|---|---|---|
| Regresión logística (sin balance) | 0.783 | 0.067 | 0.117 | 0.676 |
| Regresión logística (balanceada) | 0.685 | 0.705 | 0.489 | 0.757 |
| **Random Forest** | **0.858** | 0.447 | **0.573** | **0.859** |

**Hallazgos principales:**
- Sin balancear, el modelo acierta 78% pero detecta solo 7% de los clientes que se van: accuracy es engañosa con clases desbalanceadas.
- Balancear las clases multiplicó el recall por 10 (0.07 → 0.70), a costa de más falsos positivos.
- El Random Forest ofrece el mejor equilibrio: F1 de 0.573 y AUC de 0.859, la mejor capacidad para separar a quienes se van de quienes se quedan.

## Conclusiones
- El Random Forest es el modelo recomendado para esta tarea, aunque requiere más cómputo que la regresión logística.
- Si el banco prioriza **detectar a la mayor cantidad de clientes en riesgo**, la regresión logística balanceada (recall 0.70) puede ser preferible; si prioriza **no gastar en retención de clientes que no se iban a ir**, conviene el Random Forest.
- **Siguientes pasos:** evaluar en un conjunto de prueba independiente, ajustar el umbral de decisión y probar modelos de boosting.

## Herramientas
Python, pandas, scikit-learn, matplotlib.

## Cómo ejecutar
1. Coloca `Churn.csv` en la carpeta `data/`.
2. Instala dependencias: `pip install -r requirements.txt`
3. Abre `churn_model.ipynb` y ejecuta las celdas en orden.
