# Instrucciones de Copilot para este proyecto

## Proposito
Este workspace implementa un flujo de analisis inmobiliario de CABA en Python, enfocado solo en departamentos para venta y alquiler, con salida final apta para EDA y reglas de asociacion.

## Leer primero
- Especificacion funcional y metodologica: [claude.md](../claude.md)
- Material legado (usar con cautela): [TP_Analisis_Brambilla_base.Rmd](../TP_Analisis_Brambilla_base.Rmd)

## Regla de precedencia documental
Si hay conflicto entre documentos, prevalece [claude.md](../claude.md).
El archivo [TP_Analisis_Brambilla_base.Rmd](../TP_Analisis_Brambilla_base.Rmd) contiene partes historicas (por ejemplo, locales/oficinas y rutas absolutas) que no deben guiar el flujo principal nuevo.

## Alcance no negociable
- Incluir solo propiedades con type_building = departamentos.
- Incluir solo type_operation en {venta, alquiler}.
- Excluir locales y oficinas del flujo principal.

## Estructura de datos del workspace
- Dataset principal en raiz:
  - [venta_departamentos_consolidado.csv](../venta_departamentos_consolidado.csv)
  - [alquiler_departamentos_consolidado.csv](../alquiler_departamentos_consolidado.csv)
- Fuentes complementarias en carpeta [datos](../datos): censales, comunas/barrios y planillas de mercado.

## Politica de moneda
- Priorizar USD.
- Descartar registros con moneda Consultar.
- ARS: decision pendiente (TODO explicito). No asumir conversion sin regla formal documentada.

## Reglas minimas de calidad
- Eliminar price_val nulo o <= 0.
- Eliminar surface_total nula o <= 0.
- Filtrar outliers extremos de price_m2 con criterio robusto (percentiles o IQR).
- Normalizar barrio antes de joins (por ejemplo: trim, lower, sin acentos).
- Reportar cobertura de join barrio/comuna y porcentaje de no-match.

## Enriquecimiento y granularidad
- Respetar granularidad real de cada fuente.
- pct_65_mas_comuna se usa por comuna, no por barrio.
- Documentar supuestos de periodo, discretizacion y cobertura.

## Flujo notebook-first (objetivo Colab)
- Priorizar implementacion en notebook para facilitar migracion a Colab.
- Usar rutas relativas, nunca rutas absolutas locales.
- Separar el notebook por etapas reproducibles:
  1) ingesta
  2) limpieza
  3) enriquecimiento
  4) features
  5) reglas de asociacion
- Guardar salidas intermedias en formatos portables (csv/parquet).

## Entregables esperados
- Dataset final enriquecido (csv o parquet).
- Diccionario de variables finales.
- Tabla de calidad y cobertura de joins.
- Reglas de asociacion ordenadas por lift y confidence.
- Resumen interpretativo de hallazgos.
