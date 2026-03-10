# Telecom X – Predicción de Cancelación de Clientes (Churn)

## Descripción del Proyecto

Este proyecto corresponde a la **Parte 2 del desafío Telecom X**, cuyo objetivo principal es **desarrollar modelos de Machine Learning capaces de predecir la cancelación de clientes (churn)**.

La cancelación de clientes representa un problema importante para las empresas de telecomunicaciones, ya que implica pérdida de ingresos y costos asociados a la adquisición de nuevos clientes. Por esta razón, el análisis busca identificar **patrones y variables clave que permitan anticipar qué clientes tienen mayor probabilidad de cancelar el servicio**.

A partir de datos previamente tratados en la Parte 1 del desafío, se desarrolló un **pipeline de análisis y modelado predictivo**, que incluye preparación de datos, análisis exploratorio, entrenamiento de modelos y evaluación de resultados.

---

# Objetivos del Análisis

* Preparar los datos para el modelado predictivo.
* Identificar variables que influyen en la cancelación de clientes.
* Construir modelos de Machine Learning para predecir el churn.
* Evaluar el rendimiento de los modelos mediante métricas de clasificación.
* Generar insights que permitan proponer **estrategias de retención de clientes**.

---

# Estructura del Proyecto

```
TelecomX-Churn-Prediction/
│
├── TelecomX_ML.ipynb
│   Cuaderno principal con todo el análisis y modelado
│
├── datos_tratados.csv
│   Dataset limpio y preparado obtenido en la Parte 1
│
├── visualizaciones/
│   Gráficos generados durante el análisis exploratorio
│
└── README.md
    Documentación del proyecto
```

---

# Preparación de los Datos

## Clasificación de Variables

El dataset contiene variables de distintos tipos:

### Variables Numéricas

* `customer.tenure`
* `account.Charges.Monthly`
* `account.Charges.Total`
* `customer.SeniorCitizen`

### Variables Categóricas

* Género del cliente
* Tipo de contrato
* Tipo de servicio de internet
* Método de pago
* Servicios adicionales (seguridad, soporte técnico, etc.)

Estas variables categóricas fueron transformadas a formato numérico para poder utilizarlas en los modelos de Machine Learning.

---

## Codificación de Variables

Se utilizó **One-Hot Encoding** mediante `pandas.get_dummies()` para transformar las variables categóricas en variables binarias.

Esto permite que los algoritmos de Machine Learning interpreten correctamente las categorías sin introducir relaciones numéricas artificiales.

---

## Normalización de Datos

Para modelos sensibles a la escala de las variables (como **Regresión Logística**), se aplicó **estandarización utilizando StandardScaler** de `sklearn`.

Esto permite que todas las variables tengan:

* media = 0
* desviación estándar = 1

Los modelos basados en árboles como **Random Forest** no requieren normalización.

---

## División de los Datos

El dataset se dividió en dos subconjuntos:

* **80% datos de entrenamiento**
* **20% datos de prueba**

Esto permite evaluar el desempeño del modelo en datos que **no fueron utilizados durante el entrenamiento**, reduciendo el riesgo de overfitting.

---

# Modelos Utilizados

Se implementaron dos modelos de clasificación:

## 1. Regresión Logística

Modelo lineal ampliamente utilizado para problemas de clasificación binaria.

Ventajas:

* Fácil interpretación
* Buen rendimiento en datasets estructurados

Este modelo logró aproximadamente **80% de exactitud** en la predicción del churn.

---

## 2. Random Forest

Modelo basado en **árboles de decisión ensamblados**.

Ventajas:

* Capacidad de capturar relaciones no lineales
* Permite medir la importancia de las variables

Aunque su rendimiento fue similar al de la regresión logística, su mayor utilidad fue **identificar las variables más influyentes en la cancelación**.

---

# Evaluación de Modelos

Se utilizaron las siguientes métricas:

* Accuracy
* Precision
* Recall
* F1 Score
* Matriz de confusión

Estas métricas permiten evaluar no solo la precisión general del modelo, sino también su capacidad para detectar correctamente a los clientes que cancelan.

---

# Análisis Exploratorio de Datos (EDA)

Durante el análisis exploratorio se identificaron varias relaciones importantes.

## Antigüedad del cliente vs Cancelación

Se observó que los clientes con **menor antigüedad presentan mayor probabilidad de cancelar el servicio**.

Esto sugiere que los primeros meses son críticos para la retención.

---

## Cargos mensuales vs Cancelación

Los clientes con **cargos mensuales más altos tienden a cancelar con mayor frecuencia**.

Esto puede indicar problemas en la percepción del valor del servicio.

---

# Variables Más Importantes para el Churn

Según el modelo Random Forest, las variables con mayor impacto en la cancelación fueron:

* Antigüedad del cliente (`tenure`)
* Cargos mensuales (`Monthly Charges`)
* Cargos totales (`Total Charges`)
* Método de pago
* Tipo de contrato
* Tipo de servicio de internet

---

# Conclusiones Estratégicas

Los resultados indican que los principales factores asociados al churn son:

* Baja antigüedad del cliente
* Altos cargos mensuales
* Contratos de corto plazo
* Determinados métodos de pago

En base a estos resultados, se sugieren las siguientes estrategias:

* Implementar programas de retención durante los **primeros meses del cliente**.
* Incentivar contratos de **mayor duración**.
* Revisar la propuesta de valor de los **planes con mayor costo**.
* Ofrecer beneficios adicionales a clientes con alto riesgo de cancelación.

---

# Cómo Ejecutar el Proyecto

## Requisitos

Instalar las siguientes bibliotecas:

```
pip install pandas
pip install numpy
pip install matplotlib
pip install seaborn
pip install scikit-learn
```

---

## Ejecución

1. Descargar el repositorio.
2. Abrir el archivo:

```
TelecomX_ML.ipynb
```

3. Cargar el dataset tratado:

```
datos_tratados.csv
```

4. Ejecutar las celdas del cuaderno paso a paso.

---

# Autor

Proyecto desarrollado como parte del desafío **Telecom X – Machine Learning Challenge**, enfocado en el desarrollo de habilidades en análisis de datos y modelado predictivo.

