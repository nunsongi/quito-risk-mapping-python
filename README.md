# Análisis y modelado de vulnerabilidad ante riesgos naturales en Quito

<div align="center">
  <img src="https://i.imgur.com/y1wJk3s.jpeg" width="600" alt="Quito City"/>
</div>

### Proyecto geoespacial con Python, SIG y modelado espacial predictivo

## Contenido

1. Introducción y Alcance
2. Fuentes, Insumos y Esquema de Datos
3. Configuración del Entorno y Librerías
4. Carga de Datos (CSV) y Validación Rápida
5. Preparación Espacial
6. Análisis Exploratorio Espacial (EDA)
7. Ingeniería de Características
8. Modelado Predictivo de Riesgo
9. Evaluación, Interpretabilidad y Incertidumbre
10. Visualizaciones y Mapas Interactivos
11. Conclusiones, Limitaciones y Recomendaciones
12. Referencias

---

## 1. Introducción

Quito se asienta en un entorno andino, sísmicamente activo y con climas variables que incrementan la **exposición a sismos, inundaciones y olas de calor**. La combinación de **Python** y **Sistemas de Información Geográfica (SIG)** permite integrar capas geológicas, hidrológicas, topográficas y demográficas para **cuantificar y mapear la vulnerabilidad** a nivel urbano.

**Utilidad del proyecto**

* **Prioriza intervenciones** (obras, mantenimiento, alertas) en zonas críticas.
* **Soporta decisiones** de gestión de riesgos y ordenamiento territorial.
* **Comunica evidencia** a autoridades y comunidad mediante mapas y tableros interactivos.

### Objetivo general

Generar un **mapa de vulnerabilidad ante riesgos naturales** en Quito (sismos, inundaciones, olas de calor) mediante análisis geoespacial en Python y modelos predictivos, con visualizaciones interactivas para facilitar la toma de decisiones.

### Objetivos específicos (concisos)

1. **Curar y unificar datos abiertos** de peligros naturales y contexto territorial del DMQ.
2. **Integrar y georreferenciar capas** (geología, hidrología, topografía, clima y demografía) con `geopandas`/`rasterio`.
3. **Construir indicadores de riesgo** combinando amenaza, exposición y vulnerabilidad por zona/parroquia.
4. **Entrenar modelos espaciales** (p. ej., Random Forest o Regresión logística geográfica) para estimar probabilidad de riesgo.
5. **Publicar visualizaciones interactivas** (`folium`/`plotly`) y un informe reproducible en Colab.

> Resultado esperado: un **pipeline reproducible** (ETL → features → modelos → mapas) que entregue **insumos prácticos** para planificación urbana, gestión de emergencias y comunicación pública.

## 📂 Sismos: Catálogos de Eventos Sísmicos

### ✨ Origen y Propósito

Los datos iniciales provienen de los **Catálogos Sísmicos – IG-EPN** (formato `.txt`).
El notebook **`Limpieza_Sismos.ipynb`** procesa y limpia estos catálogos con el objetivo de obtener un conjunto de datos **filtrado geográficamente** que incluya solo los eventos sísmicos dentro de la ciudad de **Quito**.

---

### 🧹 Proceso de Limpieza (`Limpieza_Sismos.ipynb`)

Este script transforma los datos crudos a **CSV listos para el análisis**.

**Pasos principales:**

* **Manejo de duplicados:** eliminación y resolución de inconsistencias en los registros.
* **Conversión de tipos:**

  * Fechas y tiempos → `datetime`
  * Magnitudes y coordenadas → numéricos (`float`)
* **Manejo de faltantes (NaN):** tratamiento de valores nulos.
* **Filtros de correspondencia:** se validaron **Magnitudes** y **Picks** para asegurar su correspondencia con **Orígenes** dentro de Quito.

---

### 🗺️ Filtro Geográfico Aplicado (Quito)

Se aplicó un filtro espacial para los eventos ubicados dentro de los siguientes límites:

| Coordenada   | Límite Mínimo | Límite Máximo |
| ------------ | ------------: | ------------: |
| **Latitud**  |     **-0.50** |     **-0.05** |
| **Longitud** |    **-78.80** |    **-78.20** |

---

### 🛠️ Limpieza de Datos Clave

* **Duplicados:** detectados y removidos/resueltos.
* **Tipos de datos:**

  * `fecha_hora` → `datetime`
  * `magnitud`, `latitud`, `longitud`, `profundidad` → `float`
* **Valores faltantes:** imputación/eliminación según el caso y la variable.
* **Integridad relacional:** se mantuvo consistencia entre tablas (orígenes ↔ magnitudes ↔ picks) **solo** para eventos dentro del área de Quito.

---

### 📊 Resultados y Archivos Exportados

Volúmenes finales para la zona de interés, exportados en formato **CSV**:

| Conjunto de Datos           | Registros Filtrados | Archivo Exportado      |
| --------------------------- | ------------------: | ---------------------- |
| **Orígenes de Sismos**      |              **18** | `quito_origins.csv`    |
| **Registros de Magnitud**   |              **77** | `quito_magnitudes.csv` |
| **Tiempos de Onda (Picks)** |            **1514** | `quito_picks.csv`      |

