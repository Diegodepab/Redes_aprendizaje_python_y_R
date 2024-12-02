# red_aprendizaje_profundo

# Proyecto de Predicción con LASSO y Redes Neuronales Profundas

Este proyecto implementa un análisis de clasificación utilizando dos enfoques de modelado: **LASSO** (Least Absolute Shrinkage and Selection Operator) y **Redes Neuronales Profundas**. El objetivo es comparar el rendimiento de ambos modelos en un conjunto de datos de expresión génica o similares, evaluando sus métricas de rendimiento (precisión y AUC) a través de validación cruzada.

## Flujo de Trabajo

1. **Carga de Datos**  
   Los datos se cargan desde un archivo `RData` que contiene la información de las muestras y las características, además de los pliegues para la validación cruzada.

2. **Preprocesamiento**  
   Se realiza la normalización de las características para evitar problemas de escala, dividiendo las variables en dos bloques y normalizándolas por separado para mejorar la eficiencia computacional.

3. **Selección de Características**  
   Se aplica un filtro de características mediante una prueba t (o cualquier otro procedimiento de selección), con corrección por pruebas múltiples. Las características retenidas son las que se utilizan en el modelado.

4. **Entrenamiento y Evaluación de Modelos**  
   Se entrena un modelo de regresión LASSO y una red neuronal profunda para cada pliegue de la validación cruzada (10 pliegues en este caso).  
   
   - **LASSO**: Se entrena utilizando la función `glmnet` para ajustar un modelo de regresión lineal con regularización L1.
   - **Red Neuronal Profunda**: Se entrena un modelo utilizando la librería `h2o`, que permite la construcción de redes neuronales profundas con una arquitectura configurable.

5. **Evaluación de Desempeño**  
   Se evalúa el rendimiento de los modelos utilizando medidas como la precisión (accuracy) y el área bajo la curva ROC (AUC) tanto para el conjunto de entrenamiento como para el conjunto de prueba.

6. **Resultados**  
   Los resultados de las métricas de rendimiento (precisión y AUC) se almacenan en un archivo CSV para su posterior análisis y comparación. También se guarda un archivo `RData` con los resultados completos de las repeticiones.

## Instalación y Requisitos

Para ejecutar este proyecto, necesitas tener instaladas las siguientes librerías de R:

- `glmnet` (para el modelo LASSO)
- `h2o` (para redes neuronales profundas)
- `pROC` (para calcular el AUC)
- Otras librerías necesarias (dependencias internas).

Puedes instalar las librerías necesarias usando los siguientes comandos en R:

```R
install.packages("glmnet")
install.packages("pROC")
install.packages("h2o")
```

