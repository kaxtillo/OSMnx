# OSMnx

Isócronas en Python

En las ciencias geoespaciales y la inteligencia de ubicación, las isócronas representan áreas geográficas accesibles en un tiempo determinado desde un punto específico. Por ejemplo, en el contexto de las distancias a pie, las isócronas son herramientas útiles para profesionales como los urbanistas que buscan comprender la accesibilidad y la conectividad dentro de un área determinada.

Al visualizar las isócronas, la ciencia de datos puede proporcionar una herramienta rápida y fácil de usar para ayudar a obtener información sobre el nivel de conectividad y accesibilidad a pie de los vecindarios, ayudar a identificar áreas que están bien conectadas y señalar áreas potenciales de mejoras de infraestructura.

En este artículo, explicaremos cómo generar isócronas de distancia a pie mediante los paquetes de Python NetworkX (diseñado para análisis de grafos) y OSMNnx (que combina OpenStreetMap y NetworkX). Tomamos como ejemplo Perímetro urbano de la ciudad de Poayán. Primero, descargamos la red vial del área, seleccionamos un nodo aleatorio (una intersección aleatoria) y dibujamos las isócronas de distancia a pie de 5, 10, 20 y 30 minutos a su alrededor.

Todas las imágenes fueron creadas por el autor.

1. Adquisición de datos
Primero, importaremos OSMnx y lo usaremos para descargar los límites administrativos del área objetivo. Puede reemplazarlo por el nombre de cualquier lugar que prefiera, que puede consultar fácilmente en OpenStreetMap. A continuación, usaremos OSMnx para descargar la red vial del área objetivo y mostrar el tamaño de esta red de nodos en términos de número de intersecciones y segmentos viales. Además, debemos especificar el tipo de red , que ahora está configurado como “walk” para obtener solo las partes transitables de la red vial.

2. Polígonos de alcanzabilidad
Ahora, construyamos los polígonos isócronos de transitabilidad. Para ello, primero, asumimos una velocidad promedio de caminata de 5 km/h (1,39 m/s) y, con esta velocidad, asignamos un tiempo de caminata a cada borde de la red vial. Luego, seleccionamos un nodo aleatorio para comenzar y definimos la lista de rangos de transitabilidad: 5, 10, 20 y 30 minutos.

Para crear los polígonos de accesibilidad, primero usamos la función integrada de NetworkX llamada _ego graph , que devuelve un subgrafo específico de la red vial original que contiene todos los nodos dentro de un radio determinado, según las métricas de distancia que elijamos. Si seleccionamos _travel time , podemos devolver el subgrafo accesible en un tiempo determinado y almacenarlo como un atributo de borde llamado _travel time .

Luego, necesitamos extraer todas las coordenadas de los nodos de este subgrafo, que almacenaremos en la lista _node points . Finalmente, las convertimos en un polígono, lo graficamos y lo guardamos para la siguiente sección.

El resultado: todos los polígonos isócronos de transitabilidad, para 5, 10, 20 y 30 minutos, respectivamente

3. Visualizando las isócronas
Por último, utilicemos Matplotlib y la coloración de rojo a verde para trazar y visualizar las isócronas sobre la red de carreteras.
