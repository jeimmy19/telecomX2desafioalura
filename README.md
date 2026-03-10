# 📊 Telecom X - Análisis de Retención de Clientes (Customer Churn EDA)

## 📝 Descripción del Proyecto
La empresa de telecomunicaciones **Telecom X** enfrenta una problemática significativa: una alta tasa de cancelación de servicios por parte de sus clientes (Churn). Este proyecto de Data Science se centra en la extracción, limpieza, procesamiento y análisis exploratorio de datos (EDA) para identificar los factores clave que impulsan esta fuga de clientes.

El objetivo final es extraer *insights* accionables y proporcionar recomendaciones estratégicas basadas en datos para reducir la tasa de abandono actual del **26.45%**.

## 🛠️ Tecnologías y Herramientas Utilizadas
* **Lenguaje:** Python 3
* **Entorno:** Google Colab / Jupyter Notebook
* **Manipulación de Datos:** Pandas, NumPy
* **Visualización de Datos:** Matplotlib, Seaborn

## ⚙️ Metodología Aplicada

1. **Extracción y Normalización de Datos:**
   * Ingesta de datos desde una fuente JSON alojada en la web.
   * Aplanado (Flattening) de estructuras JSON anidadas utilizando `pd.json_normalize` para transformar los datos en un DataFrame tabular estructurado.
2. **Limpieza y Transformación (Data Cleaning):**
   * Detección y eliminación de 22 registros duplicados.
   * Imputación de valores nulos (NaN) en variables continuas mediante la media.
   * Limpieza de registros con valores vacíos en la variable objetivo (`Abandono`).
   * Estandarización de variables categóricas (mapeo a variables binarias 1/0).
   * Feature Engineering: Creación de nuevas variables de negocio como `Cargos_Diarios`.
   * Traducción y estandarización de nombres de columnas al español para mejor interpretabilidad.
3. **Análisis Exploratorio de Datos (EDA):**
   * Análisis univariado y bivariado.
   * Creación de visualizaciones de alto impacto (gráficos de pastel, barras apiladas, histogramas y boxplots) para comparar el comportamiento de clientes retenidos vs. fugados.

## 💡 Hallazgos Principales (Key Insights)

Tras el análisis de más de 7,000 registros, se identificaron los siguientes patrones críticos:
* **Flexibilidad Contractual:** Los contratos de tipo "mes a mes" presentan un riesgo altísimo (**42.64%** de abandono), siendo casi 4 veces más propensos a la fuga que los contratos anuales.
* **Método de Pago:** El pago mediante "cheque electrónico" está fuertemente correlacionado con la cancelación (**45.15%** de fuga).
* **Calidad/Precio del Servicio:** Sorprendentemente, los usuarios del servicio premium de internet (*Fiber optic*) tienen la tasa de abandono más alta (**41.78%**), lo que sugiere una disonancia entre el precio y el valor percibido.
* **Antigüedad (Tenure):** El mayor riesgo se concentra en los primeros 18 meses de vida del cliente.

## 🚀 Recomendaciones Estratégicas
En base a los datos, se proponen las siguientes acciones para el equipo de negocio:
1. **Incentivar contratos a largo plazo:** Crear beneficios o descuentos para migrar clientes de planes mensuales a anuales.
2. **Fomentar la automatización de pagos:** Ofrecer incentivos para migrar del cheque electrónico al débito automático.
3. **Planes de Retención Temprana:** Implementar programas de *onboarding* más sólidos durante el primer año y medio del cliente.
4. **Auditoría de Fibra Óptica:** Revisar urgentemente la competitividad de los precios y la calidad del servicio de fibra óptica.

## 📂 Estructura del Repositorio
* `TelecomX_Analysis.ipynb`: Cuaderno principal de Google Colab con todo el código, análisis y visualizaciones (Mejoradas con diseño premium en Seaborn).
* `README.md`: Resumen y conclusiones del proyecto.

## 👩‍💻 Autor
**[Jeimmy Ortiz]**


---
*Este proyecto fue desarrollado como parte de un Challenge de Data Science para demostrar habilidades de análisis descriptivo, limpieza de datos y visualización.*
