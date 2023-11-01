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

## 2. ¿What is AWS EMR?

https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html

**AWS EMR** is a platform managed on AWS that allows us to execute **Big Data** jobs with the **Hadoop** ecosystem as a **distributed processing engine**

Use Amazon Elastic Compute Cloud (Amazon **EC2**) instances to run the clusters with the open source services that we need, such as **Apache Spark** or **Apache Hive**

**EMR** has **HDFS** as the storage layer for the cluster

Also, it allows us to decouple computing from storage using the **S3** service to store data and logs without limit

You can choose between several versions that determine the open source stack that is deployed in the cluster

Includes Hadoop, Hive, Tez, Flink, Hue, Spark, Oozie, Pig and HBase among others

The system is also integrated with other AWS services and provides us with **notebooks** to run code on the cluster

**Jupyter Lab** can be used using **Apache Livy**

## 3. AWS EMR Architecture

**Master**: Master nodes must be up and running to service the cluster.

Several can be deployed to have high availability.

By default, they host services like Hive Metastore.

**Core**: These nodes are responsible for storing data in HDFS and executing jobs, they can also be scaled.

**Task**: These nodes do not store data so they can be added and deleted without risk of data loss.

They are used to add processing capacity to the cluster.

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/ec875d11-635f-4d4f-a0ef-a25d31626cb7)

Among the deployment options that EMR has, we can choose to pay per use, based on time or save on costs by using reserved instances, savings plans or AWS spot instances.

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

## 7. ¿Cómo crear un nuevo cluster AWS EMR?

### 7.1. Primero asignamos un nombre al AWS EMR Cluster

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/f51d1fa0-4e1c-445d-a1d0-909acbe00a1e)

### 7.2. Posteriormente elegimos una version del servicio AWS EMR

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/6dc07758-46b0-47e0-9448-3ad907670d67)

### 7.3. A continuación elegimos las aplicaciones de BigData que vamos a instalar en el cluster:

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/d0ab1396-0bc3-41f3-9d36-e122bc1b5724)

### 7.4. Respecto al sistema operativo elegimos Linux:

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/55b6a195-2e05-4ba7-9af9-6904fe582700)

### 7.5. Elegimos la opción "Grupos de instancias".

**Un tipo de instancia por grupo de nodos**

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/e24f5c04-a851-4211-8949-3fb026877d3c)

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/b69da727-a59f-41cf-a522-cab917bd6363)

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/984bb374-7620-4b37-a59a-2d3c586911b6)

### 7.6. Respecto al escalado del cluster, elegimos escalado del cluster manual:

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/cf882afe-6f36-4dc9-8c34-d6ee8f4b8449)

### 7.7. For your subnet to communicate with external sources

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

### 7.8. VPC y Subnet

Elegimos la VPC por defecto creada en nuestra cuenta de AWS. Respecto a la subnet, elegimos una de las tres subnets que integran la default VPC de nuestra cuenta.

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/6b278626-f4b0-4637-9b69-b1b225a88971)

Podemos consultar las VPC y las subnets disponibles

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/5c189763-7de2-4ff0-a78a-610522497ed1)

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/80f4910b-ee72-4e39-96c1-2f984bb5d039)

### 7.9. Elegimos el tipo de Terminación del AWS EMR

En nuestro caso elegimos el tipo de terminación del cluster "Manual"

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/96de6987-6e98-4c91-9a70-0f7fa7ca130a)

### 7.10. Elegimos las "Bootstrap actions" y el "Cluster Logs"

Dejamos los valores por defecto:

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/42c0214f-a8c2-4eac-9721-bc521cd2b4f1)

### 7.11. "Tags" y "Edit software settings"

Dejamos los valores por defecto: 

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/e0e57bd8-8dba-4ccd-a317-f02e785f3e96)

### 7.12. Security configuration and EC2 key pair 

