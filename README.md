# AWS EMR (Amazon-Elastic-MapReduce)

## 1. Youtube videos

AWS EMR Cluster Create using AWS Console | Submitting Spark Jobs in AWS EMR Cluster:

https://www.youtube.com/watch?v=XRGveXDutKM

AWS EMR Big Data Processing with Spark and Hadoop | Python, PySpark, Step by Step Instructions: 

https://www.youtube.com/watch?v=a_3Md9nV2Mk

How to process big data workloads with spark on AWS EMR: 

https://www.youtube.com/watch?v=6OEwdJbnDY8

https://github.com/Primus-Learning/emr-spark-job-to-process-data/tree/main

Running an Amazon EMR Cluster in the AWS Academy Data Engineering Sandbox:

https://www.youtube.com/watch?v=radrkdkUI0U

AWS EMR videos by Dr. Sian Lun:
https://www.youtube.com/@sianlun/videos

## 2. ¿Qué es AWS EMR?

https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html

**EMR** es una plataforma gestionada en AWS que nos permite ejecutar trabajos **Big Data** con el ecosistema **Hadoop** como motor de procesamiento distribuido. 

Usa instancias de Amazon Elastic Compute Cloud (Amazon **EC2**) para ejecutar los clusters con los servicios open source que necesitemos, como por ejemplo Apache **Spark** o Apache **Hive**.

EMR tiene **HDFS** como capa de almacenamiento para el clúster. 

También, nos permite desacoplar el cómputo del almacenamiento usando el servicio **S3** para almacenar datos y logs sin límite.

Se puede elegir entre varias versiones que determinan el stack open source que se despliega en el clúster. 

Incluye **Hadoop**, **Hive**, **Tez**, **Flink**, **Hue**, **Spark**, **Oozie**, **Pig** y **HBase** entre otros.

El sistema también está integrado con otros servicios de AWS y nos proporciona notebooks para ejecutar código en el clúster. 

Se puede usar **Jupyter Lab** usando **Apache Livy**.

## 3. Arquitectura de EMR

**EMR** tiene tres tipos de nodos:

**Master**: Los nodos Master deben estar en funcionamiento para dar servicio al clúster.

Se pueden desplegar varios para tener alta disponibilidad. 

Por defecto, alojan servicios como Hive Metastore.

**Core**: Estos nodos se encargan de almacenar los datos en HDFS y ejecutar los trabajos, también se pueden escalar.

**Task**: Estos nodos no almacenan datos por lo que se pueden añadir y eliminar sin riesgos de pérdida de datos. 

Se usan par añadir capacidad de procesamiento al clúster.

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/ec875d11-635f-4d4f-a0ef-a25d31626cb7)

Entre las opciones de despliegue que tiene EMR podemos elegir pago por uso, en función del tiempo o ahorrar en costes usando instancias reservadas, planes de ahorro o instancias spot de AWS.

## 4. Escalado en Amazon EMR

En función de las cargas de trabajo que queramos ejecutar, podemos desplegar **clusters específicos** para la duración de nuestro trabajo o bien tener un **clúster permanente** con alta disponibilidad y auto escalable en función de la demanda. 

El primer caso está aconsejado para trabajos puntuales y más ligeros.

Los despliegues de EMR se pueden escalar de forma **automática** o de forma **manual** estableciendo límites de nodos core. 

Para escalar el clúster se usarán **métricas de utilización**, tomando en cuenta las réplicas de datos.

En el caso de trabajos de streaming con **Spark Streaming** deberemos analizar muy bien la capacidad del clúster para escalar con el volumen. 

Es posible que el clúster pueda añadir capacidad automáticamente pero cuando el volumen de trabajo vuelva a disminuir **no sea capaz de reducir el número de nodos**, aumentando los costes considerablemente.

## 5. Almacenamiento en Amazon EMR

Debemos entender que EMR proporciona dos formas de almacenamiento:

**EMRFS**: Este sistema de ficheros se basa en el servicio **S3**. Tiene la capacidad de desacoplar el cómputo del clúster del almacenamiento.

**HDFS**: Necesita un **clúster dedicado**. Debemos configurar un factor de replicación para los nodos Core y tenerlo en cuenta para un correcto dimensionamiento.

**EMR** siempre necesita **HDFS**, por lo que al menos se necesitará un nodo de tipo Core.

Ambos modos son compatibles, y podemos persistir nuestros datos en el almacenamiento que necesitemos. 

También, podremos usar **s3DistCp** para copiarnos datos entre ellos.

En trabajos en los que no se realicen muchas operaciones de lectura, podremos usar EMRFS con S3 para optimizar los costes. 

En los trabajos con muchas lecturas iterativas (por ejemplo **Machine Learning**), nos beneficiaremos más de un sistema como **HDFS**.

## 6. Aplicationes que se pueden incluir en AWS EMR 

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/16aa1cc5-4199-4401-a7ac-190b2dda86ed)

Let me break down some of the main capabilities of each:

**Flink 1.17.1**: Apache Flink is a stream processing framework for big data processing and analytics. It supports both batch and stream processing with low-latency and high-throughput.

**Ganglia 3.7.2**: Ganglia is a scalable and distributed monitoring system for high-performance computing systems. It is often used to monitor clusters and grids.

**HBase 2.4.17**: Apache HBase is a distributed, scalable, and NoSQL database built on top of Hadoop. It provides real-time read and write access to large datasets.

**HCatalog 3.1.3**: HCatalog is a table and storage management service for Hadoop that enables users to share and access data across Pig, Hive, and MapReduce.

