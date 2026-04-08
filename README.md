README (Español)
# Sistema de Alerta Temprana (SAT) - Violencia de Género

Este repositorio contiene el desarrollo de un Modelo de Alerta Temprana diseñado para identificar el riesgo de interrupción del proceso judicial ("No Denuncia") en casos de violencia de género.

El modelo fue desarrollado a partir de datos cedidos por la Dirección General de Género de la Municipalidad de Bahía Blanca, en el marco de la materia Aprendizaje Automático de la Especialización en Ciencia de Datos (UNLaM). El sistema es una propuesta técnica de investigación y no se encuentra en funcionamiento operativo actualmente.

El análisis permitió demostrar cómo las fallas en el registro administrativo (como la falta de datos geográficos o de vivienda) actúan como predictores críticos de la desconexión de la víctima con el sistema judicial. El valor principal del proyecto radica en:
•	Detección de Invisibilidad: Identificar que la falta de datos no es "ruido", sino una señal de vulnerabilidad.
•	Priorización de Sensibilidad: Optimizar el Recall (0.6842) para minimizar los falsos negativos en un contexto de protección humana.
•	Benchmark Técnico: Validar que un modelo lineal (Ridge Classifier) es más robusto y explicable para este tipo de datos sociales que modelos complejos de boosting (LightGBM).

# Sobre el repositorio

Este repositorio contiene el pipeline completo de datos y los modelos de Machine Learning desarrollados para un Sistema de Alerta Temprana de casos de violencia de género. 

## Sobre los Datos
El modelo fue entrenado utilizando un dataset real provisto por la Dirección General de Género del Municipio de Bahía Blanca. Todos los datos han sido **estrictamente anonimizados** para proteger la identidad y privacidad de las personas involucradas, cumpliendo con los estándares éticos para el tratamiento de información sensible.

## Arquitectura del Proyecto y Flujo de Trabajo

El proyecto está estructurado en una serie de Jupyter Notebooks que reflejan el pipeline de datos de principio a fin:

* `01_PREVISUALIZATION.ipynb`: Carga inicial del dataset, previsualización de la estructura y evaluación del estado general de los datos crudos.
* `02_Cleaning.ipynb`: Tratamiento de valores nulos, corrección de tipos de datos y estandarización de formatos.
* `03_Ing_Feat.ipynb`: Ingeniería de características (Feature Engineering). Incluye decisiones metodológicas clave como:
  * Eliminación de variables de alta cardinalidad (ej. `profesionales`) para evitar ruido en el modelo.
  * Eliminación de variables casi constantes (ej. `motivo_de_consulta`) por bajo poder predictivo.
  * Agrupación funcional de categorías en variables clave (ej. `medio_por_el_que_ingresa`) para mejorar la estabilidad estadística del algoritmo.
* `04_EDA.ipynb`: Análisis Exploratorio de Datos (EDA) profundo. Visualización de distribuciones, análisis bivariado y correlaciones entre las variables resultantes.
* `04_Modeling_1.ipynb`: Entrenamiento, validación y evaluación del modelo de Machine Learning base.
* `04_Modeling_2.ipynb`: Interpretabilidad y explicabilidad del modelo. Análisis de importancia de características (*Feature Importance*) mediante la extracción y visualización de los coeficientes del modelo Ridge. Esto permite identificar de forma transparente qué variables (como la cantidad de tipos de violencias) tienen mayor peso matemático para catalogar un caso como de alto riesgo.

## Requerimientos
* **Lenguaje:** Python 3.10+
* **Manipulación y Análisis de Datos:** `pandas`, `numpy`
* **Visualización:** `matplotlib`, `seaborn`
* **Machine Learning:** `scikit-learn`, `imbalanced-learn`

## Resultados y métricas del modelo final

Tras evaluar la predicción del nivel de riesgo, el modelo seleccionado fue un **Ridge Classifier** optimizado con **SMOTE** para manejar el desbalanceo de clases original.

Dado el contexto del problema, la métrica crítica a optimizar fue el **Recall de la clase positiva (Alto Riesgo)**, buscando minimizar a toda costa los falsos negativos (casos de alto riesgo clasificados erróneamente como de bajo riesgo).

