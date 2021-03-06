# spark-avro installation in linux or unix sytems.
Creating Avro file in linux or unix systems, required packages

# Initial step for Git clone link:
Run the below steps to clone the git repo.

git clone https://github.com/databricks/spark-avro.git

After cloning run below command

cd spark-avro

# git checkout v2.0.1 
./build/sbt assembly

# Initial Setup for Creating the Avro file: 
To install Avro module in PySpark, check the version PySpark and Scala versions installed in the terminus. Replace the versions (at avro_2.11 , scala-2.1, assembly-4.1.0 ) accordingly in the below command.

# Command for scala installation 
$ bin/spark-shell --packages com.databricks:spark-avro_2.11:4.0.0

# Command for pysaprk installation

pyspark --jars ~/spark-avro/target/scala-2.11/spark-avro-assembly-4.1.0-SNAPSHOT.jar

# Create data frame for the file which you want to convert into Avro
avrodf=spark.read.format("csv").option("header","true").load("myfile.csv")

# Create Avro file using the dataframe above
avrodf.write.format("com.databricks.spark.avro").save("myfile.avro")
