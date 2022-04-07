# Hive
Facilita la lectura, escritura y administración de grandes conjuntos de datos
* ## Muy parecido a SQL

# Impala
Parecido a Hive

# Pig
* ## Arrancar shell de Pig en local
  pig -x local

* ## Cargar datos en variables
  variable = LOAD 'fichero.txt' USING PigStorage(‘,’) as (key:tipo, col1:tipo, col2:tipo ...)
  
* ## Filtrar
  Es como el WHERE en SQL
  variable = FILTER _datos_ by nombre_columna == ALGO;
  
* ## Generar variable recorriendo otra
  variable = FOREACH _datos_ GENERATE col1, col23, col6 ...
  
* ## Guardar contenido en local
  STORE _datos_ INTO ‘ruta’;
