# Iniciar el shell
spark-shell

# Cambiar la versión de TLS a v1.2

echo 'export JAVA_TOOL_OPTIONS="-Dhttps.protocols=TLSv1.2"' >> ~/.bashrc
source ~/.bashrc

# Crear Scala Collection

val ***colection*** = List("e1","e2","e3","e4")

# Convertir a RDD
> Fichero de texto local 

val **variable** = sc.textFile("file:***ruta del fichero***")  

---

> Fichero de texto hdfs

val ***variable*** = sc.textFile("hdfs:****ruta del fichero***")

---

> De Scala Collection a RDD

val ***variable*** = sc.parallelize(***Scala Collection***)

# Contar número de líneas de un RDD
*rdd*.count()

# Mostrar RDD (a)
> El método collect es recomendable para RDDs, ya que muestra un Array de todos los elementos. Lanzará una excepción si es demasiado grande

*rdd*.collect()

----

> El método take devuelve el numero de filas que le indiquemos

*rdd*.take(5)

# Guardar RDD en fichero de texto en local

*rdd*.saveAsTextFile("file:***ruta***/***nombre***")

# Foreach

*rdd*.foreach(***function***)

# Filter/where (t)

> Se puede interpretar como el where en SQL

*rdd*.filter(***function***) --->  Ejemplo: frutas.filter(f => f.contains("p"))  
*Nos de volvería las frutas que contienen la letra p*

# Map (t)

> Ejecuta la función que le pasemos en cada línea del RDD. Devuelve las mismas filas que las que tiene el RDD original

*rdd*.map(***function***) ---> Ejemplo: lineas.map(l => l.split(" "))

# FlatMap (t)

> Igual que map pero nos devuelve el resultado línea por línea  
En este caso, cada cada palabra estará en una fila. Po reso devuelve más filas de las que tenía el RDD original

*rdd*.flatMap(***function***) ---> Ejemplo: lineas.flatMap(l => l.split(" "))


# ReduceByKey

> Agrupa por clave y a la vez ejecuta un reduce, es decir a mediad que agrupa por clave ejecutará la función que le pasemos

*rdd*.reduceByKey(***function***) ---> Ejemplo: lineas.recudeByKey(_+_)

> Esto agrupará por clave y sumará los valores de cada clave