# Gestión de Riesgos y Cronograma de Proyecto

Este documento detalla la identificación de riesgos técnicos, operativos y regulatorios del proyecto clínico, junto con su plan de mitigación y la estructura temporal estimada.

---

## 1. Matriz de Riesgos (Risk Matrix)

El análisis de riesgos abarca desde la calidad de los datos de salud hasta el cumplimiento de las normativas de privacidad vigentes.

| ID | Categoría | Descripción del Riesgo | Impacto | Probabilidad | Plan de Mitigación |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **R01** | Técnico (Datos) | **Desbalanceo crítico de clases:** Muy pocas readmisiones en el dataset histórico en comparación con las altas comunes. | Alto | Alta | Aplicar técnicas de remuestreo estadístico (SMOTE) o ajustar pesos de clase en el algoritmo de Machine Learning durante el Sprint 2. |
| **R02** | Regulatorio | **Violación de Privacidad de Datos:** Filtración involuntaria de Datos Personales de Salud (HC, nombres, identificaciones). | Crítico | Baja | Implementar un pipeline de anonimización estricta en la fase de extracción SQL, eliminando o encriptando identificadores directos antes de pasar a Python. |
| **R03** | Técnico (Calidad)| **Valores faltantes o inconsistencias en registros médicos:** Datos de laboratorio o signos vitales sin registrar. | Medio | Alta | Diseñar reglas de imputación estadística robustas (por mediana o algoritmos KNN) basadas en la distribución del perfil clínico del paciente. |
| **R04** | Operativo | **Resistencia al cambio del personal médico:** Que los directores o médicos no confíen en las alertas predictivas del tablero. | Alto | Media | Incluir métricas de explicabilidad del modelo (SHAP o LIME) en la presentación final para que el cuerpo médico entienda *por qué* el modelo clasifica a un paciente como de alto riesgo. |

---

## 2. Cronograma Tentativo y Estimación (Gantt Conceptual)

El desarrollo completo contempla un horizonte de **6 semanas estructuradas**, divididas de la siguiente manera:

### Semanas 1 y 2: Fase de Infraestructura y Datos (Sprint 1)
* **Días 1-4:** Diseño y validación de consultas SQL para extracción limpia.
* **Días 5-10:** Desarrollo del script de limpieza automatizado (`cleaning_pipeline.py`).
* **Hito 1:** Dataset maestro anonimizado y limpio disponible para modelado.

### Semanas 3 y 4: Fase de Análisis Avanzado y Modelado (Sprint 2)
* **Días 11-14:** Ejecución del EDA estadístico y validación de hipótesis biomédicas.
* **Días 15-20:** Ingeniería de variables y entrenamiento de algoritmos clasificadores.
* **Hito 2:** Modelo entrenado con métricas técnicas validadas (ROC-AUC > 0.82).

### Semanas 5 y 6: Fase de Despliegue, ROI y Cierre (Sprint 3 / Unidad 5)
* **Días 21-25:** Diseño de la arquitectura de MLOps y simulación de monitoreo continuo (Data Drift).
* **Días 26-30:** Cálculo del ROI del proyecto y armado de la estructura de Storytelling de negocio.
* **Hito Final:** Entrega del monorepo integrado y defensa ejecutiva del proyecto.
