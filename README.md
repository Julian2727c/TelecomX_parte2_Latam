
**Telecom X - Parte 2: Predicción de Cancelación de Clientes (Churn)**
1. Propósito del Análisis
Este proyecto forma la segunda parte del desafío Telecom X y tiene como objetivo principal desarrollar modelos predictivos para identificar clientes propensos a la cancelación (churn). La meta es anticipar la fuga de clientes basándose en sus características y patrones de uso, permitiendo a la compañía implementar estrategias de retención proactivas. La predicción temprana del churn es crucial para minimizar la pérdida de ingresos y maximizar la satisfacción del cliente.

2. Estructura del Proyecto
El proyecto está organizado de la siguiente manera:

notebook.ipynb: Este cuaderno de Google Colab es el archivo principal que contiene todo el proceso de preprocesamiento, modelado y evaluación.
/content/datos_tratados.csv: Este archivo CSV contiene los datos ya limpios y organizados de la Parte 1 del desafío. Es la fuente de datos para este análisis.
Visualizaciones: Todas las visualizaciones se generan dinámicamente dentro del cuaderno utilizando matplotlib y seaborn y se muestran en línea.
3. Proceso de Preparación de Datos
Clasificación de Variables
Antes del modelado, las variables en el dataset fueron categorizadas y tratadas:

Variables Numéricas: Meses_Permanencia, Charges.Monthly, Charges.Total, Cuentas_Diarias.
Variables Categóricas: Fuga_Cliente (variable objetivo), Genero, Adulto_Mayor, Tiene_Pareja, Personas_a_Cargo, Servicio_Telefonico, Lineas_Multiples, Servicio_Internet, Seguridad_Online, Respaldo_Online, Proteccion_Dispositivo, Soporte_Tecnico, Streaming_TV, Streaming_Peliculas, Tipo_Contrato, Facturacion_Electronica, Metodo_Pago.
Etapas de Normalización y Codificación
Eliminación de Columnas Irrelevantes: La columna ID_Cliente fue eliminada al inicio, ya que no aporta valor predictivo directo y solo actúa como un identificador único.
Codificación One-Hot: Las variables categóricas fueron transformadas a formato numérico utilizando pd.get_dummies y OneHotEncoder de sklearn.preprocessing. Esto crea nuevas columnas binarias para cada categoría, permitiendo que los algoritmos de Machine Learning las procesen.
Balanceo de Clases: La variable objetivo Fuga_Cliente mostró un desbalance significativo (aproximadamente 73.46% 'No Churn' vs. 26.54% 'Churn'). Para abordar esto y evitar que los modelos se sesgaran hacia la clase mayoritaria, se aplicó la técnica de Oversampling utilizando RandomOverSampler de imblearn.over_sampling sobre el conjunto de entrenamiento. Esto igualó el número de instancias para ambas clases.
Normalización/Estandarización: Las características numéricas (Meses_Permanencia, Charges.Monthly, Charges.Total, Cuentas_Diarias) fueron estandarizadas utilizando StandardScaler de sklearn.preprocessing. Este paso es crucial para modelos sensibles a la escala de los datos, como la Regresión Logística, asegurando que todas las características contribuyan equitativamente al modelo.
Separación de Datos
El conjunto de datos fue dividido en dos partes:

Conjunto de Entrenamiento (80%): Utilizado para entrenar los modelos.
Conjunto de Prueba (20%): Utilizado para evaluar el rendimiento de los modelos con datos no vistos.
La división se realizó utilizando train_test_split de sklearn.model_selection con test_size=0.2 y random_state=42. Además, se empleó stratify=y_cleaned para asegurar que la proporción de clases de la variable objetivo se mantuviera similar en ambos conjuntos, especialmente importante debido al desbalance inicial.

4. Justificaciones para las Decisiones de Modelado
Se seleccionaron dos tipos de modelos para comparar su desempeño y entender cómo diferentes enfoques abordan el problema de predicción de churn:

Regresión Logística: Este modelo lineal es sensible a la escala de las características. Por ello, se incorporó un StandardScaler dentro de un Pipeline antes del modelo de Regresión Logística. Esto asegura que las características numéricas estén estandarizadas, lo que mejora la convergencia y el rendimiento del modelo.
Random Forest Classifier: Este es un modelo basado en árboles de decisión y, por naturaleza, es robusto a la escala de las características. No requiere normalización, lo que permite observar el rendimiento de un modelo que no se ve afectado por la magnitud de los valores de las características.
La elección de estos dos modelos permite evaluar la importancia de la estandarización para modelos específicos y comparar la interpretabilidad de un modelo lineal (Regresión Logística a través de sus coeficientes) con la capacidad de un modelo de conjunto (Random Forest) para capturar interacciones no lineales.

5. Ejemplos de Gráficos e Insights (EDA)
El Análisis Exploratorio de Datos (EDA) reveló información clave:

Desbalance de Clases: Se confirmó que Fuga_Cliente está desbalanceada (aprox. 73.5% 'No Churn', 26.5% 'Churn').

Distribución de Cancelación de Clientes

Correlación con Fuga_Cliente: La matriz de correlación y un gráfico de barras específico para la variable objetivo Fuga_Cliente destacaron las características más influyentes. Por ejemplo, Meses_Permanencia mostró una fuerte correlación negativa, indicando que los clientes con mayor antigüedad son menos propensos al churn. Charges.Monthly y Charges.Total mostraron correlaciones positivas, sugiriendo que costos más altos pueden incrementar la probabilidad de churn.

Correlación de variables con Fuga_Cliente

Análisis Dirigido (Boxplots):

Tiempo de Permanencia vs. Cancelación: Los clientes que cancelan (Fuga_Cliente = 1) tienen una mediana de Meses_Permanencia significativamente menor que los que no cancelan (Fuga_Cliente = 0).

Tiempo de Permanencia vs Cancelación

Gasto Total vs. Cancelación: Los clientes con mayor Charges.Total y Charges.Monthly tienden a tener una mayor tasa de cancelación, lo que sugiere que el costo del servicio es un factor importante.

Gasto Total vs Cancelación

Gasto Mensual vs Cancelación

6. Instrucciones para Ejecutar el Cuaderno
Para ejecutar este cuaderno de Google Colab, siga los siguientes pasos:

Cargar el Archivo de Datos: Asegúrese de que el archivo datos_tratados.csv esté disponible en el entorno de Colab, preferiblemente en la ruta /content/datos_tratados.csv.
Instalar Bibliotecas (si es necesario): Las siguientes bibliotecas son necesarias. Si está ejecutando en un entorno local o si no están preinstaladas en Colab, puede instalarlas con pip:
pip install pandas scikit-learn matplotlib seaborn imbalanced-learn
Abrir el Cuaderno: Abra el archivo notebook.ipynb en Google Colab.
Ejecutar Celdas: Ejecute las celdas de código de forma secuencial. El cuaderno está diseñado para ser ejecutado de principio a fin, siguiendo el flujo de preprocesamiento, modelado y evaluación.
