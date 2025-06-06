# AGENTS.md — OpenAI Codex Guide for R Quarto Data Science Projects

Este archivo `AGENTS.md` proporciona una guía detallada para OpenAI Codex y otros agentes AI que colaboren en este repositorio orientado a análisis de datos en R con enfoque académico y reproducible.

## Estructura del Proyecto para Navegación por OpenAI Codex

- `/scripts`: Scripts auxiliares en R. Codex puede analizarlos y modularizarlos.
- `/Datos`: Archivos `.csv` u otras fuentes de datos utilizadas. Codex no debe editarlos.
- `/docs` o `/reportes`: Documentos Quarto (`.qmd`) que Codex debe compilar y validar.
- `/models`: Modelos entrenados y artefactos serializados (por ejemplo, `.rds`).
- `/figuras`: Gráficos generados automáticamente. Codex puede sobrescribirlos si el código fuente se ejecuta.

## Convenciones de Programación para OpenAI Codex

### Estilo General de Código

- Codex debe usar `tidyverse` y `tidymodels` según las buenas prácticas del curso.
- Nombrar funciones, objetos y columnas de forma explícita y descriptiva.
- Agregar comentarios para bloques clave (preprocesamiento, entrenamiento, evaluación).
- Usar `here::here()` para rutas relativas y garantizar reproducibilidad.

### Uso de Quarto

- Los documentos `.qmd` deben tener encabezados YAML válidos y compilarse sin errores.
- Codex debe seguir la estructura: introducción, preparación de datos, análisis, modelos, conclusiones.
- Los chunks deben usar etiquetas `#| label:` y ser reproducibles al 100%.

## Reglas para Visualización

- Codex debe utilizar `ggplot2` y opcionalmente `ggpubr` o `patchwork` si hay varias figuras.
- Evitar estilos innecesarios; seguir una estética clara y profesional.
- Guardar gráficos con `ggsave()` si se especifica una ruta o se automatiza el pipeline.

## Modelado Estadístico y Machine Learning

- Codex debe utilizar `tidymodels`, con `recipe()` y `workflow()` como estructuras principales.
- El split de datos debe ser reproducible (`set.seed()`).
- Codex debe evaluar los modelos con métricas apropiadas (`accuracy`, `roc_auc`, etc.).
- El preprocesamiento debe declararse de forma explícita (imputación, normalización, dummies).
- Los modelos deben ajustarse en el set de entrenamiento y evaluarse en test o mediante validación cruzada.

## Validaciones antes de Commitear Código Generado por Codex

Antes de subir cualquier cambio, OpenAI Codex debe:

1. Asegurarse que todos los `.qmd` compilen a PDF o HTML sin error.
2. Verificar que todos los objetos, rutas y funciones estén correctamente definidos.
3. Confirmar que los resultados numéricos y gráficos se reproduzcan con `Render Document`.
4. No dejar código innecesario o chunks marcados como `eval: false`, salvo que se indique explícitamente.

## Ejecución Recomendada de Checks

```r
# Verificar entorno de trabajo reproducible
here::here()

# Comprobar dependencias
renv::status()

# Compilar todos los .qmd
quarto::quarto_render()
````

## Convenciones de Pull Requests

Cuando Codex contribuya con un Pull Request, debe:

1. Incluir un resumen claro de los cambios.
2. Adjuntar capturas o archivos generados relevantes (PDF, gráficos, modelos).
3. Indicar qué scripts o archivos `.qmd` fueron modificados.
4. Asegurar que el PR está enfocado a una sola tarea o sección del proyecto.
