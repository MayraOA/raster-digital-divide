# Raster Digital Divide — Análisis Geoespacial de la Brecha Digital en Cusco

## Descripción y pregunta de investigación

Este proyecto analiza la **brecha digital territorial** en la región Cusco, Perú,
cruzando dos capas raster satelitales: luminosidad nocturna NASA Black Marble VNL 2025
(proxy de urbanización) y densidad de cobertura de red móvil OSIPTEL 2019 (proxy de
acceso a internet). **¿Qué tan desigual es el acceso digital en la región Cusco y qué
zonas deben priorizarse para políticas de conectividad?**

## Dependencias e instalación

```bash
pip install -r requirements.txt
```

## Datos de entrada

Descargar los archivos raster del repositorio del curso y colocarlos en `data/`:

```bash
# Desde el repo del curso:
# https://github.com/d2cml-ai/Data-Science-Python/tree/main/_data/Raster_2026/
```

| Archivo | Descripción | CRS |
|---------|-------------|-----|
| `VNL_cusco_2025.tif` | Luminosidad nocturna NASA (nW·cm⁻²·sr⁻¹) | EPSG:4326 |
| `kernel_cobmovil2019_50m.tif` | Cobertura móvil OSIPTEL kernel 50m | EPSG:32719 |

## Cómo ejecutar el notebook

```bash
cd notebooks
jupyter notebook digital_divide_cusco.ipynb
```

Ejecutar todas las celdas en orden (Kernel → Restart & Run All).

## Archivos de salida (`output/`)

| Archivo | Descripción |
|---------|-------------|
| `vnl_norm.tif` | Luminosidad VNL normalizada [0, 1] |
| `conn_norm.tif` | Conectividad normalizada [0, 1] |
| `ibd_brecha_digital.tif` | Índice de Brecha Digital IBD [-1, 1] |
| `clasificacion_brecha.tif` | Clasificación territorial 4 categorías |
| `dashboard_brecha_digital.png` | Dashboard compuesto final (6 mapas) |

## Hallazgos principales

El 96.97% del territorio de Cusco corresponde a la clase "Critical Divide" (sin luz ni
conectividad), mientras que solo el 0.20% es "Urban Connected". La clase "Urban Divide"
(0.27%) revela zonas con actividad económica pero sin cobertura móvil, donde la
intervención es más urgente. La correlación de Pearson entre VNL y conectividad es
r=0.31 (p≈0), confirmando que el acceso digital sigue concentrado en los mismos núcleos
urbanos que ya cuentan con electrificación.