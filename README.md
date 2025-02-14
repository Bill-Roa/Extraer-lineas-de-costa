# **Guía para la Ejecución del Código en Google Earth Engine**

Este documento consolida las instrucciones esenciales para modificar y ejecutar el código de detección de cuerpos de agua y extracción de línea de costa usando Google Earth Engine (GEE). Sigue estos pasos para garantizar una correcta configuración y adaptación del script a tus necesidades.

---

## **1. Ajustes de Configuración**
Antes de ejecutar el código, revisa y modifica los siguientes parámetros según el proyecto:

### **1.1 Parámetros Generales**
```javascript
var exportResolutionMeters = 10; // Resolución de exportación en metros (ajustar según necesidad)
var waterbodySizeMeters = 4000;  // Tamaño mínimo de cuerpos de agua en metros
var islandSizeMeters = 1000;  // Tamaño mínimo de islas en metros
```

### **1.2 Rango de Años a Analizar**
El script procesa imágenes desde 2024 hasta 2015. Puedes ajustar este rango modificando la siguiente línea:
```javascript
for (var year = 2024; year >= 2015; year--) {
```

### **1.3 Ubicación de Análisis (Geometría de Estudio)**
El script requiere definir una **geometría de análisis** llamada `geometry`. Es fundamental asegurarse de que esta variable esté definida antes de ejecutar el código.
```javascript
.filter(ee.Filter.bounds(geometry))
.clip(geometry);
```
Si `geometry` no está definida, usa `var geometry = ee.Geometry.Polygon([...]);` con las coordenadas de la región de estudio.

---

## **2. Filtros de Preprocesamiento**
El script aplica los siguientes filtros a la colección de imágenes Sentinel-2:
- **Fecha:** Se seleccionan imágenes dentro del primer trimestre de cada año.
- **Cobertura de nubes:** Solo imágenes con menos del 30% de nubes.
- **Ubicación:** Se filtran imágenes dentro de la geometría de estudio.

Si necesitas modificar el porcentaje de nubes permitido, cambia este valor:
```javascript
.filter(ee.Filter.lt('CLOUDY_PIXEL_PERCENTAGE', 30));
```

---

## **3. Consideraciones Finales**
- **Asegúrate de definir la variable `geometry` correctamente antes de ejecutar el código.**
- **Verifica los valores de los umbrales y ajustes de resolución.**
- **Si el código genera errores, revisa los filtros y asegurarte de que Sentinel-2 tenga datos disponibles para la zona y el período seleccionado.**

Con estos pasos, puedes adaptar y ejecutar el script eficientemente en Google Earth Engine. ¡Buena suerte con tu análisis! 🚀

