# keywrd analisis
Ésta es un repositorio para el análisis de palabras por dominio utilizando commoncrawl para identificar tendencias en la industria.

## Proceso de funcionamiento
### Captura de Datos de Dominio Específico
#### Captura de datos de NetApp en Common Crawl 
1. Inicia una instancia EC2 en Amazon AWS con 30GB SSD.
2. Conéctate a la instancia vía SSH.
3. Instala Git, clona y configura `cdx-index-client`.
4. Ejecuta `cdx-index-client.py` para capturar datos de NetApp, guárdalos en un archivo.
5. Clona `CommonCrawlDocumentDownload`.
6. Instala Java y configura `JAVA_HOME`.
7. Ejecuta `gradlew check` y descarga documentos.
8. Sube los datos a un bucket de AWS S3.

#### Captura de Datos de NetApp con Wget (opcional)
1. Usa `wget` para descargar archivos del sitio web de NetApp y súbelos a AWS S3.

### Eliminación de Etiquetas HTML
1. Inicia un nodo AWS EMR y conéctate a él.
2. Instala Git, descarga y configura Maven.
3. Clona `dkpro-c4corpus`, sincroniza datos de S3 y compílalo.
4. Crea un script para procesar archivos, ejecútalo y sube los resultados a S3.

### Proceso de Conteo de Palabras
1. Usa Spark para contar palabras en los datos de IBM y NetApp, y guarda los recuentos.

### Conversión de Texto a Parquet
1. Convierte texto a formato Parquet usando Spark.

### Eliminación de Palabras Vacías
1. Elimina puntuación y palabras vacías de los datos, guarda los resultados.

### Pipeline de Aprendizaje Automático: TF-IDF y K-Means
1. Implementa TF-IDF para vectorizar palabras y aplica K-Means para clustering.
2. Usa Spark para visualizar y evaluar los resultados del clustering.
