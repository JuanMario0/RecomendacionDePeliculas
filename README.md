🎬 Sistema de Recomendación de Películas 🍿
Este proyecto combina técnicas de filtrado colaborativo y recomendación basada en contenido para ofrecer sugerencias personalizadas de películas a los usuarios. A continuación, se detallan los resultados y el proceso seguido.

📊 Resultados Obtenidos
1. Preprocesamiento de Datos
Se cargaron los datasets movies.csv y ratings.csv.

Se combinaron ambos datasets utilizando movieId como clave.

El conjunto de datos combinado contiene:

userId: Identificador único del usuario.

movieId: Identificador único de la película.

rating: Calificación otorgada por el usuario (escala de 1 a 5).

timestamp: Fecha y hora de la calificación.

title: Título de la película.

genres: Géneros de la película (separados por |).

Ejemplo de las primeras filas:

plaintext
Copy
userId  movieId  rating   timestamp                title                        genres
0       1      296     5.0  1147880044  Pulp Fiction (1994)  Comedy|Crime|Drama|Thriller
1       3      296     5.0  1439474476  Pulp Fiction (1994)  Comedy|Crime|Drama|Thriller
2. Filtrado Colaborativo con SVD
Se utilizó el algoritmo SVD (Singular Value Decomposition) para predecir calificaciones de películas no vistas por los usuarios.

El modelo se entrenó con el conjunto de entrenamiento (trainset).

Se evaluó el modelo utilizando el RMSE (Root Mean Squared Error), obteniendo un valor de 0.7776, lo que indica un buen rendimiento.

Ejemplo de predicciones para el usuario 1:

python
Copy
user_predictions = []
for movie_id in all_movies:
    predicted_rating = model.predict(uid=1, iid=movie_id).est
    user_predictions.append((movie_id, predicted_rating))
3. Recomendación Basada en Contenido
Se utilizó TF-IDF para convertir los géneros de las películas en una representación numérica.

Se calculó la similitud de coseno entre películas basada en sus géneros.

Se implementó una función para obtener recomendaciones basadas en contenido.

Ejemplo de uso:

python
Copy
print(get_recommendations('Toy Story (1995)'))
Resultado:

plaintext
Copy
2203                                           Antz (1998)
3021                                    Toy Story 2 (1999)
3653        Adventures of Rocky and Bullwinkle, The (2000)
3912                      Emperor's New Groove, The (2000)
4780                                 Monsters, Inc. (2001)
9949     DuckTales: The Movie - Treasure of the Lost La...
10773                                     Wild, The (2006)
11604                               Shrek the Third (2007)
12969                       Tale of Despereaux, The (2008)
17431    Asterix and the Vikings (Astérix et les Viking...
🛠️ Tecnologías Utilizadas
Python como lenguaje principal.

Bibliotecas:

scikit-surprise para el modelo SVD.

scikit-learn para TF-IDF y similitud de coseno.

pandas y numpy para manipulación de datos.

🚀 Cómo Usar
Preprocesamiento:

Cargar y combinar los datos de películas y calificaciones.

Limpiar y preparar los datos (manejo de valores nulos, normalización de géneros).

Entrenamiento:

Entrenar el modelo SVD con las calificaciones de los usuarios.

Calcular la matriz de similitud de coseno para las películas.

Recomendaciones:

Generar recomendaciones basadas en contenido para una película dada.

Generar recomendaciones personalizadas para un usuario específico usando SVD.

Combinar ambas recomendaciones en un enfoque híbrido.

Evaluación:

Calcular métricas como RMSE para evaluar el modelo.

⬇️ Instalación
Clona el repositorio:

bash
Copy
git clone https://github.com/tu-usuario/recomendacion-peliculas.git
Instala las dependencias:

bash
Copy
pip install scikit-surprise scikit-learn pandas numpy
🤝 Contribuciones
¡Las contribuciones son bienvenidas! Si deseas mejorar el proyecto, abre un issue o envía un pull request. ¡Juntos podemos hacerlo mejor! 💪
