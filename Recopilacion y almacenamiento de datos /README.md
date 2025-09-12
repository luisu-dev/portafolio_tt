# Recopilación y Almacenamiento de Datos — EDA

## Qué hace este notebook
- Carga dos CSV con resultados agregados desde SQL (empresas y barrios) para análisis exploratorio.
- Explora estructura (`info`, `head`) y revisa coherencia de campos numéricos (conteos, promedios).
- Ordena y extrae Top 10 barrios por `average_trips` y realiza visualizaciones.

## Datos requeridos
- Carpeta: `Recopilacion y almacenamiento de datos /data/` (atención al espacio en el nombre de la carpeta).
- Archivos: `moved_project_sql_result_01.csv`, `moved_project_sql_result_04.csv`.
- Recomendado: usar rutas relativas desde el notebook, por ejemplo `data/...` si ejecutas dentro de esta carpeta.

## Flujo de trabajo (resumen)
- Carga → `info`/`head` → selección de métricas → ranking Top 10 → gráficos.

## Dependencias y ejecución
- Python 3.10+, pandas, matplotlib, Jupyter.
- Abre `notebook.ipynb` y ejecuta en orden. Ejemplo de carga:
  ```python
  companies = pd.read_csv('data/moved_project_sql_result_01.csv')
  barrios   = pd.read_csv('data/moved_project_sql_result_04.csv')
  ```

## Salidas esperadas
- Resúmenes `info()` y vistas de datos.
- Gráfico de Top 10 barrios por `average_trips`.
