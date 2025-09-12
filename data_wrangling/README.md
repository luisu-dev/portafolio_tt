# Data Wrangling — Instacart

## Qué hace este notebook
- Carga 5 archivos principales (`orders`, `order_products`, `products`, `aisles`, `departments`) desde `data_wrangling/dfs/` usando `sep=';'`.
- Inspección y control de calidad: `info()`, `head()`, conteos de nulos y duplicados por tabla y por columna clave.
- Verificaciones de unicidad: IDs duplicados en `order_id`, `product_id`, `department_id`, `aisle_id` y nombres duplicados en `product_name`.
- Limpieza: eliminación de duplicados totales cuando corresponde.
- Opcional: uniones básicas para explorar consistencia entre catálogos (productos/aisles/departments).

## Datos requeridos
- Carpeta: `data_wrangling/dfs/` con CSVs mencionados.
- Ajusta `sep` si tus archivos no usan `;`.

## Flujo de trabajo (resumen)
- Carga → `info`/`head` → duplicados → correcciones → validaciones de consistencia.

## Dependencias y ejecución
- Python 3.10+, pandas, numpy, matplotlib, Jupyter.
- Abre `data_wrangling.ipynb` y ejecuta en orden. Para rutas robustas:
  ```python
  from pathlib import Path
  base = Path('data_wrangling') / 'dfs'
  orders = pd.read_csv(base / 'orders.csv', sep=';')
  ```

## Salidas esperadas
- Reporte de duplicados y nulos por dataset.
- Tablas de verificación de claves y consistencia entre catálogos.