**Hadoop 3.3.3**: Apache Hadoop is an open-source framework for distributed storage and processing of large data sets using a cluster of commodity hardware.

**Hive 3.1.3**: Apache Hive is a data warehousing and SQL-like query language for large datasets stored in Hadoop distributed file systems.

**Hue 4.11.0**: Hue is a web-based interface for analyzing data with Hadoop. It provides a user-friendly interface for various Hadoop ecosystem components.

**JupyterEnterpriseGateway 2.6.0 and JupyterHub 1.5.0**: JupyterHub is a multi-user server for Jupyter notebooks, and Enterprise Gateway enables Jupyter notebooks to interact with big data clusters.

**Livy 0.7.1**: Apache Livy is a REST service for interacting with Spark from anywhere. It allows remote applications to submit Spark jobs, query status, and retrieve results.

**MXNet 1.9.1 and TensorFlow 2.11.0**: These are deep learning frameworks. MXNet and TensorFlow are used for developing and training machine learning models.

**Oozie 5.2.1**: Apache Oozie is a workflow scheduler for Hadoop jobs. It allows users to define, manage, and schedule data workflows.

**Phoenix 5.1.3**: Apache Phoenix is a SQL skin over HBase, providing a relational database layer for HBase.

**Pig 0.17.0**: Apache Pig is a high-level scripting language for analyzing large datasets on Hadoop. It simplifies the development of complex data processing tasks.

**Presto 0.281 and Trino 422**: Presto (now known as Trino) is a distributed SQL query engine optimized for ad-hoc analysis. It allows querying data where it resides.

**Spark 3.4.1**: Apache Spark is a fast and general-purpose cluster computing system for big data processing. It supports in-memory processing and various data processing tasks.

**Sqoop 1.4.7***: Apache Sqoop is a tool for efficiently transferring bulk data between Hadoop and structured datastores such as relational databases.

**Tez 0.10.2**: Apache Tez is an extensible framework for building high-performance batch and interactive data processing applications.

**Zeppelin 0.10.1**: Apache Zeppelin is a web-based notebook that enables interactive data analytics with a variety of interpreters, including for Spark, Hive, and more.

**ZooKeeper 3.5.10**: Apache ZooKeeper is a distributed coordination service used for maintaining configuration information, naming, providing distributed synchronization, and group services.

These tools collectively form a powerful ecosystem for big data processing, analytics, and machine learning. 

They enable various tasks such as data storage, processing, monitoring, and analysis in large-scale distributed systems.

## 7. Amazon EMR - Configuring Putty

VERY IMPORTANT! youtube video: https://www.youtube.com/watch?v=JzENuQhelUM

## 8. ¿Cómo crear un nuevo cluster AWS EMR?

### 8.1. Primero asignamos un nombre al AWS EMR Cluster

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/f51d1fa0-4e1c-445d-a1d0-909acbe00a1e)

### 8.2. Posteriormente elegimos una version del servicio AWS EMR

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/6dc07758-46b0-47e0-9448-3ad907670d67)

### 8.3. A continuación elegimos las aplicaciones de BigData que vamos a instalar en el cluster:

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/d0ab1396-0bc3-41f3-9d36-e122bc1b5724)

### 8.4. Respecto al sistema operativo elegimos Linux:

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/55b6a195-2e05-4ba7-9af9-6904fe582700)

### 8.5. Elegimos la opción "Grupos de instancias".

**Un tipo de instancia por grupo de nodos**

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/e24f5c04-a851-4211-8949-3fb026877d3c)

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/b69da727-a59f-41cf-a522-cab917bd6363)

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/984bb374-7620-4b37-a59a-2d3c586911b6)

### 8.6. Respecto al escalado del cluster, elegimos escalado del cluster manual:

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/cf882afe-6f36-4dc9-8c34-d6ee8f4b8449)

### 8.8. VPC y Subnet

Elegimos la VPC por defecto creada en nuestra cuenta de AWS. Respecto a la subnet, elegimos una de las tres subnets que integran la default VPC de nuestra cuenta.

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/6b278626-f4b0-4637-9b69-b1b225a88971)

Podemos consultar las VPC y las subnets disponibles

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/5c189763-7de2-4ff0-a78a-610522497ed1)

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/80f4910b-ee72-4e39-96c1-2f984bb5d039)

### 8.7. For your subnet to communicate with external sources

As previous stFor your subnet to communicate with external sources:

a) you need to add a default route (0.0.0.0/0) pointing to either an Internet Gateway (if it's a public subnet)

b) or a NAT Gateway (if it's a private subnet).

Here's what you can do:

**a) Internet Gateway (for public subnet):**

- Go to the AWS VPC Console.

- Navigate to the "Internet Gateways" section.

- Create an Internet Gateway if you haven't already.

- Attach the Internet Gateway to your VPC.

- Go back to the route table (rtb-04c42678a04496623) for subnet-0c773b8ac5250a86a and add a route:

- Destination: 0.0.0.0/0

- Target: The Internet Gateway you just attached.

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/36540288-6c17-4223-8504-3671bffc406d)

**b) NAT Gateway (for private subnet):**

Go to the AWS VPC Console.

Navigate to the "NAT Gateways" section.

Create a NAT Gateway if you haven't already.

Make sure the NAT Gateway is in a public subnet.

Go back to the route table (rtb-04c42678a04496623) for subnet-0c773b8ac5250a86a and add a route:

Destination: 0.0.0.0/0

Target: The NAT Gateway you just created.

After making these changes, your subnet should have a route to external sources,




IAM 

EMR_DefaultRole

EMR_EC2_DefaultRole->AmazonEMRFullAccessPolicy_v2