Como paso previo tenemos que crear un Key-Pair y descargar su archivo en nuestro ordenador personal.

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/505e669d-fba6-4788-80bb-5f1a724f01b2)

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/91b15915-6517-43d6-a04f-a3aa9d74a997)

Después de pulsar el valor de **"Create key pair"**, automáticamente se decarga el archivo **ppk** en nuestro ordenador

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/6eb18812-7990-4235-a2bf-8c6e940e9d92)

Una vez que hemos creado el archivo **ppk** lo cargamos para configurar la opción de seguridad de nuestro AWS EMR cluster

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/3dacbb4d-a0c8-4e67-b167-32a57a4b723b)

### 7.13. IAM (Identity and Access Management)

Tenemos que crear el "Service Role" y el "Instance Profile" para las instancias EC2 de nuestro cluster.

#### 7.13.1. Primero: creamos el "Service Role"

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/ecbaeaeb-5c94-451d-a412-5a01a9e0abda)

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/b4edb5b5-d981-4463-8444-2d92ae6672ef)

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/76869987-7a38-41ba-aa49-ddffce7bc38f)

Le asignamos al nuevo role el nombre "EMR_DefaultRole", y pulsamos el botón crear:

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/97f9c876-c952-4a61-b44f-f6178783f810)

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/3f3201d6-3789-4518-b8c7-3a74cd92c984)

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/c674c8b2-2c1e-4ebc-955d-45c2d5618c26)

#### 7.13.2. Segundo: cremos el "Instance Profile"

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/10c81cff-cccf-467d-8cec-57ba962d3c1b)

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/e2ee9732-3ee3-49b7-9eef-6e0c387736b2)

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/ca4bc151-77be-4bdf-ab9f-5038bd7a7988)

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/edc4b802-83b7-4d61-a2ee-a58254003db9)

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/8c2b7c9b-35e5-4ec9-9498-a75c1b29bbf9)

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/53fcc013-00e4-4b17-ac24-0823a86dd44c)

#### 7.13.3. Identity and Access Management (IAM) roles 

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/64a3b6b9-0a97-4381-b072-89ac16637065)

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/c2a39772-04f8-4a41-8da5-6c9de3990a79)

### 7.14. Pulsamos el botón "Create cluster"

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/d95ff2c6-316e-44e5-ab00-82c9051b8225)

### 7.15. Editamos el Security Group del Master

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/d7a5953a-4df6-4ec0-9539-6f6d7bde4eca)

Pulsamos en el botón "Edit Inbound Rules" 

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/ecc96903-cc6e-4620-b99c-8942e9e8824c)

Añadimos una regla más para el protocolo SSH puerto 22 desde mi IP y pulsamos el botón "Save Rules"

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/82726647-979f-4daf-af86-8a1ec49b1114)

O acceso mediante protocolo SSH puerto 22 desde cualquier IP y pulsamos el botón "Save Rules"

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/dfcaf925-3b7e-4004-91ea-9bb993ac75fa)

### 7.16. Conectar al "Primary node" usando SSH

Tenemos dos opciones conexión en Windows

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/8fad7a5a-2906-4d61-a84d-5496a719ba9c)

O conexión mediante Mac o Linux

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/27fa7995-9832-404c-96c6-9ebc2d5e9109)

## 8. AWS EMR - Configuración de Putty para conexión con el Nodo Primario en Windows

Primero seleccionamos la opción **Session** e introducimos el nombre del servidor "hadoop@ec2-52-47-194-255.eu-west-3.compute.amazonaws.com" el protocolo de conexión SSH y el puerto 22

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/ef8cfc82-7372-40cf-a6f9-b4b385c058c9)

Posteriormente elegimos la opción **SSH->Auth->Credentials** y subimos el archivo **ppk** que generamos cuando creamos el Key-Pair en AWS.

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/8ae93a5d-079b-47fa-a41b-4aad9e2f90e7)

Damos un nombre a la Session y pulsamos el botón **Save** para guardar los datos de la Session

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/39981c6f-c709-4739-9940-c14d3bca09c4)

