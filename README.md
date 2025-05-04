## Problema

La diabetes es una enfermedad crónica que afecta a millones de personas en todo el mundo. La detección temprana es fundamental para implementar intervenciones que prevengan o retrasen su aparición. Con el auge de los datos de salud y las técnicas de aprendizaje automático, es posible desarrollar modelos predictivos que identifiquen a individuos en riesgo basándose en factores personales y clínicos.

El dataset proviene de Kaggle y contiene 10,000 registros y 21 variables, incluyendo edad, sexo, etnia, índice de masa corporal (IMC), niveles de glucosa en ayunas, HbA1c, perfil lipídico, presión arterial, hábitos de vida y antecedentes familiares de diabetes.

El objetivo principal es construir un modelo que, a partir de estas variables, pueda predecir de forma precisa la probabilidad de que una persona desarrolle diabetes, ayudando así a una detección temprana.

## Metodología

### 1. Carga y Exploración Inicial

* Lectura del archivo `diabetes_dataset.csv`.
* Visualización de las primeras filas, inspección de tipos de datos, conteo de nulos y detección de duplicados.

### 2. Limpieza y Preprocesamiento

* Tratamiento de valores faltantes en la columna `Alcohol_Consumption` mediante imputación con la moda.
* Normalización de variables numéricas (`IMC`, `glucosa`, `HbA1c`, `colesterol`, `presión arterial`, `GGT`, `ácido úrico`, `ingesta calórica`) con `StandardScaler`.
* Codificación de características categóricas mediante LabelEncoder (`Sex`, `Ethnicity`, `Physical_Activity_Level`, `Alcohol_Consumption`, `Smoking_Status`, `BMI_Category`, `Age_Group`).

### 3. Análisis Exploratorio de Datos

* Estadísticas descriptivas para variables numéricas.
* Visualización de distribuciones y diagramas de caja.
* Matriz de correlaciones para identificar relaciones entre variables y seleccionar las más relevantes.

### 4. Construcción de Modelos

* División de datos en conjuntos de entrenamiento (80%) y prueba (20%).
* Implementación de cuatro clasificadores:

  * Árbol de Decisión
  * Support Vector Machine (SVM)
  * Random Forest
* Para cada modelo: entrenamiento, predicción y evaluación.

### 5. Evaluación y Comparación

* Métricas usadas: precisión (`accuracy`), `recall`, `precision`, `F1-score`, `AUC-ROC` y matriz de confusión.
* Visualización de fronteras de decisión en un espacio bidimensional (edad vs. glucosa en ayunas) para ilustrar el comportamiento de cada clasificador.

### 6. Optimización de Hiperparámetros

* Uso de los `Hiperparámetros` para ajustar parámetros clave en Random Forest, SVM, Árbol de Decisión y mejorar la generalización.

## Conclusiones

* **Desempeño del Modelo:** El Random Forest y el Árbol de Decisión obtuvieron el mejor balance entre todas las métricas evaluadas, alcanzando alta precisión, recall y AUC-ROC, superando a SVM.
* **Variables Más Predictivas:** Los factores con mayor importancia en la predicción fueron:

  1. Glucosa en ayunas
  2. HbA1c
  3. Índice de Masa Corporal (IMC)
  4. Antecedentes familiares de diabetes
* **Aplicabilidad:** Este modelo podría integrarse en entornos clínicos o programas de salud pública como herramienta de selección para la identificación temprana de individuos en riesgo, permitiendo intervenciones preventivas.
* **Líneas Futuras de Desarrollo:**
  - Investigar algoritmos de clasificación más avanzados o técnicas de ensamblaje.  
  - Aplicar métodos de escalado o transformación de características para mejorar el desempeño del modelo.  
  - Integrar conjuntos de datos adicionales o datos a largo plazo, si están disponibles.  
  - Realizar análisis más profundos de subgrupos, considerando factores como el sexo o la etnicidad.
