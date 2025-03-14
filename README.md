# Project1CV

# Proyecto de Visión por Computadora: Binarización y Discretización de Imágenes

Este proyecto tiene como objetivo procesar imágenes en formato PGM aplicando técnicas de binarización y discretización. Se utilizan métodos de umbralización global (Otsu) y adaptativa (Sauvola) para obtener imágenes binarias, se aplican técnicas de pre y postprocesamiento para mejorar la calidad, y se realiza la esqueletonización de las imágenes para extraer estructuras y construir grafos con clasificación de nodos.

## Descripción

El proyecto se divide en dos módulos principales:

### Binarización y Evaluación de Imágenes

- **Carga y preprocesamiento**: Se cargan imágenes en formato PGM y se aplica un filtro mediano para reducir ruido, seguido de corrección de iluminación mediante un filtro gaussiano y ecualización histográfica.
  
- **Binarización**:
  - **Método de Otsu**: Se aplica un umbral global para obtener la imagen binaria, seguido de operaciones morfológicas (apertura y cierre) para eliminar pequeños artefactos.
  - **Método de Sauvola**: Se utiliza un umbral adaptativo, con ajuste de parámetros según la iluminación de la imagen, y se realiza un postprocesamiento específico para mejorar la estructura resultante.
  
- **Evaluación**: Se calculan métricas de desempeño (Accuracy, Precision, Recall, Specificity, F1 Score) comparando la imagen original (umbralizada con la mediana) con la binarizada.

### Discretización y Análisis del Esqueleto

- **Esqueletonización**: Se utiliza la función `skeletonize` para obtener el esqueleto de la imagen binaria.
  
- **Construcción y clasificación del grafo**:
  - Se construye un grafo donde cada píxel del esqueleto es un nodo.
  - Se clasifican los nodos según su conectividad en “extremo”, “intermedio”, “bifurcación” o “trifurcación”.
  
- **Salida de datos**:
  - Se guarda la estructura del grafo y la clasificación de los nodos en un archivo JSON.
  - Se genera una visualización en la que se superpone el grafo sobre la imagen original, usando distintos colores para diferenciar cada tipo de nodo.

## Requisitos

- **Python 3.x**
- **Librerías**:
  - `numpy`
  - `matplotlib`
  - `pandas`
  - `seaborn`
  - `scikit-image`
  - `scipy`
  - `scikit-learn`
  - `opencv-python`
  - `networkx`

## Funciones desarrolladas

### Binarización y Evaluación

El proceso de binarización se realiza en varios pasos:

1. **Carga y preprocesamiento**:
   - Se cargan las imágenes desde el directorio `data/database` y se les aplica un preprocesamiento que incluye filtro mediano, corrección de iluminación y ecualización.

2. **Aplicación de métodos de binarización**:
   - **Otsu**:
     - Se calcula el umbral global con Otsu.
     - Se realiza postprocesamiento (eliminación de objetos pequeños y operaciones morfológicas) para refinar la imagen.
   - **Sauvola**:
     - Se aplica un umbral adaptativo con parámetros ajustables.
     - Se efectúa un postprocesamiento específico para mejorar la conexión de estructuras.

3. **Visualización y evaluación**:
   - Se muestran las imágenes originales y las binarizadas para comparar los resultados.
   - Se calculan y visualizan métricas de evaluación mediante heatmaps (Accuracy, Precision, Recall, Specificity y F1 Score).
