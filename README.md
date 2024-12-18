1. Introducción
El mercado de los videojuegos ha crecido exponencialmente en los últimos años, convirtiéndose en una de las industrias más lucrativas del mundo. Con millones de usuarios dejando valoraciones y reviews en plataformas como Amazon, surge una oportunidad única para analizar tendencias, comportamientos y preferencias en el sector.

Este proyecto se centra en el análisis de datos relacionados con videojuegos disponibles en Amazon, con el objetivo de extraer información valiosa para consumidores y desarrolladores. Nuestro interés radica en entender patrones de consumo, identificar videojuegos destacados y ofrecer recomendaciones basadas en datos.

A pesar del entusiasmo y planificación detrás del proyecto, varios problemas técnicos obstaculizaron la ejecución completa de los análisis. No obstante, se documentan aquí los avances realizados y las dificultades encontradas, así como propuestas para futuras mejoras.

2. Modelo de datos y origen
Para este proyecto, trabajamos con dos datasets principales, ampliamente utilizados en investigaciones relacionadas con Amazon:

reviews.json: Incluye valoraciones de usuarios, con información sobre puntuaciones, descripciones, IDs de producto y más.
meta_Video_Games.json: Contiene metadatos como el título de los videojuegos, precios, categorías, descripciones y otros detalles.
Estos datasets son significativamente grandes (21GB y 4GB respectivamente), lo que plantea desafíos tanto técnicos como computacionales. Para las pruebas iniciales, usamos versiones reducidas de estos archivos.

3. Descripción técnica
Software desarrollado
Se implementaron varios scripts para responder a preguntas clave del análisis. Estos son los más relevantes:

formatoCategoria.py: Genera un gráfico circular con los formatos de videojuegos más populares en una categoría, agrupando los menos frecuentes bajo la categoría "Otros formatos".
categoryPriceEvolution.py: Analiza cómo han evolucionado los precios de videojuegos en una categoría específica.
mostRatings.py: Presenta un ranking de videojuegos con más valoraciones y su puntuación media.
recommendedByViewed.py: Recomienda videojuegos en función de búsquedas similares realizadas por otros usuarios.
outstandingAuthors.py: Identifica desarrolladores destacados basándose en el promedio de valoraciones y el número de reseñas recibidas.
Problemas técnicos encontrados
Aunque los scripts fueron diseñados y probados localmente, nos encontramos con importantes barreras durante la ejecución en Google Cloud. Estos fueron los problemas principales:

Falta de permisos en Google Cloud Console: Al intentar ejecutar los scripts, se produjeron errores relacionados con la configuración de permisos en la plataforma. Esto afectó el acceso a los buckets y la capacidad de lanzar trabajos en el cluster.

Reinicio y recreación de recursos: Intentamos resolver los problemas reiniciando el cluster y recreando los buckets de almacenamiento. Sin embargo, esto generó nuevos inconvenientes, como conflictos entre zonas y restricciones de Google Cloud.

Limitaciones en la infraestructura: Aunque las máquinas ofrecían recursos suficientes en términos de CPU y memoria, los problemas de configuración y permisos impidieron su aprovechamiento.

Estos problemas nos forzaron a trabajar principalmente con simulaciones y pruebas locales, lo que limitó el alcance del análisis real.

4. Resultados
Debido a los problemas técnicos descritos, no fue posible ejecutar los scripts en el entorno de Google Cloud. Sin embargo, se generaron ejemplos y simulaciones basadas en subconjuntos de datos, que ilustran los tipos de análisis que el proyecto buscaba realizar:

Popularidad de formatos: Un gráfico circular muestra cómo se distribuyen los formatos más utilizados en una categoría específica.
Tendencias de precios: Simulaciones gráficas demuestran cómo los precios de videojuegos han cambiado con el tiempo en categorías seleccionadas.
Recomendaciones basadas en búsquedas: Tablas de ejemplo presentan videojuegos recomendados basados en patrones de búsqueda de usuarios.
Estos resultados, aunque simulados, reflejan el potencial del análisis planteado.

5. Conclusión y próximas mejoras
A pesar de los obstáculos encontrados, este proyecto sirvió para identificar los desafíos técnicos de trabajar con datos grandes en plataformas como Google Cloud. En el futuro, proponemos las siguientes mejoras:

Resolución de problemas de permisos: Una configuración más detallada y documentación exhaustiva de los permisos requeridos para ejecutar scripts en Google Cloud.

Automatización de recursos: Uso de herramientas de gestión como Terraform para evitar errores en la creación de clusters y buckets.

Ampliación de pruebas locales: Validar scripts con subconjuntos de datos más grandes antes de migrar a entornos de producción.

El aprendizaje obtenido durante el desarrollo de este proyecto será de gran utilidad para futuros análisis de datos a gran escala.