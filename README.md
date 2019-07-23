# Zeppelin + Spark
This is an orchestrated set of Docker and Docker Compose files that will allow for local experimentation with Zeppelin and Spark.  This example was created to support work with the Hortonworks tutorial from https://hortonworks.com/tutorial/learning-spark-sql-with-zeppelin/.

#Prerequisites
Before running this example, you need to be sure that Docker has been allocated enough resources on your machine.  At a minimum, you will need to allocate 8Gb (16Gb is preferred) of memory to your docker host.

## Getting Up and Running
There are a couple of things that you need to do in order to get off the ground with this package.

1. Build the customized Zeppelin image using `docker-compose build`.  This step can take a bit to download the images and packages; maybe grab some 
1. Launch the Docker services with `docker-compose up`.
1. Visit [http://localhost:8090](http://localhost:8090) to see the Zeppelin UI and get working.

## Notes on ORC use.
If you want to use ORC file writing (necessary if you want to use the example notebook), you will need to update the Spark interpreter to use the Native implemenation of ORC.  To do this, you will need to do the following:

1. From the Zeppelin UI, go to the interpreter settings at [http://localhost:8090/#/interpreter](http://localhost:8090/#/interpreter).
1. Search for, or scroll down to, the Spark interpreter.
1. Click the "Edit" button.
1. Add a new value by using the text input at the end of the list of properties.
1. Enter a property name of `spark.sql.orc.impl`, select an input type of `string`, and provide a value of `native`.
1. Click "Save" and confirm that you're okay with the interpreter restarting.

## Notes On Python/PySpark
If you want to use PySpark in your experimentation, you will need to update the interpreter to use the same version of python that is on the Spark images (Python 3.4).  To make this happen, you will need to do the following:

1. From the Zeppelin UI, go to the interpreter settings at [http://localhost:8090/#/interpreter](http://localhost:8090/#/interpreter).
1. Search for, or scroll down to, the Spark interpreter.
1. Click the "Edit" button.
1. Update the value of the "zeppelin.pyspark.python" to be `python3`.
1. Click "Save" and confirm that you're okay with the interpreter restarting.

## Example Notebook

An example notebook has been provided in the `/examples` folder.  Simply import this notebook in to Zeppelin and run it/edit it at your liesure.