# Analisis Inmobiliario CABA (Departamentos)

Proyecto de mineria de datos para analizar avisos de departamentos en CABA, enfocado en:
- venta
- alquiler

El flujo principal esta orientado a notebooks y prepara datos para EDA y reglas de asociacion.

## Alcance

- Solo departamentos (`type_building = departamentos`)
- Solo operaciones de venta y alquiler
- Excluye locales y oficinas del flujo principal

## Estructura del proyecto

- `notebooks/01_carga.ipynb`: ingesta y carga inicial
- `notebooks/02_analisis_de_datos.ipynb`: limpieza y analisis exploratorio
- `notebooks/03_enriquecimiento_con_mapas.ipynb`: enriquecimiento geografico
- `notebooks/outputs/`: salidas intermedias y tablas
- `docker/`: entorno reproducible para ejecutar notebooks

## Requisitos

- Python 3.10+
- Dependencias en `docker/requirements-notebook.txt`
- Recomendado: ejecutar con Docker para evitar problemas de entorno

## Ejecucion rapida (Docker)

1. Construir y levantar el entorno:

```bash
docker compose -f docker-compose.notebook.yml up --build
```

2. Abrir Jupyter y ejecutar notebooks en orden:
- 01_carga.ipynb
- 02_analisis_de_datos.ipynb
- 03_enriquecimiento_con_mapas.ipynb

## Datos de entrada

En la raiz del proyecto:
- `venta_departamentos_consolidado.csv`
- `alquiler_departamentos_consolidado.csv`

Fuentes complementarias y salidas dentro de `notebooks/datos/` y `notebooks/outputs/`.

## Criterios de calidad (resumen)

- Eliminar `price_val` nulo o <= 0
- Eliminar `surface_total` nula o <= 0
- Filtrar outliers extremos en `price_m2`
- Normalizar barrio para joins
- Reportar cobertura de joins barrio/comuna

## Entregables esperados

- Dataset final enriquecido (CSV o Parquet)
- Diccionario de variables
- Tabla de calidad y cobertura de joins
- Reglas de asociacion ordenadas por lift y confidence
- Resumen interpretativo de hallazgos
