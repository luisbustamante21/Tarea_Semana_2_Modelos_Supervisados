## Problema

La diabetes mellitus es una enfermedad crónica con alta prevalencia y complicaciones severas si no se detecta a tiempo. El objetivo de este proyecto es desarrollar un modelo predictivo capaz de estimar la probabilidad de que un individuo desarrolle diabetes, a partir de factores demográficos, de estilo de vida y métricas clínicas.

El dataset proviene de Kaggle y contiene 10,000 registros y 21 variables, incluyendo edad, sexo, etnia, índice de masa corporal (IMC), niveles de glucosa en ayunas, HbA1c, perfil lipídico, presión arterial, hábitos de vida y antecedentes familiares de diabetes.

El objetivo principal es construir un modelo que, a partir de estas variables, pueda predecir de forma precisa la probabilidad de que una persona desarrolle diabetes, ayudando así a una detección temprana.

## Metodología

### 1. Carga y Exploración Inicial

* Lectura del archivo `diabetes_dataset.csv`.
* Visualización de las primeras filas, inspección de tipos de datos, conteo de nulos y detección de duplicados.
* Confirmación de un índice entero (0–9999) que se eliminó por no aportar información predictiva.

### 2. Limpieza y Preprocesamiento

* Tratamiento de valores faltantes en la columna `Alcohol_Consumption` (aprox. 33% de datos faltantes) mediante imputación con la moda.
* Normalización de variables numéricas (`IMC`, `glucosa`, `HbA1c`, `colesterol`, `presión arterial`, `GGT`, `ácido úrico`, `ingesta calórica`) con `StandardScaler`.
* Codificación one‑hot de variables categóricas (`Sex`, `Ethnicity`, `Physical_Activity_Level`, `Alcohol_Consumption`, `Smoking_Status`).

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

* Uso de `GridSearchCV` para ajustar parámetros clave en Random Forest (número de árboles, profundidad máxima, etc.) y mejorar la generalización.

## Conclusiones

* **Desempeño del Modelo:** El Random Forest obtuvo el mejor balance entre todas las métricas evaluadas, alcanzando alta precisión, recall y AUC-ROC, superando a Regresión Logística, SVM y Árbol de Decisión.
* **Variables Más Predictivas:** Los factores con mayor importancia en la predicción fueron:

  1. Glucosa en ayunas
  2. HbA1c
  3. Índice de Masa Corporal (IMC)
  4. Antecedentes familiares de diabetes
* **Aplicabilidad:** Este modelo podría integrarse en entornos clínicos o programas de salud pública como herramienta de cribado para la identificación temprana de individuos en riesgo, permitiendo intervenciones preventivas.
