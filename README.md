# Análisis y modelado de vulnerabilidad ante riesgos naturales en Quito

<div align="center">
  <img src="https://i.imgur.com/y1wJk3s.jpeg" width="600" alt="Quito City"/>
</div>

### Proyecto de análisis geoespacial con Python, SIG y modelado espacial predictivo

## Contenido
* 1 Introducción
* 2 Importación de Librerías
* 3 Carga y Descripción Inicial de Datos
* 4 Preprocesamiento y Transformación de Datos (ETL)
  * 4.1 Conversión de TXT a CSV con Pandas
  * 4.2 Limpieza de Datos](4.2-Limpieza-de-Datos)
  * 4.3 Ingeniería de Características (Feature Engineering)
* 5 Integración de Datasets y Análisis Exploratorio Espacial
* 6 Modelado Predictivo de Riesgo
* 7 Visualización Detallada de Resultados
* 8 Conclusiones y Recomendaciones
* 9 Referencias

## 1. **Introducción**

La ciudad de Quito, capital de Ecuador, se encuentra en una zona geográfica compleja caracterizada por su relieve montañoso, su ubicación en el Cinturón de Fuego del Pacífico y su diversidad climática. Estas condiciones naturales hacen que la urbe esté expuesta a diferentes amenazas ambientales que ponen en riesgo a su población, infraestructura y ecosistemas urbanos.

Entre las amenazas más relevantes destacan:

- **Sismos:** Quito se ubica sobre una zona sísmicamente activa debido a la interacción de las placas tectónicas de Nazca y Sudamericana. Los movimientos telúricos representan uno de los mayores riesgos para la ciudad, especialmente en áreas con suelos blandos o edificaciones vulnerables.
- **Inundaciones:** Las precipitaciones intensas, combinadas con la expansión urbana y la deforestación de las laderas, incrementan la probabilidad de desbordamientos de quebradas y anegamientos en sectores bajos.
- **Olas de calor:** El cambio climático ha provocado un aumento de las temperaturas y una mayor frecuencia de eventos extremos, afectando la salud pública, la calidad del aire y el confort térmico en zonas densamente pobladas.

Frente a este contexto, resulta fundamental identificar las zonas más vulnerables de Quito mediante el uso de herramientas tecnológicas que integren información geográfica, estadística y ambiental. La programación en **Python** y los **Sistemas de Información Geográfica (SIG)** permiten analizar grandes volúmenes de datos espaciales y construir modelos predictivos que ayuden a la toma de decisiones basadas en evidencia.

Este proyecto busca aplicar técnicas de **análisis espacial y modelado predictivo** para generar un **mapa de vulnerabilidad ante riesgos naturales en Quito**, integrando diversas fuentes de datos abiertos.

### **Objetivo general:**
Analizar e identificar las zonas más vulnerables de Quito frente a amenazas naturales como sismos, inundaciones y olas de calor, utilizando herramientas de programación en Python, sistemas de información geográfica (SIG) y técnicas de modelado espacial para generar un mapa predictivo de riesgo y una visualización interactiva que facilite la interpretación de resultados. 

### **Objetivos específicos:**
1. **Explorar y limpiar datasets abiertos** sobre peligros naturales (sísmicos, hidrológicos y climáticos) y características geográficas del Distrito Metropolitano de Quito.

2. **Integrar y georreferenciar capas de información** (geológica, hidrológica, topográfica, demográfica y climática) en un entorno de análisis geoespacial utilizando Python y librerías como `geopandas` y `rasterio`.

3. **Calcular indicadores de riesgo** combinando variables de amenaza, exposición y vulnerabilidad para cada zona o parroquia de Quito.

4. **Aplicar un modelo espacial predictivo** (por ejemplo, Random Forest espacial o Regresión logística geográfica) para estimar la probabilidad de riesgo en función de las características del terreno y los eventos históricos.

5. **Diseñar una visualización interactiva** de los resultados en Google Colab o mediante mapas dinámicos con `folium`o `plotly`, facilitando la interpretación de las áreas de mayor vulnerabilidad.
