# 🤖 Telecom X - Predicción de Cancelación de Clientes (Machine Learning)

## 📝 Descripción del Proyecto (Fase 2)
Tras haber completado con éxito el Análisis Exploratorio de Datos (EDA) y la limpieza profunda de la base de datos de **Telecom X**, esta segunda fase del proyecto se enfoca en la **construcción de modelos predictivos de Machine Learning**. 

El objetivo principal es anticipar qué clientes tienen la mayor probabilidad de cancelar sus servicios (Churn) para permitirle a la empresa tomar decisiones proactivas y estrategias de retención focalizadas.

## 🗂️ Sobre la Base de Datos
Para este entrenamiento, partimos del dataset limpio `telecom_clientes_limpio.csv`, producto de la Fase 1. 
* **Target (Variable Objetivo):** `Abandono` (0 = Permanece, 1 = Cancela). Existe un desbalance natural de clases (73.5% retención vs 26.5% fuga).
* **Variables Predictoras (Features):** Incluye datos demográficos (género, tercera edad, pareja), información de servicios contratados (tipo de internet, soporte técnico, streaming) y datos financieros.
* **Ajustes de Modelado:** Se eliminaron las variables `Cargos_Totales` y `Cargos_Diarios` debido a su alta correlación matemática (multicolinealidad > 0.82) con `Antiguedad_Meses` y `Cargos_Mensuales`, evitando así inestabilidad en los modelos lineales.

## 🛠️ Tecnologías y Herramientas Utilizadas
* **Lenguaje:** Python 3 (Google Colab)
* **Preprocesamiento y Modelado:** `Scikit-Learn` (`Pipeline`, `ColumnTransformer`, `OneHotEncoder`, `StandardScaler`)
* **Manipulación de Datos:** `Pandas`, `NumPy`
* **Visualización:** `Matplotlib`, `Seaborn`

## ⚙️ Arquitectura del Pipeline de Machine Learning

Se construyó un flujo de trabajo robusto para evitar la fuga de datos (*Data Leakage*) y asegurar la escalabilidad:
1. **Train/Test Split:** División 80/20 utilizando `stratify=y` para garantizar que la proporción de abandonos se mantenga idéntica en el entrenamiento y la prueba.
2. **ColumnTransformer:** * Variables Categóricas: `OneHotEncoder` (eliminando la primera categoría para evitar colinealidad perfecta).
   * Variables Numéricas: `StandardScaler` para normalizar escalas, vital para modelos basados en gradientes y regresiones.
3. **Entrenamiento de Múltiples Modelos:** Se evaluaron 5 algoritmos distintos:
   * Logistic Regression
   * Decision Tree (Estándar y Balanceado)
   * Random Forest
   * Gradient Boosting

## 📊 Resultados y Evaluación de Modelos

Dado el desbalance de clases, no nos limitamos al *Accuracy*. Se priorizó el **ROC-AUC** para medir la capacidad de discriminación del modelo, y el **Recall** para asegurar que estamos detectando correctamente a los clientes que realmente se van.

| Modelo | Accuracy | Recall (Churn) | F1-Score | ROC-AUC |
| :--- | :---: | :---: | :---: | :---: |
| **Gradient Boosting** | **0.7941** | 0.5053 | 0.5658 | **0.8454** |
| **Logistic Regression** | 0.7948 | **0.5267** | **0.5768** | 0.8416 |
| Random Forest | 0.7885 | 0.4839 | 0.5484 | 0.8169 |
| Decision Tree (Bal) | 0.7210 | 0.4598 | 0.4667 | 0.6389 |

## 💡 Conclusiones Estratégicas y Feature Importance

1. **Modelos Ganadores:** El modelo de **Gradient Boosting** demostró la mayor capacidad predictiva global (ROC-AUC: 0.845). Sin embargo, la **Regresión Logística** resultó ser un *baseline* extremadamente fuerte, ganando ligeramente en *Recall*, lo que la hace ideal si el negocio prefiere un modelo más rápido y altamente interpretable. Los ensambles y modelos lineales superaron con creces a los árboles de decisión individuales.
2. **Perfil del Cliente en Riesgo:** Gracias a la extracción de la *Importancia de Variables (Feature Importance)*, confirmamos matemáticamente que el riesgo de fuga se dispara cuando:
   * El cliente tiene una **antigüedad muy baja** (los primeros meses son críticos).
   * El **gasto mensual es elevado** (sensibilidad al precio).
   * Tiene **contratos mes a mes** en lugar de anuales.

## 📂 Estructura del Repositorio
* `Challenge_2_telecomX.ipynb`: Cuaderno de Google Colab con el desarrollo completo del pipeline de Machine Learning y la evaluación de modelos.
* `telecom_clientes_limpio.csv`: Dataset procesado utilizado para el entrenamiento.
* `README.md`: Resumen ejecutivo de los resultados técnicos.