**Métricas destacadas en el conjunto de prueba:**
* **Recall (Clase 1 - Alto Riesgo):** 0.86 *(El modelo detecta correctamente el 86% de los casos reales de alto riesgo)*
* **F1-Score (Clase 1):** 0.77
* **Accuracy General:** 0.72
* **Precisión (Clase 1):** 0.69

**Validación Cruzada (Cross-Validation F1-Score):** 0.72 (± 0.08), lo que demuestra un modelo estable y generalizable frente a datos no vistos.


-------------------------------------------------------------------------------------------------------------

README (English)
# Early Warning System (EWS) - Gender-Based Violence

This repository contains the development of an Early Warning Model designed to identify the risk of judicial process interruption ("Non-Reporting") in cases of gender-based violence.

The model was developed using data provided by the General Directorate of Gender of the Municipality of Bahía Blanca, as part of the Machine Learning course of the Data Science Specialization (UNLaM). The system is a technical research proposal and is not currently in operational use.

The analysis demonstrated how failures in administrative recording (such as the lack of geographic or housing data) act as critical predictors of the victim's disconnection from the judicial system. The main value of the project lies in:
* **Invisibility Detection:** Identifying that the lack of data is not "noise", but a sign of vulnerability.
* **Sensitivity Prioritization:** Optimizing Recall (0.6842) to minimize false negatives in a context of human protection.
* **Technical Benchmark:** Validating that a linear model (Ridge Classifier) is more robust and explainable for this type of social data than complex boosting models (LightGBM).

## About the repository

This repository contains the complete data pipeline and Machine Learning models developed for an Early Warning System for gender-based violence cases. 

### About the Data
The model was trained using a real dataset provided by the General Directorate of Gender of the Municipality of Bahía Blanca. All data has been **strictly anonymized** to protect the identity and privacy of the individuals involved, complying with ethical standards for the handling of sensitive information.

### Project Architecture and Workflow

The project is structured in a series of Jupyter Notebooks that reflect the end-to-end data pipeline:

* `01_PREVISUALIZATION.ipynb`: Initial loading of the dataset, structure preview, and evaluation of the general state of the raw data.
* `02_Cleaning.ipynb`: Treatment of null values, data type correction, and format standardization.
* `03_Ing_Feat.ipynb`: Feature Engineering. Includes key methodological decisions such as:
  * Removal of high cardinality variables (e.g., `profesionales`) to avoid noise in the model.
  * Removal of near-constant variables (e.g., `motivo_de_consulta`) due to low predictive power.
  * Functional grouping of categories in key variables (e.g., `medio_por_el_que_ingresa`) to improve the statistical stability of the algorithm.
* `04_EDA.ipynb`: In-depth Exploratory Data Analysis (EDA). Visualization of distributions, bivariate analysis, and correlations among the resulting variables.
* `04_Modeling_1.ipynb`: Training, validation, and evaluation of the base Machine Learning model.
* `04_Modeling_2.ipynb`: Model interpretability and explainability. Feature importance analysis by extracting and visualizing the coefficients of the Ridge model. This allows for transparent identification of which variables (such as the number of types of violence) have the greatest mathematical weight in classifying a case as high risk.

## Requirements
* **Language:** Python 3.10+
* **Data Manipulation and Analysis:** `pandas`, `numpy`
* **Visualization:** `matplotlib`, `seaborn`
* **Machine Learning:** `scikit-learn`, `imbalanced-learn`

## Results and metrics of the final model

After evaluating the risk level prediction, the selected model was a **Ridge Classifier** optimized with **SMOTE** to handle the original class imbalance.

Given the context of the problem, the critical metric to optimize was the **Recall of the positive class (High Risk)**, seeking to minimize false negatives at all costs (high-risk cases erroneously classified as low risk).

**Key metrics on the test set:**
* **Recall (Class 1 - High Risk):** 0.86 *(The model correctly detects 86% of the actual high-risk cases)*
* **F1-Score (Class 1):** 0.77
* **Overall Accuracy:** 0.72
* **Precision (Class 1):** 0.69

**Cross-Validation (F1-Score):** 0.72 (± 0.08), demonstrating a stable and generalizable model on unseen data.
