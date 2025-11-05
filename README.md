# Análisis y modelado de vulnerabilidad ante riesgos naturales en Quito

<div align="center">
  <img src="https://i.imgur.com/y1wJk3s.jpeg" width="600" alt="Quito City"/>
</div>

### Proyecto geoespacial con Python, SIG y modelado espacial predictivo

## Contenido

1. Introducción
2. Importación de Librerías
3. Carga y Descripción Inicial de Datos
4. Preprocesamiento y Transformación de Datos (ETL)
   4.1 Conversión de TXT a CSV con Pandas
   4.2 Limpieza de Datos
   4.3 Ingeniería de Características
5. Integración de Datasets y Análisis Exploratorio Espacial
6. Modelado Predictivo de Riesgo
7. Visualización de Resultados
8. Conclusiones y Recomendaciones
9. Referencias

---

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

