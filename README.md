
## ??? Estructura del Proyecto
El sistema se organiza en un pipeline lineal de tres etapas:
1. **Data Prep:** Ingesta de GeoJSON y extracción de chips multiespectrales (10 bandas).
2. **Inference (Clay Engine):** Generación de embeddings normalizados mediante Vision Transformer.
3. **Analytics:** Cálculo de distancias euclidianas y detección de anomalías por Z-Score.

## ?? Guía de Uso Rápido
Para replicar el análisis en un nuevo lote:

### 1. Requisitos
- Python 3.10+
- GPU compatible con CUDA (Recomendado)
- Librerías: torch, terratorch, timm, numpy, geopandas.

### 2. Configuración del Lote
Carga tu archivo .geojson en la raíz y actualiza la ruta en el script maestro:
PATH_GEOJSON = 'tu_lote.geojson'

### 3. Ejecución
Corre el script unificado para procesar la campaña:
python maestro_inferencia.py

## ?? Especificaciones del Modelo
- **Model:** vit_large_patch16_224 (Clay Foundation)
- **Input:** 10 x 224 x 224 (Sentinel-2 L2A)
- **Normalization:** Reflectancia / 10000
- **Output:** Vector latente de 1024 dimensiones.
