# Credit Risk Loan Default Analysis  * Análisis de riesgo crediticio y morosidad de préstamos

Análisis y preparación de datos para la predicción de **riesgo crediticio y morosidad de préstamos**.
Este proyecto documenta un pipeline completo desde la limpieza de datos hasta la preparación para modelos de Machine Learning.

---

## Objetivo

Construir un flujo reproducible para:

* Limpieza de datos financieros
* Tratamiento de valores nulos
* Detección y manejo de outliers
* Preparación para Machine Learning
* Predicción de default crediticio

---

## Dataset

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

### Variable Objetivo

| Valor | Significado |
| ----- | ----------- |
| 0     | No Default  |
| 1     | Default     |

Distribución del target:

* No Default → 76%
* Default → 24%

---

## Estructura del Proyecto

```
credit-risk-loan-default-analysis
│
├── credit_risk_data_cleaning.ipynb
├── credit_risk_model.ipynb
├── credit_risk_clean.csv
└── README.md
```

---

## Pipeline de Limpieza de Datos

### 1. Carga y exploración inicial

* Lectura del dataset
* Revisión de estructura
* Tipos de datos

### 2. Análisis de valores nulos

* Identificación de missing values
* Cuantificación porcentual
* Visualización con heatmap

### 3. Imputación de datos

Se imputan valores faltantes usando mediana:

* rate_of_interest
* Interest_rate_spread
* Upfront_charges
* dtir1
* property_value
* income
* LTV

Se crean variables indicadoras:

* rate_of_interest_missing
* Interest_rate_spread_missing
* Upfront_charges_missing

---

### 4. Eliminación de columnas irrelevantes

Se eliminan:

* ID
* year

---

### 5. Detección de outliers

Se utiliza:

* Boxplot general
* Estadística descriptiva
* Análisis de rangos

---

### 6. Limpieza de valores extremos

Reglas aplicadas:

```
income > 0
rate_of_interest > 0
LTV < 200
Interest_rate_spread > -1
property_value < percentil 99
```

---

### 7. Dataset limpio final

El dataset limpio se exporta como:

```
credit_risk_clean.csv
```

Listo para modelado.

---

## Tecnologías Utilizadas

* Python
* Pandas
* NumPy
* Seaborn
* Matplotlib
* Scikit-learn
* Jupyter Notebook

---

## Próximos Pasos

* Encoding de variables categóricas
* Train/Test split
* Logistic Regression
* Random Forest
* Evaluación del modelo
* Feature importance
* ROC Curve

---

## Autor

Erick Chicaiza * 
Jr. Data Analysis
