# Sqoop
Es una herramienta para transferir datos entre RDBMs y Hadoop

* ## Ver BD concectada a Sqoop por ejemplo, Mysql
  sqoop list-databases --connect jdbc:mysql://localhost --username root --password cloudera

* ## Ver tablas de la base de datos pruebadb
  sqoop list-tables --connect jdbc:mysql://localhost/pruebadb --username root --password cloudera
  
* ## Importar tabla de Mysql a Hive
  sqoop import --connect jdbc:mysql://localhost/pruebadb --table tabla_prueba --username root --password cloudera -m 1 --hive-import --hive-overwrite --hive-table prueba_sqoop_hive.tabla_prueba
  
# Flume
Es un sistema para recopilar, agregar y mover grandes cantidades de dtaos de diferentes fuentes a un almacen de datos centralizado

* ## Ejemplo fichero de configuracion

  #Name the components on this agent
  a1.sources = r1 
  a1.sinks = k1 
  a1.channels = c1  
  
  #Describe/configure the source 
  a1.sources.r1.type = netcat 
  a1.sources.r1.bind = localhost 
  a1.sources.r1.port = 44444 
  
  #Describe the sink 
  a1.sinks.k1.type = logger 
  
  #Use a channel which buffers events in memory 
  a1.channels.c1.type = memory 
  a1.channels.c1.capacity = 1000 
  a1.channels.c1.transactionCapacity = 100 
  
  #Bind the source and sink to the channel 
  a1.sources.r1.channels = c1 
  a1.sinks.k1.channel = c1
  
# Arrancar un agente flume cuyo archvio de configuración está en /home/cloudera/example.conf
  flume-ng agent --conf conf --conf-file /home/cloudera/example.conf --name a1 -Dflume.root.logger=INFO,console
