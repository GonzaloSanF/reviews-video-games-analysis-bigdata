# Análisis de Videojuegos en Amazon

## Introducción
Cada día, millones de personas disfrutan de videojuegos en diversas plataformas, y Amazon se ha convertido en uno de los mayores mercados para la compra de videojuegos y accesorios relacionados. En este proyecto, nos propusimos analizar los datos generados por las valoraciones de los usuarios y los productos de videojuegos disponibles en Amazon.

El objetivo principal es proporcionar información útil tanto para los jugadores como para los desarrolladores y vendedores, permitiendo identificar tendencias, preferencias y patrones de consumo.

Para abordar este análisis, empleamos técnicas de Big Data y procesamiento paralelo, dadas las dimensiones del dataset y la complejidad de las operaciones necesarias.

---

## Modelo de datos y origen
### Fuentes de datos
Los datos analizados provienen de dos datasets principales:

1. **Valoraciones (reviews.json)**  
   Este dataset contiene millones de valoraciones de usuarios sobre videojuegos, incluyendo información como puntuaciones, comentarios y fechas.

2. **Metadatos de videojuegos (metabooks.json)**  
   Contiene información detallada sobre los videojuegos, como títulos, categorías, precios, y otros atributos relevantes.

Ambos datasets se redujeron para ajustarse a las limitaciones del entorno de trabajo.

---

## Descripción técnica
### Scripts desarrollados
En este proyecto, creamos varios scripts en Python utilizando PySpark. A continuación, se describen algunos de ellos:

- **formatoCategoria.py**  
  Este script genera un gráfico circular que muestra los cinco formatos más populares de videojuegos en una categoría específica, basándose en el número de valoraciones. Los formatos restantes se agrupan en una categoría llamada "Otros formatos". También genera un archivo CSV con los detalles completos.

  **Uso:**  
  ```bash
  spark-submit formatoCategoria.py "Action"
