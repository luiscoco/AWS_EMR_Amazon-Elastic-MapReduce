# AWS_EMR (Amazon-Elastic-MapReduce)

## Youtube videos

AWS EMR Cluster Create using AWS Console | Submitting Spark Jobs in AWS EMR Cluster:
https://www.youtube.com/watch?v=XRGveXDutKM

AWS EMR Big Data Processing with Spark and Hadoop | Python, PySpark, Step by Step Instructions: 

https://www.youtube.com/watch?v=a_3Md9nV2Mk

How to process big data workloads with spark on AWS EMR: https://www.youtube.com/watch?v=6OEwdJbnDY8

https://github.com/Primus-Learning/emr-spark-job-to-process-data/tree/main


## ¿Qué es AWS EMR?

https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html

**EMR** es una plataforma gestionada en AWS que nos permite ejecutar trabajos **Big Data** con el ecosistema **Hadoop** como motor de procesamiento distribuido. 

Usa instancias de Amazon Elastic Compute Cloud (Amazon **EC2**) para ejecutar los clusters con los servicios open source que necesitemos, como por ejemplo Apache **Spark** o Apache **Hive**.

EMR tiene **HDFS** como capa de almacenamiento para el clúster. 

También, nos permite desacoplar el cómputo del almacenamiento usando el servicio **S3** para almacenar datos y logs sin límite.

Se puede elegir entre varias versiones que determinan el stack open source que se despliega en el clúster. 

Incluye **Hadoop**, **Hive**, **Tez**, **Flink**, **Hue**, **Spark**, **Oozie**, **Pig** y **HBase** entre otros.

El sistema también está integrado con otros servicios de AWS y nos proporciona notebooks para ejecutar código en el clúster. 

Se puede usar **Jupyter Lab** usando **Apache Livy**.

## Arquitectura de EMR

**EMR** tiene tres tipos de nodos:

**Master**: Los nodos Master deben estar en funcionamiento para dar servicio al clúster.

Se pueden desplegar varios para tener alta disponibilidad. 

Por defecto, alojan servicios como Hive Metastore.

**Core**: Estos nodos se encargan de almacenar los datos en HDFS y ejecutar los trabajos, también se pueden escalar.

**Task**: Estos nodos no almacenan datos por lo que se pueden añadir y eliminar sin riesgos de pérdida de datos. 

Se usan par añadir capacidad de procesamiento al clúster.

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/ec875d11-635f-4d4f-a0ef-a25d31626cb7)

Entre las opciones de despliegue que tiene EMR podemos elegir pago por uso, en función del tiempo o ahorrar en costes usando instancias reservadas, planes de ahorro o instancias spot de AWS.

## Escalado en Amazon EMR

En función de las cargas de trabajo que queramos ejecutar, podemos desplegar **clusters específicos** para la duración de nuestro trabajo o bien tener un **clúster permanente** con alta disponibilidad y auto escalable en función de la demanda. 

El primer caso está aconsejado para trabajos puntuales y más ligeros.

Los despliegues de EMR se pueden escalar de forma **automática** o de forma **manual** estableciendo límites de nodos core. 

Para escalar el clúster se usarán **métricas de utilización**, tomando en cuenta las réplicas de datos.

En el caso de trabajos de streaming con **Spark Streaming** deberemos analizar muy bien la capacidad del clúster para escalar con el volumen. 

Es posible que el clúster pueda añadir capacidad automáticamente pero cuando el volumen de trabajo vuelva a disminuir **no sea capaz de reducir el número de nodos**, aumentando los costes considerablemente.

## Almacenamiento en Amazon EMR

Debemos entender que EMR proporciona dos formas de almacenamiento:

**EMRFS**: Este sistema de ficheros se basa en el servicio **S3**. Tiene la capacidad de desacoplar el cómputo del clúster del almacenamiento.

**HDFS**: Necesita un **clúster dedicado**. Debemos configurar un factor de replicación para los nodos Core y tenerlo en cuenta para un correcto dimensionamiento.

**EMR** siempre necesita **HDFS**, por lo que al menos se necesitará un nodo de tipo Core.

Ambos modos son compatibles, y podemos persistir nuestros datos en el almacenamiento que necesitemos. 

También, podremos usar **s3DistCp** para copiarnos datos entre ellos.

En trabajos en los que no se realicen muchas operaciones de lectura, podremos usar EMRFS con S3 para optimizar los costes. 

En los trabajos con muchas lecturas iterativas (por ejemplo **Machine Learning**), nos beneficiaremos más de un sistema como **HDFS**.

