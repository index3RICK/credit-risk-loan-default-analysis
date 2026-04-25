# Credit Risk Loan Default Analysis

Este proyecto construye un modelo de clasificación para predecir la **probabilidad de impago de préstamos hipotecarios**, con el objetivo de apoyar decisiones de aprobación crediticia y reducir riesgo financiero.

Se documenta un pipeline completo desde la limpieza de datos hasta el entrenamiento y evaluación del modelo de Machine Learning.

---

# Objetivo

Construir un flujo reproducible para:

* Limpieza de datos financieros
* Tratamiento de valores nulos
* Detección y manejo de outliers
* Preparación para Machine Learning
* Predicción de default crediticio
* Generación de probabilidades de riesgo

---

# Dataset

El dataset contiene información de préstamos hipotecarios:

| Variable             | Descripción              |
| -------------------- | ------------------------ |
| loan_amount          | Monto del préstamo       |
| rate_of_interest     | Tasa de interés          |
| Interest_rate_spread | Spread de tasa           |
| Upfront_charges      | Cargos iniciales         |
| property_value       | Valor de propiedad       |
| income               | Ingresos del solicitante |
| Credit_Score         | Puntaje crediticio       |
| LTV                  | Loan to Value            |
| dtir1                | Debt to Income Ratio     |
| Status               | Variable objetivo        |

## Variable Objetivo

| Valor | Significado |
| ----- | ----------- |
| 0     | No Default  |
| 1     | Default     |

Distribución del target:

* No Default → 76%
* Default → 24%

Esto representa un dataset desbalanceado típico de riesgo crediticio.

---

# Estructura del Proyecto

```
credit-risk-loan-default-analysis
│
├── credit_risk_data_cleaning.ipynb
├── credit_risk_model.ipynb
├── credit_risk_clean.csv
└── README.md
```

---

# Pipeline de Limpieza de Datos

## 1. Carga y exploración inicial

* Lectura del dataset
* Revisión de estructura
* Tipos de datos
* Identificación de variables

---

## 2. Análisis de valores nulos

* Identificación de missing values
* Cuantificación porcentual
* Visualización con heatmap

---

## 3. Imputación de datos

Se imputan valores faltantes usando mediana para evitar impacto de outliers:

* rate_of_interest
* Interest_rate_spread
* Upfront_charges
* dtir1
* property_value
* income
* LTV

Se crean variables indicadoras de ausencia:

* rate_of_interest_missing
* Interest_rate_spread_missing
* Upfront_charges_missing

---

## 4. Eliminación de columnas irrelevantes

Se eliminan variables sin valor predictivo:

* ID
* year

---

## 5. Detección de outliers

Se utiliza:

* Histogramas de distribución
* Boxplots individuales
* Estadística descriptiva
* Análisis de rangos

---

## 6. Limpieza de valores extremos

Reglas aplicadas:

```
income > 0
rate_of_interest > 0
LTV < 200
Interest_rate_spread > -1
property_value < percentil 99
```

---

## 7. Dataset limpio final

El dataset limpio se exporta como:

```
credit_risk_clean.csv
```

Listo para modelado.

---

# Modelado

Pipeline aplicado:

* Encoding de variables categóricas
* Eliminación de NaN
* Train/Test Split
* Escalado de variables (StandardScaler)
* Logistic Regression
* Manejo de dataset desbalanceado (class_weight="balanced")

---

# Resultados del Modelo

Modelo utilizado: Logistic Regression

Resultados obtenidos:

Accuracy: 0.83
Precision (Default): 0.64
Recall (Default): 0.70
F1 Score (Default): 0.67
ROC AUC: 0.86

El modelo muestra buena capacidad para identificar clientes con alto riesgo de impago, priorizando la detección de morosos sobre la precisión global.

Esto es consistente con escenarios reales de riesgo crediticio.

---

# Interpretación del Modelo

El modelo aprende relaciones como:

* Mayor LTV → mayor riesgo
* Menor income → mayor riesgo
* Mayor dtir → mayor riesgo
* Menor credit score → mayor riesgo

El resultado final es una probabilidad de default para cada cliente.

Ejemplo de salida:

| Cliente | Prob Default | Decisión |
| ------- | ------------ | -------- |
| A       | 0.12         | Aprobar  |
| B       | 0.78         | Rechazar |
| C       | 0.45         | Revisión |
| D       | 0.83         | Rechazar |

Esto permite construir un sistema de scoring crediticio.

---

# Tecnologías Utilizadas

* Python
* Pandas
* NumPy
* Seaborn
* Matplotlib
* Scikit-learn
* Jupyter Notebook

---

# Aplicación en Negocio

Este modelo puede utilizarse para:

* Evaluación de solicitudes de crédito
* Scoring crediticio
* Reducción de riesgo financiero
* Segmentación de clientes de alto riesgo
* Automatización de decisiones crediticias

---

# Próximas Mejoras

* Random Forest
* XGBoost
* Feature Importance
* Threshold tuning
* Cross Validation
* Pipeline con sklearn
* Deploy del modelo

---

# Autor

Erick Chicaiza
Junior Data Analyst

