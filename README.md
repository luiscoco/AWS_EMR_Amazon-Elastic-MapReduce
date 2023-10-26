# AWS_EMR (Amazon-Elastic-MapReduce)

https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html

## ¿Qué es Amazon EMR?

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

