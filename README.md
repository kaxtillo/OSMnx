# OSMnx

##Isócronas en Python

En las ciencias geoespaciales y la inteligencia de ubicación, las isócronas representan áreas geográficas accesibles en un tiempo determinado desde un punto específico. Por ejemplo, en el contexto de las distancias a pie, las isócronas son herramientas útiles para profesionales como los urbanistas que buscan comprender la accesibilidad y la conectividad dentro de un área determinada.

Al visualizar las isócronas, la ciencia de datos puede proporcionar una herramienta rápida y fácil de usar para ayudar a obtener información sobre el nivel de conectividad y accesibilidad a pie de los vecindarios, ayudar a identificar áreas que están bien conectadas y señalar áreas potenciales de mejoras de infraestructura.

En este artículo, explicaremos cómo generar isócronas de distancia a pie mediante los paquetes de Python NetworkX (diseñado para análisis de grafos) y OSMNnx (que combina OpenStreetMap y NetworkX). Tomamos como ejemplo Perímetro urbano de la ciudad de Poayán. Primero, descargamos la red vial del área, seleccionamos un nodo aleatorio (una intersección aleatoria) y dibujamos las isócronas de distancia a pie de 5, 10, 20 y 30 minutos a su alrededor.

Todas las imágenes fueron creadas por el autor.
