# Guía de Inicio Rápido: Hub de Papers

Este documento te explica cómo poner en marcha tu hub de revisiones y cómo visualizarlo.

## 1. Instalación de Quarto

Para poder "correr" este proyecto visualmente, necesitas instalar **Quarto**.

1. Descarga el instalador para macOS desde el sitio oficial: [quarto.org/docs/get-started/](https://quarto.org/docs/get-started/)
2. Instala el paquete `.pkg`.
3. (Opcional) Si usas VS Code, instala la extensión oficial de **Quarto**.

## 2. Cómo previsualizar el libro

Una vez instalado Quarto, abre tu terminal en la carpeta del proyecto y ejecuta:

```bash
quarto preview
```

### ¿Qué hace este comando?
- Abre una ventana en tu navegador con el libro interactivo.
- Se actualiza **automáticamente** cada vez que guardas cambios en un archivo `.qmd`.

## 3. Cómo agregar un nuevo Paper

1. Crea un nuevo archivo `.qmd` (puedes copiar `ejemplo_analisis.qmd` o usar `template_paper.qmd` que está en el repo).
2. Escribe tu análisis.
3. Agrégalo a la estructura en el archivo `_quarto.yml` bajo la sección `chapters`.

Ejemplo en `_quarto.yml`:
```yaml
chapters:
  - index.qmd
  - intro.qmd
  - part: "Mis Revisiones"
    chapters:
      - mi-nuevo-paper.qmd
```

## 4. Personalización básica

En `_quarto.yml` puedes cambiar los siguientes campos para que el libro sea tuyo:
- `title`: El título de tu hub.
- `author`: Tu nombre y datos.
- `page-footer`: El texto al pie de cada página.
