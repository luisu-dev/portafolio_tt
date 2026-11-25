# Recuperación de oro: análisis y modelado

Proyecto de ciencia de datos que analiza el proceso de recuperación de oro y compara modelos para predecir la recuperación en las etapas *rougher* y final.

## Objetivo

Predecir `rougher.output.recovery` y `final.output.recovery` con mediciones disponibles durante el proceso. El análisis busca evitar fuga de información y respetar el orden temporal de las observaciones.

## Contenido del proyecto

- `gold_recovery_corregido_v2.ipynb`: análisis exploratorio, preparación de datos, modelado y conclusiones.
- `requirements.txt`: dependencias de Python.
- `data/`: ubicación local esperada de los CSV. Los datos no se incluyen en este repositorio.

## Flujo de análisis

1. Revisión de estructura, fechas, valores ausentes y cálculo de recuperación.
2. Selección de variables disponibles antes de conocer los resultados de cada etapa.
3. Análisis de concentraciones, valores atípicos y diferencias entre entrenamiento y prueba.
4. Comparación de regresión lineal, Ridge y Random Forest con validación temporal (`TimeSeriesSplit`).
5. Evaluación con sMAPE ponderado y comparación contra una referencia que predice la mediana.

La métrica final es:

`0.25 × sMAPE(rougher) + 0.75 × sMAPE(final)`

Un valor menor indica mejor desempeño.

## Resultados principales

En la ejecución documentada en el notebook, Random Forest obtuvo un sMAPE ponderado de **6.253** en el conjunto de prueba, frente a **6.912** de la referencia de mediana. El resultado se basa en una sola partición de prueba y debe interpretarse junto con el análisis de desfase entre entrenamiento y prueba que aparece en el notebook.

## Datos

Coloca los archivos del proyecto en `data/` con estos nombres:

- `gold_recovery_train.csv`
- `gold_recovery_test.csv`
- `gold_recovery_full.csv`

El notebook espera esos tres archivos y los carga desde esa carpeta. Si recibiste los datos como parte de un curso o proyecto, utiliza los archivos originales proporcionados allí. Por su tamaño y para mantener el repositorio ligero, los CSV están excluidos de Git.

## Requisitos

- Python 3.10 o posterior
- Jupyter Notebook
- Paquetes listados en `requirements.txt`

## Cómo reproducir

Desde la carpeta del proyecto, crea un entorno e instala las dependencias:

```bash
python -m venv .venv
```

Activa el entorno y luego ejecuta:

```bash
python -m pip install -r requirements.txt
jupyter notebook
```

Abre `gold_recovery_corregido_v2.ipynb` y ejecuta las celdas en orden. La búsqueda de hiperparámetros de Random Forest puede tardar varios minutos, según el equipo.

## Herramientas

Python · pandas · NumPy · Matplotlib · SciPy · scikit-learn · Jupyter

## Autoría

Proyecto personal de portafolio. Actualiza esta sección con tu nombre y enlaces profesionales antes de publicarlo, si quieres que el repositorio conecte directamente con tu perfil de LinkedIn.

