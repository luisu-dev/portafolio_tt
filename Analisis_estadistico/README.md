# Análisis Estadístico — Telco (Megaline)

## Qué hace este notebook
- Carga 5 fuentes: `megaline_calls`, `megaline_internet`, `megaline_messages`, `megaline_plans`, `megaline_users`.
- Limpieza básica: inspección (`info`, `head`), redondeo de `duration` y `mb_used` hacia arriba con `math.ceil` según reglas del negocio.
- Genera métricas mensuales por usuario: conteo de llamadas, minutos totales, mensajes totales, MB totales.
- Une resúmenes mensuales y enriquece con información de usuarios y planes.
- Calcula ingresos por usuario-mes con tarifas del plan (mensualidad, costo por GB adicional, por mensaje y por minuto cuando aplica).
- Visualiza distribuciones (boxplots) y comparativas de ingresos por plan/mes; identifica outliers con IQR.

## Datos requeridos
- Carpeta: `Analisis_estadistico/dfs/`
- Archivos: `megaline_calls.csv`, `megaline_internet.csv`, `megaline_messages.csv`, `megaline_plans.csv`, `megaline_users.csv`
- Importante: rutas relativas sin barra inicial. Corrige la línea con `/Analisis_estadistico/dfs/megaline_messages.csv` a `Analisis_estadistico/dfs/megaline_messages.csv`.

## Flujo de trabajo (resumen)
- Carga → inspección de tipos/nulos/duplicados.
- Transformaciones: `ceil` en duraciones/MB, extracción de mes.
- Agregación por `user_id, month` y merge de tablas auxiliares.
- Cálculo de `total_income_by_user` y análisis por plan/ciudad.
- Detección de outliers por IQR y conteo por plan.

## Dependencias y ejecución
- Python 3.10+, pandas, numpy, math, matplotlib, seaborn, Jupyter.
- Ejecuta `notebook.ipynb` en orden. Para rutas robustas:
  ```python
  from pathlib import Path
  base = Path('Analisis_estadistico') / 'dfs'
  calls = pd.read_csv(base / 'megaline_calls.csv')
  ```

## Salidas esperadas
- `user_summary` mensual con ingresos y métricas de uso.
- Boxplots de ingresos por plan/mes y comparativas.
- Estadísticos `info()` y `describe()` de cada dataset.
