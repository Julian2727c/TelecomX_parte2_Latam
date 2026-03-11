---

# 📡 Telecom X - Análisis de Churn (Parte 2)

## 🎯 Propósito del Proyecto

El objetivo principal de este análisis es **predecir la tasa de cancelación (Churn)** de los clientes de Telecom X. Mediante el uso de modelos de aprendizaje automático, buscamos identificar proactivamente a los usuarios con mayor riesgo de abandonar el servicio, permitiendo al equipo de marketing ejecutar estrategias de retención personalizadas.

---

## 📂 Estructura del Proyecto

```text
├── data/
│   ├── raw_telecom_data.csv       # Datos originales
│   └── processed_telecom.csv     # Datos limpios y normalizados
├── notebooks/
│   └── telecom_x_part2.ipynb     # Cuaderno principal con el análisis
├── visuals/
│   └── plots/                     # Gráficos generados (EDA y Matrices)
└── README.md                      # Documentación del proyecto

```

---

## ⚙️ Preparación de los Datos

El éxito del modelo reside en el tratamiento riguroso de la información:

1. **Clasificación de Variables:**
* **Categóricas:** Género, tipo de contrato, método de pago (transformadas mediante *One-Hot Encoding*).
* **Numéricas:** Tenencia (meses), cargos mensuales, cargos totales (escaladas para uniformidad).


2. **Normalización:** Aplicamos `StandardScaler` a las variables numéricas para evitar que escalas mayores (como cargos totales) dominen injustamente el aprendizaje del modelo.
3. **División de Datos:** Se utilizó un split de **80% entrenamiento / 20% prueba** para asegurar una validación robusta y evitar el sobreajuste (*overfitting*).

> **Justificación:** Se optó por un modelo de Bosques Aleatorios (Random Forest) debido a su excelente manejo de variables categóricas y su capacidad para capturar relaciones no lineales en el comportamiento del cliente.

---

## 📊 Insights del EDA (Análisis Exploratorio)

Durante el análisis, descubrimos patrones críticos que afectan la retención:

* **Contratos mes a mes:** Representan el mayor foco de fuga de clientes.
* **Cargos Totales:** Los clientes que cancelan suelen tener una tenencia menor a 6 meses pero con cargos mensuales superiores al promedio.
* **Soporte Técnico:** La falta de servicios de valor agregado (como soporte técnico o seguridad online) correlaciona directamente con un mayor Churn.

---

## 🚀 Instrucciones de Ejecución

### 1. Requisitos Previos

Asegúrate de tener instaladas las siguientes librerías:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn

```

### 2. Carga de Datos

El cuaderno está configurado para leer automáticamente el archivo procesado en la carpeta `/data`. Si deseas replicar el proceso desde cero:

1. Abre `telecom_x_part2.ipynb`.
2. Ejecuta las celdas de la sección **"Data Cleaning"**.
3. Los resultados se exportarán automáticamente a un nuevo CSV.

---

### 🤝 Próximos Pasos

* [ ] Implementar técnicas de balanceo de clases (SMOTE) para mejorar el Recall del Churn.
* [ ] Probar modelos de Boosting (XGBoost o LightGBM).

**¿Te gustaría que añadamos una tabla comparativa de las métricas finales (Accuracy, Precision, Recall) para que el README sea aún más impactante?**
