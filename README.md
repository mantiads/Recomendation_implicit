# <p align="center">SISTEMA DE RECOMENDACION BASADO EN FEEDBACK IMPLICITO</p>

[Acceso a archivo Jupyter.](https://github.com/mantiads/Clustering/blob/main/clusters.ipynb)


## INTRODUCCION

En la actualidad, los sistemas de recomendación desempeñan un papel crucial en la mejora de las experiencias personalizadas para los usuarios en diversas plataformas. La recomendación de productos basada en el comportamiento del usuario se ha convertido en un área de investigación y desarrollo esencial para proporcionar sugerencias relevantes y adaptadas a las preferencias individuales.

En este proyecto, nos centramos en un conjunto de datos de feedback implícito derivado de las contrataciones de productos por parte de los usuarios a lo largo de 17 meses consecutivos. Este feedback implícito, en forma de acciones realizadas por los usuarios, proporciona valiosa información sobre sus preferencias y comportamientos, lo que nos permite construir un modelo de recomendación efectivo.

## SELECCION DE MODELO

La elección del algoritmo de factorización de matrices, y en particular de Alternating Least Squares (ALS) implementado en la biblioteca Implicit, se basa en su eficacia para manejar feedback implícito. Dado que en nuestro conjunto de datos no contamos con calificaciones explícitas, sino con acciones como contrataciones de productos, necesitamos un enfoque que se adapte a esta naturaleza implícita del feedback.

## PREPARACION DE DATOS
En primer lugar, extraemos las interacciones realizadas por cada uno de los clientes con los 15 productos de la compañía. Luego, nos quedamos únicamente con los usuarios de nuestra base de datos que han realizado interacciones con los productos. Buscamos que las contrataciones repetidas tengan mayor peso, pero para que este efecto disminuya a medida que aumenta el número de contrataciones repetidas y el impacto de un fanático del producto, utilizaremos BM25 (Best Matching 25).

## HIPERPARAMETROS Y EVALUACION
Seleccionamos la métrica de evaluación precision_at_k, que mide la precisión de los top k elementos recomendados. Después de realizar una búsqueda de hiperparámetros (la cual debemos diseñar, ya que la biblioteca seleccionada no cuenta con esta opción), entrenamos el modelo con los hiperparámetros que arrojan una mejor métrica, en este caso, 0.30 (lo que significa que el 30% de los elementos recomendados en las listas de los usuarios son relevantes para ellos).

## RECOMENDACIONES
Obtenemos la lista de productos con mayor puntuación por usuario, excluyendo de la misma los productos que ya han sido consumidos anteriormente.
