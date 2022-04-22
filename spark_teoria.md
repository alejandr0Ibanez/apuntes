# Introducción
 Spark se creó por la inceficiencia de MapReduce
 Es entre 10 y 20 veces más rápido que MR
 Procesa los datos de manera paralela y distribuida

 Se usa para: Data Science, Procesado de datos, Inteligencia Artificial, procesado gráfico

# Funcionamiento
> * Divide los datos en diferentes nodos
> * Las Tasks se envían al clúster, dónde se dividen entre los diferentes nodos
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


# Topología

                              ______________
                              Driver Program
                              ______________
                                    |
                                    |
                                    |
                              _______________
                              Cluster Manager
                              _______________
                             /      |       \
                            /       |        \
                           /        |         \
                         ______   ________   _______
                         Worker   Worker     Worker
                           |         |         |
                        Executor  Executor  Executor
                        ________  _________ __________

* El usuario lanza una aplicación
* Spark lanza el driver e invoca al método main()
* El driver contacta el Cluster Manager y pide recursos para lanzar los executors
* El Cluster Manager lanza los Executors de parte del driver
* El Driver corre a través de la aplicación
* El Driver envía trabajo a los executers en forma de Task
* Las tareas corren en los executers
* Siel main() finaliza, finalizan los executors y liberan los recursos del Cluster Manager