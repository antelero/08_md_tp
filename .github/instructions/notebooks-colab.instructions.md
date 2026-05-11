---
applyTo: "**/*.ipynb"
description: "Convenciones para crear o editar notebooks de este proyecto con compatibilidad Colab y foco en departamentos venta/alquiler."
---

# Convenciones de Notebook (Colab)

## Contexto obligatorio
- Seguir [claude.md](../../claude.md) como fuente principal.
- Tomar [TP_Analisis_Brambilla_base.Rmd](../../TP_Analisis_Brambilla_base.Rmd) solo como referencia historica.

## Reglas de alcance
- Incluir solo departamentos en venta y alquiler.
- Excluir locales/oficinas en filtros, joins y reportes.

## Estructura minima de celdas
1. Configuracion e imports.
2. Ingesta de datos base (archivos de raiz).
3. Limpieza y estandarizacion.
4. Enriquecimiento con fuentes de [datos](../../datos).
5. Feature engineering y discretizacion.
6. Reglas de asociacion y exportes.
7. Resumen de calidad y cobertura.

## Reglas de portabilidad
- Usar rutas relativas con pathlib.
- No usar rutas absolutas de Windows.
- Evitar dependencias de estado local no reproducible.

## Reglas de calidad
- Validar price_val y surface_total positivos antes de modelar.
- Medir no-match de joins barrio/comuna.
- Documentar outliers removidos y criterio usado.

## Moneda
- Descartar moneda Consultar.
- Mantener ARS como decision pendiente hasta que haya regla formal de conversion.
