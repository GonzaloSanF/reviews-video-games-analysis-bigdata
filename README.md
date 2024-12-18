
## Mirar el proyecto, esto es lo que teóricamente hubiera habido de no habernos topado con errores persistentes estos dias al crear el cluster y no dar con ello.
## En el bucket Errores hay una explicación y capturas de ello.

# README - Proyecto Big Data y Cloud Computing

## 1. Descripción del problema

Cada día, millones de personas disfrutan de videojuegos en diversas plataformas, y Amazon se ha convertido en uno de los mayores mercados para la compra de videojuegos y accesorios relacionados. En este proyecto, nos propusimos analizar los datos generados por las valoraciones de los usuarios y los productos de videojuegos disponibles en Amazon.

El objetivo principal es proporcionar información útil tanto para los jugadores como para los desarrolladores y vendedores, permitiendo identificar tendencias, preferencias y patrones de consumo.

Para abordar este análisis, empleamos técnicas de Big Data y procesamiento paralelo, dadas las dimensiones del dataset y la complejidad de las operaciones necesarias.

El objetivo principal del proyecto es analizar datos de videojuegos utilizando **Google Cloud Platform (GCP)** y herramientas de procesamiento distribuido como **Apache Spark** en un entorno Dataproc. Este análisis busca proporcionar insights clave sobre el rendimiento de ventas, categorías más exitosas, y tendencias temporales mediante patrones de procesamiento como:
- **Numerical Summarization**: Estadísticas descriptivas (media, mediana, percentiles).
- **Inverted Index**: Búsqueda eficiente de regiones y fechas de ventas.
- **Filtering**: Filtrado de datos por condiciones (años, plataformas, etc.).
- **Frecuencias**: Conteo de juegos por regiones y plataformas.

El problema surge debido a la gran cantidad de datos existentes, lo que requiere soluciones escalables y distribuidas para obtener resultados en tiempos razonables.

---

## 2. Necesidad de Big Data y Cloud
El uso de Big Data y Cloud se justifica por:
- **Volumen de datos**: Datos extensos sobre ventas globales de videojuegos.
- **Velocidad de procesamiento**: Necesidad de analizar rápidamente grandes volúmenes de información.
- **Escalabilidad**: Cloud permite ajustar recursos según necesidades de procesamiento.
- **Accesibilidad**: GCP facilita la gestión de clústeres con Dataproc, sin configuraciones complejas.

---

## 3. Descripción de los datos
El dataset utilizado incluye información de ventas de videojuegos con las siguientes columnas:
- **Name**: Nombre del videojuego.
- **Platform**: Plataforma (PS4, Xbox, PC, etc.).
- **Year**: Año de lanzamiento.
- **Genre**: Género del juego.
- **Publisher**: Editorial del juego.
- **NA_Sales, EU_Sales, JP_Sales**: Ventas en Norteamérica, Europa y Japón (en millones).
- **Global_Sales**: Ventas globales totales.

Los datos están almacenados en archivos **CSV** dentro de buckets de **Google Cloud Storage**.

---

## 4. Descripción de la aplicación
La aplicación consiste en:
1. **Configuración de clúster Dataproc**: Para ejecutar tareas de Spark.
2. **Procesamiento de datos**: Scripts en **PySpark** que ejecutan los patrones de análisis definidos (resúmen numérico, filtros, etc.).
3. **Resultados**: Los resultados se exportan a **archivos CSV** y se almacenan en un bucket de salida en GCS.

---

## 5. Diseño del software
La estructura del proyecto es la siguiente:

```plaintext
- datasets/
    - videojuegos-input/
        - Video_Games.json
- scripts/
    - numerical_summary.py
    - inverted_index.py
    - filtering.py
    - frequency_analysis.py
- resultados/
- README.md
```

- **datasets**: Datos originales y procesados.
- **scripts**: Scripts en PySpark para realizar los análisis.
- **resultados**: Directorio donde se almacenarían los resultados finales.

---

## 6. Uso del software
### Ejecución de scripts en Dataproc
1. Subir datos al bucket de entrada (**videogames-input**).
2. Crear un clúster Dataproc.
3. Ejecutar los scripts de PySpark desde la terminal o Cloud Shell:
   ```bash
   gcloud dataproc jobs submit pyspark numerical_summary.py --cluster=[nombre-cluster] --region=[region] -- \
       --input=gs://videogames-input/Video_Games.json --output=gs://videogames-output/results.csv
   ```
4. Revisar los resultados en el bucket de salida.

---

## 7. Evaluación del rendimiento
La evaluación del rendimiento se realizaría midiendo:
- **Tiempo de ejecución**: Comparación de tiempos entre ejecuciones con diferentes recursos asignados.
- **Uso de recursos**: Monitoreo del clúster en GCP.
- **Escalabilidad**: Verificar el rendimiento con diferentes volúmenes de datos.

---

## 8. Características avanzadas
- **Automatización con scripts**: Ejecución automatizada de tareas con shell scripts.
- **Component Gateway**: Habilitar acceso a interfaces como Spark UI para monitoreo.
- **Redes personalizadas**: Uso de redes VPC y subredes configuradas para el clúster.
- **Filtrado dinámico**: Parametrización de los scripts para diferentes condiciones de filtrado.

---

## 9. Conclusiones y referencias
### Conclusiones
El proyecto demuestra cómo **Google Cloud Dataproc** permite realizar análisis de datos a gran escala utilizando **Apache Spark**. A pesar de los desafíos encontrados durante la implementación, la estructura planteada cumple con los requerimientos de Big Data.

### Referencias
1. Documentación oficial de GCP: https://cloud.google.com/docs
2. Apache Spark: https://spark.apache.org
3. Ejemplo de configuración de Dataproc: https://cloud.google.com/dataproc/docs/concepts


