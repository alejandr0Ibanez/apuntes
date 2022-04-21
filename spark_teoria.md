# Introducción
 Spark se creó por la inceficiencia de MapReduce
 Es entre 10 y 20 veces más rápido que MR
 Procesa los datos de manera paralela y distribuida

 Se usa para: Data Science, Procesado de datos, Inteligencia Artificial, procesado gráfico

# Funcionamiento
> * Divide los datos en diferentes nodos
> * Los nodos operan independientemente sobrelos datos en parelelo
> * Se combinan los resultados al acabar

>Hay que tener en cuenta la latencia del tráfico de red

* ### Arquitectura básica
                            Módulo de Spark
                                   |
                                   |
                                   |
                              Spark Core
                                   |
                                   |
                                   |
                                Cluster

### Spark Core
Contiene la funcionalidad básica de Spark (programación de tareas, gestion de memoria,recuperacion de fallos...)  

Aquí se aloja la API que define los RDD  

* Los Drivers acceden a Spark a través de SparkContext(sc)
* El Driver lanza operaciones en paralelo en un clúster
* El Driver define los datasets distribuidos en el clúster

