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

## 4. Scaling AWS EMR

Depending on the workloads we want to run, we can deploy **specific clusters** for the duration of our work or have a **permanent cluster** with high availability and auto-scaling based on demand.

The first case is recommended for specific and lighter jobs.

EMR deployments can be scaled **automatically** or **manually** by setting core node limits.

To scale the cluster, **utilization metrics** will be used, taking data replicas into account.

In the case of streaming jobs with **Spark Streaming** we must carefully analyze the cluster's ability to scale with the volume.

It is possible that the cluster can add capacity automatically but when the volume of work decreases again **it will not be able to reduce the number of nodes**, increasing costs considerably.

## 5. Storing in AWS EMR

We must understand that EMR provides two forms of storage:

**EMRFS**: This file system is based on the **S3** service. It has the ability to decouple cluster computing from storage.

**HDFS**: Requires a **dedicated cluster**. We must configure a replication factor for the Core nodes and take it into account for correct sizing.

**EMR** always needs **HDFS**, so at least one Core type node will be needed.

Both modes are supported, and we can persist our data to whatever storage we need.

Also, we can use **s3DistCp** to copy data between them.

In jobs where many read operations are not performed, we can use EMRFS with S3 to optimize costs.

In jobs with a lot of iterative reads (for example **Machine Learning**), we will benefit more from a system like **HDFS**.

## 6. AWS EMR Big Data Applications 

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

## 7. ¿How to create a new AWS EMR Cluster?

### 7.1. First we set the AWS EMR Cluster name

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/f51d1fa0-4e1c-445d-a1d0-909acbe00a1e)

### 7.2. We select the AWS EMR version

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/6dc07758-46b0-47e0-9448-3ad907670d67)

### 7.3. We select the applications to be installed in the AWS EMR cluster

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/d0ab1396-0bc3-41f3-9d36-e122bc1b5724)

### 7.4. We select the operating systems for the EC2 integrating the cluster

We leave the default option, to install Linux as operating system

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/55b6a195-2e05-4ba7-9af9-6904fe582700)

### 7.5. We select the EC2 instances types 

We select the option **One instance type per Nodes Group**

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/e24f5c04-a851-4211-8949-3fb026877d3c)

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/b69da727-a59f-41cf-a522-cab917bd6363)

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/984bb374-7620-4b37-a59a-2d3c586911b6)

### 7.6. Scaling the cluster

We select the option Manual Scaling

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

### 7.8. VPC and Subnet

We select the Default VPC in our AWS account. 

Regarding the Subnet, we select one of the subnets in the Default VPC.

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/6b278626-f4b0-4637-9b69-b1b225a88971)

You can see the available VPC and Subnets

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/5c189763-7de2-4ff0-a78a-610522497ed1)

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/80f4910b-ee72-4e39-96c1-2f984bb5d039)

### 7.9. AWS EMR Termination

We select Manual Termination

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/96de6987-6e98-4c91-9a70-0f7fa7ca130a)

### 7.10. "Bootstrap actions" and "Cluster Logs"

We leave the default values

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/42c0214f-a8c2-4eac-9721-bc521cd2b4f1)

### 7.11. "Tags" y "Edit software settings"

We leave the default values

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/e0e57bd8-8dba-4ccd-a317-f02e785f3e96)

### 7.12. Security configuration and EC2 key pair 

As previous step we have to create a **Key-Pair** and download the **ppk** file in our hard disk

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/505e669d-fba6-4788-80bb-5f1a724f01b2)

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/91b15915-6517-43d6-a04f-a3aa9d74a997)

After we press the **"Create key pair"** button, and automativally the **ppk** file is downloaded in our computer

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/6eb18812-7990-4235-a2bf-8c6e940e9d92)

Once we created the **ppk** file we load it for configuring the security option in the AWS EMR cluster

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/3dacbb4d-a0c8-4e67-b167-32a57a4b723b)

### 7.13. IAM (Identity and Access Management)

We create the "Service Role" and the "Instance Profile" for EC2 instances