Como último paso pulsamos el botón **open** para conectarnos con el Primary Node del AWS EMR cluster

La primera vez que nos conectamos nos aparece este mensaje. Pulsamos en el botón **Aceptar**

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/64ee5d09-c9ef-48f9-861d-d045878606f4)

Posteriormente ya nos aparece la siguiente pantalla. Vemos que hemos accedido con el usuario **hadoop** y con la autenticación mediante el **Key-Pair**

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/d71c93c0-7fc7-41e4-a5e5-dc2336fdae33)

Podemos ejecutar el comando "sudo yum update" para actualizar a su última version los paquetes instalados. 

```
sudo yum update
```

This command is used on Linux systems, specifically those using the yum package manager. Let's break it down:

**sudo:** This stands for "superuser do" and is used to execute commands with elevated privileges. It's often required for system-level operations.

**yum:** This is the package manager used by Red Hat-based Linux distributions, such as Fedora and CentOS. It's used for installing, updating, and removing packages on the system.

**update:** This is the specific command you're giving to yum. When you run sudo yum update, you're telling yum to update all installed packages to their latest versions. It checks the repositories configured on your system for newer versions of packages and installs them.

So, in summary, sudo yum update is a command to update all the software packages on your system to the latest available versions.

It's a good practice to run this command periodically to ensure that your system is up to date with the latest security patches and feature updates.

## 9. Probamos comandos Scala y Spark dentro de nuestro AWS EMR

Primero consultamos cuál es la versión del comando "spark-submit" 

Para ello ejecutamos el comando:

```
spark-submit --version
```

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/4a53164a-252c-4135-a14e-3c74ce4690c8)

Posteriormente podemos ejecutar el comando spark-shell.

```
spark-shell
```

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/ff22cdf4-b807-4da1-93d2-fcf74375c841)

## 10. Create AWS EMR Cluster Using AWS CLI and Submit job

**NOTA IMPORTANTE!** see the ZIP file in this Github repo with a real example

Youtube video: https://www.youtube.com/watch?v=XsWnW7-8IGQ

These are the steps to follow in order to **create and run an AWS EMR cluster uring AWS CLI**:

- In AWS create **IAM user**

- Create  **Access Key ID and Access Key** for using later during AWS CLI configuration.

- Install and configure **AWS CLI**

  Type the command:

  ```
  aws configure
  ```

  Enter AWS Access Key ID and access key

  And Region : eu-west-3

  After configuring AWS CLI you can test it running the commands:

  List all IAM user 

  ```
  aws iam list-users
  ```
  
  List all buckets in s3

  ```
  aws s3 ls
  ```
 
- Create a **Key-Pair** in AWS EC2. See section 7.2.

- Create a AWS **S3 bucket** "myemrproject" and inside several folders: "input", "logs", "scripts"

  ![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/3762f007-8403-4b88-a3fb-3da021db134f)

  Upload to the "input" folder the input data "product_data.csv"

  Upload to the "scripts" folder the application source code "mypysparkscript_1.py"

- Create an **AWS EMR cluster** (previously create the AIM roles: EMR_DefaultRole and EMR_EC2_DefaultRole)

- Add steps to execute specific job or task by using AWS CLI

- Check out

- Submit Spark job or task directly to a Spark cluster(Primary node)

This is the application source code:

```python
from pyspark.sql import SparkSession

if __name__ == "__main__":
    # Initialize SparkSession
    spark = SparkSession.builder.appName("MyPySparkJob").getOrCreate()
     
    try:
        # Your PySpark code here
        # Specify the input file path
        input_file = 's3://myemrproject/input/product_data.csv'
        df = spark.read.csv(input_file)
        df.show()
        df.write.option("header", "true").mode("overwrite").parquet("s3://myemrproject/output")
        
        # Stop SparkSession
        spark.stop()

    except Exception as e:
        # Handle any exceptions or errors
        print("Error occurred: ", str(e))
        spark.stop()
```
