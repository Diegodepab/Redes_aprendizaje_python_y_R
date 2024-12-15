# Proyecto de Predicción con Redes Neuronales con información cliníca

Este proyecto tiene como objetivo la creación de un modelo de red neuronal para predecir la variable `hospital_death` utilizando un conjunto de datos proporcionado por el profesor (posiblemente obtenido de [eICU Collaborative Research Database](https://eicu-crd.mit.edu/)). El enfoque incluye desde el preprocesamiento de los datos hasta la implementación y optimización de una red neuronal secuencial.

## Dataset

El conjunto de datos cuenta con más de 9000 filas y 186 columnas. De estas, 8 columnas corresponden a datos categóricos y 178 a datos numéricos. Una gran parte de las variables contienen valores faltantes, y las clases están desbalanceadas, lo que plantea desafíos adicionales para el entrenamiento del modelo.

### Características del Dataset:
- **Filas**: 9000+
- **Columnas categóricas**: 8
- **Columnas numéricas**: 178
- **Desbalanceo de clases**: Presente
- **Valores faltantes**: Alta proporción en algunas columnas

## Preprocesamiento de Datos

Debido a la cantidad de valores faltantes y el desbalanceo en las clases, se realizaron varias técnicas de preprocesamiento antes de entrenar el modelo:

- **Eliminación de variables**: Se eliminaron las variables con más de un 25% de valores faltantes.
- **Imputación de datos**: Los valores faltantes se imputaron utilizando la moda para variables categóricas y la media para variables numéricas.
- **Codificación de variables categóricas**: Algunas columnas categóricas se codificaron usando técnicas adecuadas.
- **Undersampling**: Se aplicó undersampling para equilibrar las clases.
- **División de datos**: Los datos fueron divididos en conjuntos de entrenamiento y validación.
- **Estandarización**: Los datos numéricos fueron estandarizados para mejorar el rendimiento del modelo.

Una parte clave del proceso fue la selección del número de características relevantes (`num_k`). Se probaron distintos valores de `num_k` para identificar el conjunto óptimo de características a incluir en el modelo.

## Modelo y Entrenamiento

Se implementó un modelo secuencial de red neuronal utilizando las siguientes configuraciones:

- **Capas ocultas**: Se emplearon capas con funciones de activación ReLU y variantes para manejar la no linealidad del modelo.
- **Capa de salida**: La capa final es una capa densa con activación sigmoide para manejar la clasificación binaria.
- **Capas Dropout**: Se introdujeron capas Dropout para evitar el sobreajuste.
- **Hiperparámetros**: Se ajustaron varios hiperparámetros durante el entrenamiento:
  - Función de pérdida: `binary_crossentropy`
  - Optimizador: Adam con distintas tasas de aprendizaje.
  - Número de iteraciones (`epochs`)
  - División de validación (`validation_split`)
  - Tamaño de lote (`batch_size`)

El modelo fue ajustado utilizando el conjunto de datos de entrenamiento y evaluado en el conjunto de validación, buscando maximizar tanto la precisión como la curva ROC-AUC.


