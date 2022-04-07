# Hadoop
* ## Listar directorio
  hadoop fs -ls (ruta)
  
* ## Mostrar
  hadoop fs -cat (ruta)

* ## Copiar (Local --> HDFS)
  hadoop fs -put [origen] [destino]
  
* ## Copiar (HDFS --> Local)
  hadoop fs -get [origen] [destino]
  
* ## Crear directorio
  hadoop fs -mkdir [(ruta)nombre]
  
* ## Borrar directorio y su contenido
  hadoop fs -rm -r [(ruta)nombre]
  
* ## Ejecutar aplicacion
  hadoop jar [fichero.jar] (Clase Main) (Parámetros)
  
* ## Cancelar un Job
  hadoop job -kill [jobId]
