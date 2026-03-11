# 📊 Telecom X - Predicción de Cancelación de Clientes (Churn)

## 📌 Descripción del Proyecto

Este proyecto tiene como objetivo **predecir la cancelación de clientes (churn)** en la empresa Telecom X utilizando técnicas de **análisis de datos y machine learning**.

A partir de información sobre los servicios contratados, características del cliente y hábitos de pago, se analizan patrones que permitan identificar **clientes con mayor probabilidad de cancelar el servicio**.

Este tipo de análisis permite a las empresas **anticipar la pérdida de clientes y aplicar estrategias de retención**.

---

## 🎯 Objetivos del Análisis

* Analizar las variables que influyen en la cancelación de clientes.
* Preparar los datos para modelos de machine learning.
* Construir modelos predictivos para identificar clientes con riesgo de churn.
* Evaluar el desempeño de diferentes algoritmos de clasificación.

---

## 📁 Estructura del Proyecto

```
TelecomX-Churn/
│
├── data/
│   └── telecomx_datos_tratados.csv
│
├── notebooks/
│   └── TelecomX_Churn_Analisis.ipynb
│
├── images/
│   └── visualizaciones_generadas.png
│
└── README.md
```

**Descripción de carpetas:**

* **data/** → contiene el dataset procesado.
* **notebooks/** → cuaderno principal con el análisis y modelado.
* **images/** → gráficos generados durante el análisis exploratorio.
* **README.md** → documentación del proyecto.

---

## 🧹 Preparación de los Datos

El preprocesamiento incluyó las siguientes etapas:

### 1️⃣ Clasificación de variables

Las variables se dividieron en:

**Variables categóricas**

* Género
* Tiene_Pareja
* Personas_a_Cargo
* Servicio_Internet
* Tipo_Contrato
* Metodo_Pago
* Streaming_TV
* Streaming_Peliculas
* Soporte_Tecnico

**Variables numéricas**

* Meses_Permanencia
* Charges.Monthly
* Charges.Total
* Cuentas_Diarias
* Adulto_Mayor

**Variable objetivo**

* `Fuga_Cliente`

  * 0 → Cliente permanece
  * 1 → Cliente cancela

---

### 2️⃣ Codificación de variables categóricas

Se aplicó **One-Hot Encoding** utilizando `pandas.get_dummies()` para convertir las variables categóricas en variables numéricas compatibles con los modelos de machine learning.

---

### 3️⃣ Normalización de datos

Se aplicó **StandardScaler** a las variables numéricas para modelos sensibles a la escala de los datos.

Esto asegura que las variables tengan **media 0 y desviación estándar 1**, evitando que variables con mayor magnitud dominen el entrenamiento del modelo.

---

### 4️⃣ División del dataset

El conjunto de datos se dividió en:

* **80% entrenamiento**
* **20% prueba**

Utilizando `train_test_split` de **Scikit-learn**.

---

## 🤖 Modelos Utilizados

Se implementaron dos modelos de clasificación:

### Regresión Logística

Modelo lineal utilizado para clasificación binaria.
Requiere normalización debido a su sensibilidad a la escala de las variables.

### Random Forest

Modelo basado en árboles de decisión que combina múltiples árboles para mejorar la precisión y reducir el overfitting.
Este modelo **no requiere normalización**.

---

## 📊 Tecnologías Utilizadas

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Scikit-learn
* Jupyter Notebook

---

## 📈 Conclusión

El análisis permitió identificar variables relevantes asociadas con la cancelación de clientes y construir modelos predictivos capaces de estimar el riesgo de churn.

Este tipo de modelos puede ayudar a las empresas a **tomar decisiones estratégicas orientadas a la retención de clientes**.



