
# 🌧️ Análisis y modelado de riesgo por lluvias intensas en Quito con Python y SIG

<div align="center">
  <img src="https://i.imgur.com/y1wJk3s.jpeg" width="600" alt="Quito City"/>
</div>

> Proyecto de análisis geoespacial que utiliza datos históricos de precipitación y capas territoriales del Distrito Metropolitano de Quito para construir un **mapa de riesgo asociado a lluvias intensas**, usando Python, `pandas`, `geopandas` y herramientas de visualización.

---

## 📚 Contenido

1. [Introducción y Alcance](#1-introducción-y-alcance)  
2. [Objetivo General](#2-objetivo-general)  
3. [Objetivos Específicos](#3-objetivos-específicos)  
4. [Alcance del Proyecto](#4-alcance-del-proyecto)  
5. [Fuentes de Datos](#5-fuentes-de-datos)  
6. [Estructura del Repositorio](#6-estructura-del-repositorio)  
7. [Tecnologías y Librerías](#7-tecnologías-y-librerías)  
8. [Cómo Reproducir el Análisis](#8-cómo-reproducir-el-análisis)  
9. [Estado Actual y Trabajo Futuro](#9-estado-actual-y-trabajo-futuro)  
10. [Referencias](#10-referencias)  

---

## 1. Introducción y Alcance

Quito, capital de Ecuador, se ubica en un entorno andino con **fuerte variabilidad climática** y eventos de lluvia intensa, especialmente en ciertas épocas del año. La combinación de **pendientes pronunciadas**, **expansión urbana sobre laderas** y **sistemas de drenaje limitados** incrementa el riesgo de **inundaciones** y **anegamientos** en varios barrios del Distrito Metropolitano.

Las lluvias extremas pueden afectar viviendas, vías, servicios básicos y, en general, la calidad de vida de la población, especialmente en las zonas más vulnerables. Contar con un **análisis espacial de la precipitación** y un **mapa de riesgo asociado a lluvias** es clave para:

- priorizar obras e intervenciones de drenaje,
- diseñar sistemas de alerta temprana,
- y apoyar la planificación urbana y la gestión del riesgo climático.

Este proyecto integra datos históricos de **precipitación** con información geográfica del **Distrito Metropolitano de Quito (DMQ)** mediante Python y Sistemas de Información Geográfica (SIG), construyendo indicadores e índices de riesgo a nivel espacial.

---

## 2. Objetivo General

Generar un **mapa de riesgo asociado a lluvias intensas en Quito** mediante análisis geoespacial en Python, utilizando datos históricos de precipitación y capas territoriales del DMQ, con **visualizaciones estáticas e interactivas** que ayuden a interpretar las zonas más vulnerables.

---

## 3. Objetivos Específicos

1. **Curar y unificar datasets abiertos de precipitación** (INAMHI u otras fuentes) y recortar la información al área del Distrito Metropolitano de Quito.  
2. **Integrar y georreferenciar capas** de estaciones meteorológicas y límites administrativos (parroquias/zonas) con `geopandas`.  
3. **Calcular indicadores de lluvia** (por ejemplo, precipitación total anual, máxima mensual, percentiles extremos) por estación y por zona.  
4. **Construir un índice de riesgo por lluvias** combinando intensidad de precipitación y exposición territorial (por ejemplo, zonas urbanas densas).  
5. **Publicar mapas y visualizaciones** (con `matplotlib`, `geopandas` y, de ser posible, `folium` o `plotly`) junto a un **pipeline reproducible**:  
   `carga de datos → limpieza (ETL) → indicadores → unión espacial → mapas`.

---

## 4. Alcance del Proyecto

- **Unidad de análisis:**  
  - Estaciones meteorológicas de la red de INAMHI.  
  - Parroquias y/o zonas urbanas del DMQ (según las capas de límites utilizadas).

- **Salidas principales:**  
  - Mapa temático de **riesgo por lluvias intensas** en Quito.  
  - Tablas con indicadores de precipitación y riesgo por estación / parroquia.  

- **Uso previsto:**  
  - Planificación urbana y priorización de obras de drenaje.  
  - Soporte para estudios de inundaciones y resiliencia climática.  
  - Comunicación de riesgo climático a tomadores de decisión y ciudadanía.

---

## 5. Fuentes de Datos

Los datos utilizados en este proyecto provienen de instituciones oficiales de Ecuador:

- **Precipitación (lluvias):**  
  - Instituto Nacional de Meteorología e Hidrología (**INAMHI**)  
  - Archivo base: series históricas de precipitación mensual por estación.  

- **Información geográfica y límites administrativos:**  
  - Capas de límites del Distrito Metropolitano de Quito (parroquias / zonas urbanas).  

---

# Análisis y modelado de vulnerabilidad ante riesgos naturales en Quito (proyecto experimental)

Este proyecto nació originalmente como un **análisis multirriesgo** para Quito (sismos, inundaciones y olas de calor) bajo el título:

> **Análisis y modelado de vulnerabilidad ante riesgos naturales en Quito**

Sin embargo, debido a la **limitada disponibilidad de datos suficientes y consistentes** para algunos peligros (especialmente sismos y olas de calor), el enfoque principal del repositorio se ha reorientado hacia el **riesgo asociado a lluvias intensas**.  

Aun así, se conservan los notebooks y datasets sísmicos como parte de un **experimento previo** centrado en la ciudad de Quito.

---

## 📂 Sismos (componente experimental para Quito)

Los datos de sismos utilizados provienen de los **Catálogos Sísmicos del IG-EPN** (formato `.txt`).  
El notebook `Limpieza_Sismos.ipynb` realiza un procesamiento preliminar para obtener eventos **filtrados geográficamente** dentro del área de Quito, aplicando:

- Conversión de tipos (`datetime`, `float`).
- Manejo de valores faltantes.
- Filtros espaciales aproximados para la ciudad de Quito.

Como resultado, se generaron estos archivos CSV para la zona de Quito:

| Conjunto de Datos           | Archivo Exportado      |
| --------------------------- | ---------------------- |
| **Orígenes de Sismos**      | `quito_origins.csv`    |
| **Registros de Magnitud**   | `quito_magnitudes.csv` |
| **Tiempos de Onda (Picks)** | `quito_picks.csv`      |

> Debido al **bajo número de eventos sísmicos disponibles para el área de Quito**, esta parte del proyecto se mantiene solo como **exploración experimental** y no se desarrolló un modelo predictivo robusto. El foco actual del repositorio es el **riesgo por lluvias intensas**.

Este repositorio incluye también un módulo experimental con datos sísmicos para Quito, documentado en Limpieza_Sismos.ipynb.