#### 7.13.1. Creating the "Service Role"

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/ecbaeaeb-5c94-451d-a412-5a01a9e0abda)

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/b4edb5b5-d981-4463-8444-2d92ae6672ef)

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/76869987-7a38-41ba-aa49-ddffce7bc38f)

Le asignamos al nuevo role el nombre "EMR_DefaultRole", y pulsamos el botón crear:

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/97f9c876-c952-4a61-b44f-f6178783f810)

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/3f3201d6-3789-4518-b8c7-3a74cd92c984)

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/c674c8b2-2c1e-4ebc-955d-45c2d5618c26)

#### 7.13.2. Creating the "Instance Profile"

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/10c81cff-cccf-467d-8cec-57ba962d3c1b)

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/e2ee9732-3ee3-49b7-9eef-6e0c387736b2)

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/ca4bc151-77be-4bdf-ab9f-5038bd7a7988)

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/edc4b802-83b7-4d61-a2ee-a58254003db9)

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/8c2b7c9b-35e5-4ec9-9498-a75c1b29bbf9)

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/53fcc013-00e4-4b17-ac24-0823a86dd44c)

#### 7.13.3. Identity and Access Management (IAM) roles 

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/64a3b6b9-0a97-4381-b072-89ac16637065)

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/c2a39772-04f8-4a41-8da5-6c9de3990a79)

### 7.14. Push the "Create cluster" buttton

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/d95ff2c6-316e-44e5-ab00-82c9051b8225)

### 7.15. Edit the Security Group in the Master node

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/d7a5953a-4df6-4ec0-9539-6f6d7bde4eca)

Press the button "Edit Inbound Rules" 

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/ecc96903-cc6e-4620-b99c-8942e9e8824c)

Add another rule in the **SSH** protocol and **port 22** to access from **My IP** and press the **Save Rules** button

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/82726647-979f-4daf-af86-8a1ec49b1114)

Or access with **SSH** protocol and **port 22** from **every IP address** and the press the **Save Rules** button

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/dfcaf925-3b7e-4004-91ea-9bb993ac75fa)

### 7.16. Connect to the "Primary node" using SSH

Tenemos dos opciones conexión en Windows

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/8fad7a5a-2906-4d61-a84d-5496a719ba9c)

Or connect with Mac or Linux

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/27fa7995-9832-404c-96c6-9ebc2d5e9109)

## 8. AWS EMR - Configuración de Putty para conexión con el Nodo Primario en Windows

First we select the **Session** and we set the Host name "hadoop@ec2-52-47-194-255.eu-west-3.compute.amazonaws.com", the protocol SSH and the port 22

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/ef8cfc82-7372-40cf-a6f9-b4b385c058c9)

We select the menu option **SSH->Auth->Credentials** and we upload the **ppk** file, previously generated when creating the Key-Pair in EC2 AWS

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/8ae93a5d-079b-47fa-a41b-4aad9e2f90e7)

We set the Session name and press the **Save** button

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

**sudo:** This stands for "superuser do" and is used to execute commands with elevated privileges. 

It's often required for system-level operations.

**yum:** This is the package manager used by Red Hat-based Linux distributions, such as Fedora and CentOS. 

It's used for installing, updating, and removing packages on the system.

**update:** This is the specific command you're giving to yum. When you run sudo yum update, you're telling yum to update all installed packages to their latest versions. 

It checks the repositories configured on your system for newer versions of packages and installs them.

So, in summary, sudo yum update is a command to update all the software packages on your system to the latest available versions.

It's a good practice to run this command periodically to ensure that your system is up to date with the latest security patches and feature updates.

## 9. Run the Scala and Spark commands in AWS EMR cluster

First we see the "spark-submit" command version 

```
spark-submit --version
```

![image](https://github.com/luiscoco/AWS_EMR_Amazon-Elastic-MapReduce/assets/32194879/4a53164a-252c-4135-a14e-3c74ce4690c8)

Then we run the command "spark-shell" command

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
