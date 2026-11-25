# Portafolio de Notebooks — Resumen y Publicación

Este repositorio agrupa notebooks de análisis de datos y machine learning (material de TripleTen). Cada carpeta tiene un README con el detalle del flujo, hallazgos y requisitos de datos.

## Estructura y enlaces
- `Proyecto integrado/` — análisis de ventas de videojuegos; feature `total_sale` y comparativas por año/plataforma/género/región.
  - Notebook: `Proyecto integrado/proyecto_integradro5.ipynb:1`
  - README: `Proyecto integrado/README.md:1`
- `Analisis_estadistico/` — telco Megaline; agregaciones mensuales por usuario e ingresos, outliers y boxplots.
  - Notebook: `Analisis_estadistico/notebook.ipynb:1`
  - README: `Analisis_estadistico/README.md:1`
- `data_wrangling/` — Instacart; control de calidad, nulos/duplicados y consistencia de catálogos.
  - Notebook: `data_wrangling/data_wrangling.ipynb:1`
  - README: `data_wrangling/README.md:1`
- `Machine Learning/` — clasificación; Decision Tree, Random Forest, Logistic Regression y baseline dummy.
  - Notebook: `Machine Learning/notebook.ipynb:1`
  - README: `Machine Learning/README.md:1`
- `Recopilacion y almacenamiento de datos /` — EDA de viajes; Top 10 barrios y gráficos.
  - Notebook: `Recopilacion y almacenamiento de datos /notebook.ipynb:1`
  - README: `Recopilacion y almacenamiento de datos /README.md:1`

## Datos y fuentes
- Origen: datasets de TripleTen (no incluidos en el repo por licencias y tamaño).
- Estado: `.gitignore` excluye `*/data/*` y `*/dfs/*`. Si quieres versionarlos, elimina o ajusta esas reglas.
- Ejecución: usa rutas relativas (por ejemplo, `data/...` desde la carpeta del notebook). Evita rutas absolutas.

## Requisitos y entorno
- Python 3.10+ y Jupyter/VS Code.
- Librerías usadas en distintos notebooks: pandas, numpy, matplotlib, seaborn, scipy, scikit-learn, math, pathlib.
- Recomendado crear un entorno:
  - `python -m venv .venv && source .venv/bin/activate` (macOS/Linux)
  - `py -m venv .venv && .venv\Scripts\activate` (Windows)

## Cómo ejecutar
- Abre cada notebook desde su carpeta y ejecuta celdas en orden.
- Verifica directorio de trabajo si hay “file not found”:
  - `import os; os.getcwd()`
- Usa `pathlib` para rutas robustas:
  - `from pathlib import Path; base = Path('data'); pd.read_csv(base/'archivo.csv')`

## Publicación en GitHub
- Inicializa y haz commit inicial:
  - `git init && git add . && git commit -m "Add notebooks y READMEs"`
- Crea el repo en GitHub y agrega remoto:
  - `git branch -M main`
  - `git remote add origin https://github.com/<tu_usuario>/<tu_repo>.git`
  - `git push -u origin main`
- Datos grandes: considera Git LFS o subir solo muestras; añade enlaces a las fuentes de TripleTen en la descripción del repo si aplica.

## Sección adicional: Aplicación web (project_tp)
Este repositorio también contiene una app web previa que genera gráficos a partir de datos de autos (relación odómetro-precio, distribuciones y boxplot por tipo).


## Proyecto nuevo
- [Recuperación de oro](Machine%20Learning/Recuperacion%20de%20oro/README.md): análisis y modelos con validación temporal.
