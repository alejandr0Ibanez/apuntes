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


# Transformaciones

>Hasta que no se ejecute una acción la transformación no se ejecuta. Para que no se ejecute innecesariamente utilizaremos ***persist()***  

>Devuelve un RDD

* map() >>> Aplica una función a cada elemento del RDD y devuelve un RDD

* flatMap() >>> Aplica una funcion al RDD y devuelve un RDD en el que cada fila es lo devuelto por cada iteración

* filter() >>> Devuelve un RDD con los elementos que cumplen la condición

* distinct() >>> Elimina los duplicados

* union() >>> Devuelve un RDD de ambos elementos de los RDDs

* intersection() >>> Devuelve sólo los elementos encontrados en ambos RDDs

* subtract() >>> Elimina los elementos de un RDD en función de si está en otro

* cartesian() >>> Producto cartesiano con otro RDD

# Acciones
> No devuelve un RDD

* collect() >>> Devuelve todos los elementos de un RDD

* count() >>> Numero de elementos de un RDD

* countByValue() >>> Numero de veces que cada elemento aparece en un RDD

* take(n) >>> Devuelve los n elementos de un RDD

* top(n) >>> Devuelve los n primeros elementos de un RDD

* takeOrdered(n)(orden) >>> Devuelve n elementos con la condición deseada

* reduce(***func***) >>> Combina os elementos del RDD con la función deseada P.E: x + y