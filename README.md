# Gestión de Proyecto: Planificación, Alcance y Objetivos

Este documento establece el marco de gestión ágil, el alcance técnico y los objetivos de negocio para el ecosistema de repositorios clínicos (`clinical-sql-data-extraction`, `clinical-data-cleaning-pipeline`, y `clinical-eda-statistical-modeling`).

---

## 1. Alcance del Proyecto (Project Scope)

### Problema de Negocio / Clínico
Las readmisiones hospitalarias imprevistas y la ineficiencia en la rotación de camas/insumos generan un incremento crítico en los costos operativos de la institución médica, además de impactar negativamente en los indicadores de calidad asistencial. La falta de un sistema predictivo impide una asignación proactiva de recursos y un seguimiento optimizado del paciente de alto riesgo.

### Solución Propuesta
Desarrollar e integrar un pipeline de datos de extremo a extremo que extraiga información histórica de pacientes desde un entorno SQL, limpie y transforme las variables biomédicas y administrativas, y ejecute un modelo estadístico predictivo de Machine Learning para identificar pacientes con alta probabilidad de reingreso dentro de los 30 días posteriores al alta.

### Componentes Técnicos Incluidos
* **Fase 1 (Extracción):** Módulo de consultas SQL optimizadas para bases de datos relacionales clínicas.
* **Fase 2 (Pipeline de Limpieza):** Scripts automatizados en Python para la imputación de valores faltantes, manejo de outliers clínicos y codificación de variables.
* **Fase 3 (Modelado y EDA):** Análisis exploratorio robusto, selección de variables mediante significancia estadística y entrenamiento del modelo clasificador.

---

## 2. Objetivos del Proyecto y KPIs

Para medir el éxito de la solución, se establecen metas claras divididas en el impacto de negocio y el rendimiento técnico del modelo:

### Objetivos de Negocio
* **Reducción de Readmisiones:** Disminuir en un **15%** las readmisiones hospitalarias no planificadas en un período de 6 meses post-despliegue.
* **Optimización de Costos:** Reducir los costos operativos asociados a camas críticas y penalizaciones institucionales.

### KPIs de Negocio (Key Performance Indicators)
* **Tasa de Readmisión Mensual (TRM):** `(Total de pacientes readmitidos antes de los 30 días / Total de altas del mes) * 100`
* **Costo Promedio por Paciente Readmitido (CPPR):** Medición del gasto en insumos farmacéuticos y hotelería médica por reingreso evitable.

### KPIs Técnicos (Métricas del Modelo)
* **ROC-AUC > 0.82:** Para asegurar una excelente capacidad de discriminación entre pacientes de bajo y alto riesgo.
* **Recall (Sensibilidad) > 75%:** En el ámbito clínico es prioritario minimizar los falsos negativos (pacientes de alto riesgo que el modelo no detecta).

---
## 3. Plan Técnico Inicial y Metodología Ágil

El proyecto se gestiona bajo el marco de trabajo **Scrum**, adaptado a Ciencia de Datos, estructurado en **3 Sprints de 2 semanas cada uno**:
### Estructura de Sprints

* **Sprint 1: Infraestructura de Datos y Calidad**
  * Configuración del repositorio `clinical-sql-data-extraction`.
  * Diseño de queries para perfiles demográficos, diagnósticos (CIE-10) y laboratorios.
  * Automatización del pipeline de limpieza en `clinical-data-cleaning-pipeline`.
* **Sprint 2: Análisis Estadístico y Entrenamiento**
  * Análisis exploratorio de datos (EDA) y validación de hipótesis clínicas en `clinical-eda-statistical-modeling`.
  * Ingeniería de características (Feature Engineering).
  * Entrenamiento y optimización de hiperparámetros del modelo clasificador.
* **Sprint 3: Evaluación y Cierre de Fase**
  * Validación cruzada del modelo para evitar sobreajuste (overfitting).
  * Generación del reporte de métricas técnicas.
  * Redacción de la documentación de arquitectura inicial.
