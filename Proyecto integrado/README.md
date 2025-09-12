# Proyecto integrado — Análisis de ventas de videojuegos

## Qué hace este notebook
- Carga y explora `games.csv` (ventas globales por juego con columnas como `Name`, `Platform`, `Year_of_Release`, `Genre`, `NA/EU/JP/Other_sales`, `Critic_Score`, `User_Score`, `Rating`).
- Limpieza y estandarización de columnas: minúsculas, `strip`, reemplazo de espacios por guiones bajos y depuración de nulos/duplicados claves.
- Crea la métrica `total_sale` como suma de ventas por región.
- EDA por año y plataforma: series anuales, top 10 plataformas globales y por periodo (enfoque en 2005–2016).
- Análisis por género y por región (NA/EU/JP), y comparativas de rating ESRB.
- Visualizaciones: líneas de ventas por año/plataforma, boxplots por plataforma y por género, barras comparativas por región.
- Conclusiones: etapa de mayor competencia a partir de 2005 (séptima generación), impacto de bundles en Sports, patrones distintos por región.

## Datos requeridos
- Archivo: `data/games.csv` (ruta relativa a esta carpeta).
- Nota: usa rutas relativas como `pd.read_csv('data/games.csv')`. Evita anteponer el nombre de la carpeta del proyecto en la ruta.

## Flujo de trabajo (resumen)
- Carga → inspección (`info`, `describe`, `isna`, `duplicated`).
- Normaliza nombres de columnas y elimina nulos críticos (`name`, `year_of_release`, `genre`).
- Feature engineering: `total_sale` y agregaciones por año/plataforma/género.
- Subconjunto de 2005–2016 para comparativas modernas y gráficas.
- Comparativas por región y por rating.

## Dependencias y ejecución
- Python 3.10+, pandas, numpy, matplotlib, seaborn, scipy, Jupyter.
- Ejecuta `proyecto_integradro5.ipynb` en orden. Para rutas robustas:
  ```python
  from pathlib import Path
  juegos = pd.read_csv(Path('data') / 'games.csv')
  ```

## Salidas esperadas
- Tablas de resumen y estadísticas descriptivas.
- Gráficos de tendencias y comparativas por plataforma/género/región.
