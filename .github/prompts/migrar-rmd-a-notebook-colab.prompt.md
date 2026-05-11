---
description: "Usar cuando se necesite migrar TP_Analisis_Brambilla_base.Rmd a una notebook Python lista para Colab, manteniendo alcance solo departamentos venta/alquiler."
---

# Migrar Rmd a Notebook Colab

Objetivo:
Convertir el flujo analitico de [TP_Analisis_Brambilla_base.Rmd](../../TP_Analisis_Brambilla_base.Rmd) a notebook de Python, preparada para ejecutar en Colab, respetando la especificacion de [claude.md](../../claude.md).

Entradas esperadas:
- Dataset principal en raiz:
  - [venta_departamentos_consolidado.csv](../../venta_departamentos_consolidado.csv)
  - [alquiler_departamentos_consolidado.csv](../../alquiler_departamentos_consolidado.csv)
- Fuentes complementarias en [datos](../../datos).

Reglas obligatorias:
1. Priorizar [claude.md](../../claude.md) si existe conflicto con el contenido legado del Rmd.
2. Excluir locales y oficinas del flujo principal.
3. Usar rutas relativas; no usar setwd ni paths absolutos locales.
4. Mantener politica de moneda vigente (descartar Consultar, ARS como TODO explicito).

Salida esperada:
- Notebook en Python con celdas ordenadas por etapas:
  1) ingesta
  2) limpieza
  3) enriquecimiento
  4) features
  5) reglas de asociacion
- Guardado de artefactos intermedios en csv/parquet.
- Resumen final de conversion: que se migro, que se descarto y que queda como TODO.

Checklist de validacion:
- Se mantienen solo departamentos de venta/alquiler.
- No quedan referencias a archivos inexistentes de locales/oficinas.
- El notebook corre de principio a fin sin depender de rutas de Windows.
- Las suposiciones (moneda, discretizacion, cobertura de joins) quedan documentadas en markdown.
