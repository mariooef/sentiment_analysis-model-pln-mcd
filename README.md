# sentiment_analysis-model-pln-mcd


### Tarea 3 de la materia de Procesamiento de Lenguaje Natural 

Modelo para realizar análisis de sentimientos de un corpus de reseñas de viaje, usando n-gramas para clasificar si la opinión es positiva o negativa.



### Descripción general
------------

##### Limpieza y Preprocesamiento

1. Primeramente se hace un análisis exploratorio de los datos para conocer el corpus.

2. Después, se normaliza el texto para las columnas 'Title' y 'Opinion' de la siguiente manera:
   - Se sustituyen valores nulos por strings vacíos 
   - Se eliminan duplicados
   - Se eliminan comillas
   - Se convierte a minúsculas
   - Se seleccionan sólo opiniones en español
   - Se eliminan caracteres acentuados
   - Se eliminan caracteres especiales

1. Finalmente, el corpus se separa en dos conjuntos y dado que existe un desbalance de clases, esto es tomado en cuenta para la creación de estos conjuntos:
- Entrenamiento: 80%
- Validación: 20%

##### Modelo de Análisis de Sentimientos

En este trabajo, se utilizan sólamente n-gramas para la clasificación de polaridad en el texto:

1. En el conjunto de entrenamiento, separamos los datos (documentos) de la clase positiva y negativa.
2. Se aplica la técnica de sobremuestreo de la clase minoritaria, para tratar el tema del desbalance de clases.
3. El entrenamiento del modelo consiste en:
   - Tokenizar
   - Generar los n-gramas o skip-gramas (el usuario selecciona n y k)
   - Se realiza un conteo de frecuencias de los n-gramas en los documentos de clase positiva y negativa.
   - Se genera un score donde se suma/resta el conteo de frecuencias en positivos y negativos
   - Finalmente, se define un umbral para el score, con el cual se realiza la clasficiación.
1. Para la validación, se usa el modelo en el conjunto de validación:
    - Se calcula el F1-Score
    - Se genera la matriz de confusión
2. Para la fase de pruebas, el conjunto de pruebas será dado por el profesor en clase para la evaluación final del desempeño del modelo.

----NOTA-------------------------------------------------------------------------------------------------------------------------------------------------------------------
##### Modelo de Análisis de Sentimientos Alternativo(Incluyendo title)
A una manera de prueba y seguir mejorando nuestro modelo, se desarrolló un segundo modelo alternativo incluyendo el factor del title de cada opinión para verificar si esta acción o que tanto peso tendría el title en la mejora para clasificar mejor, sin disminuir el score o bien aumentándolo.  

Este documento está en este repositorio: 2.0-modelo-AnálisisSentimientos-title.ipynb

Al ejecutar el modelo encontramos que no existe una diferencia significativa y de peso que nos hicieran inclinarnos por esta alternativa, y esto solo agregaría más carga al proceso de análisis sin resultados diferentes y favorables.  

Esto no llevo a pensar en la influencia del mal etiquetado en las opiniones del documento sé que tuvo para entrenamiento.  

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------

### Instrucciones de ejecución
------------
1. Clonar el repositorio
2. Ejecutar notebook "1.0-Preprocesamiento.ipynb"
3. Ejecutar notebook "2.0-modelo-AnálisisSentimientos.ipynb"
