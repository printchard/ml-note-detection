# Detección de notas usando Machine Learning

Ricardo Adolfo Fernández Alvarado - A01704813

## Introducción

En las partituras musicales existen ciertos glifos conocidos como las [figuras musicales](https://es.wikipedia.org/wiki/Figura_musical). Estos glifos representan el ritmo de las notas en una canción, atribuyendo a cada glifo un valor específico.

Este proyecto busca utilizar Machine Learning para generar un clasificador de imágenes que categorize imágenes en las siguientes categorías:

- Redonda
- Blanca
- Negra
- Corchea
- Semi Corchea

## Marco Teórico

Actualmente, existen diversas técnicas para el reconocimiento óptico de imágenes de partituras musicales. Cómo se muestra en [1], se pueden utilizar capas convolucionales para extraer los patrones de las imágenes que contienen símbolos musicales. Este proceso en específico utiliza RNNs para poder predecir el siguiente símbolo musical, ya que el dataset que se utiliza está escrito a mano, por lo que los símbolos varían entre sí y entre piezas.

Adicionalmente, en [2] se utiliza una combinación de CNN y RNN para convertir partituras musicales en su representación [\*\*kern](https://www.humdrum.org/rep/kern/). En su modelo de entrenamiento se utiliza una CNN para extraer las características importantes (las notas en sí mismas), mientras que la RNN se utiliza para generar la salida en formato \*\*kern.

Tomando estos procedimientos, se pueden utilizar las configuraciones de capas convolucionales como lo hacen estos artículos científicos para extraer las características importantes de las imágenes, acompañado de capas densas para clasificarlas.

## Dataset

El dataset fue extraído de [Kaggle](https://www.kaggle.com/datasets/kishanj/music-notes-datasets?resource=download). El mismo cuenta con 5000 imágenes, 1000 sobre cada una de las categorías mencionadas en la introducción. Cada imagen consta de una nota, en una resolución de 64x64 píxeles en blanco y negro.

### Preprocesamiento

Para el preprocesamiento, se utilizó el script dentro de `preprocessing.ipynb` para separar el 20% de los datos para probar el modelo una vez que esté entrenado.

En cuanto a Data Generation, se considera que existen suficientes imágenes para el entrenamiento del modelo. En el tema de Data Augmentation es un poco más complicado. El dataset ya cuenta con notas ligeramente distorsionadas, estiradas, ligeramente rotadas y en tipografías diferentes. Si el modelo no logra clasificar algunas imágenes, podríamos aumentar el dataset aplicando transformaciones de estiramiento o redimensionamiento. Se tendría que evitar la rotación excesiva, ya que, de ser rotados, los símbolos musicales se volverían incorrectos. Con esto, se podría comparar resultados y determinar si es mejor o no aumentar el dataset.

## Fuentes

[1] A. Baró, P. Riba, J. Calvo-Zaragoza, and A. Fornés, "From Optical Music Recognition to Handwritten Music Recognition: A baseline," Pattern Recognition Letters, vol. 123, pp. 1–8, Feb. 2019, doi: 10.1016/j.patrec.2019.02.029.

[2] X.-Y. Zhang and J.-L. Hsu, "Full-Scale piano score recognition," Applied Sciences, vol. 15, no. 5, p. 2857, Mar. 2025, doi: 10.3390/app15052857.
