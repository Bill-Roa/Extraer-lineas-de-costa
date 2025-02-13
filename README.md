# Extracción de la Línea de Costa usando Google Earth Engine en Google Colab

## Descripción
Este script en **Python** utiliza la API de **Google Earth Engine (GEE)** en **Google Colab** para procesar imágenes de Sentinel-2, detectar cuerpos de agua mediante el índice AWEI y extraer la línea de costa a lo largo de los años 2015-2024.

## Requisitos
- Cuenta en Google Earth Engine.
- Acceso a Google Drive para guardar los resultados.
- Google Colab con las siguientes librerías instaladas:
  - `earthengine-api`
  - `geemap`
  - `numpy`
  - `skimage`

## Instalación
Ejecutar en Google Colab:
```python
!pip install earthengine-api geemap numpy scikit-image
```

## Uso
1. **Autenticar GEE**: Ejecuta el script y sigue las instrucciones de autenticación.
2. **Procesamiento de imágenes**:
   - Se filtran imágenes de Sentinel-2 con menos del 30% de nubosidad.
   - Se calcula el índice AWEI para detección de agua.
   - Se usa umbralización de Otsu para clasificar agua y tierra.
   - Se eliminan cuerpos de agua menores a 4000 m² y islas menores a 1000 m².
   - Se extrae el contorno de la línea de costa.
3. **Exportación de datos**:
   - Imágenes rasterizadas (límites agua-tierra).
   - Líneas vectoriales de la línea de costa.
   - Guardado en Google Drive en formato **SHP y GeoTIFF**.

## Resultados
- Mapas de agua y línea de costa visualizables en **geemap**.
- Archivos exportados a Google Drive en `coastlines/`.

## Créditos
Desarrollado para la extracción de costas con Google Earth Engine en Google Colab.

