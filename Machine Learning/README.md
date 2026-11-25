# Machine Learning — Clasificación de comportamiento de usuarios

## Qué hace este notebook
- Carga `users_behavior.csv` y separa variables en `features` y `target`.
- División de datos: `train`/`valid`/`test` usando `train_test_split`.
- Pruebas de modelos:
  - DecisionTreeClassifier: barrido de `max_depth`, entrenamiento y evaluación.
  - RandomForestClassifier: barrido de `n_estimators`, evaluación en validación.
  - LogisticRegression: entrenamiento (solver liblinear) y evaluación.
- Entrenamiento final en `train+valid` con mejores hiperparámetros y evaluación en `test`.
- Baseline: `DummyClassifier` para verificar que los modelos aprenden sobre el patrón mayoritario.
- Conclusión: modelos simples (Logistic/Tree) alcanzan accuracy ~0.78–0.88, comparables a RandomForest con menos costo computacional.

## Datos requeridos
- Carpeta: `Machine Learning/data/`
- Archivo: `users_behavior.csv`

## Flujo de trabajo (resumen)
- Carga → split → entrenamiento y tuning → baseline → evaluación final → conclusiones.

## Dependencias y ejecución
- Python 3.10+, pandas, numpy, scikit-learn, Jupyter.
- Abre `notebook.ipynb`, ajusta hiperparámetros (`max_depth`, `n_estimators`, `solver`) según pruebas.

## Salidas esperadas
- Accuracy por modelo en train/valid y resultados finales en test.
- Comparación contra baseline dummy para validar aprendizaje.

## Otro proyecto
- [Recuperación de oro](Recuperacion%20de%20oro/README.md) — predicción de recuperación de oro con sMAPE y validación temporal.
