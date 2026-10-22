# Create A Data Pipeline based on Messaging Using PySpark Hive

Create A Data Pipeline based on Messaging Using PySpark Hive — AWS Data Engineering project.

## Overview
The purpose is to collect the real time streaming data from COVID19 open API for every 5 minutes into the ecosystem using NiFi and to process it and store it in the data lake on AWS.Data processing includes parsing the data from complex JSON format to csv format then publishing to Kafka for persistent delivery of messages into PySpark for further processing.The processed data is then fed into output Kafka topic which is inturn consumed by Nifi and stored in HDFS .A Hive external table is created on top of HDFS processed data for which the process is Orchestrated using Airflow to run for every time interval. Finally KPIs are visualised in tableau.

Project execution guidelines

- As soon as we login into the EC2 instance , we need to start the following jps services using the commands .
- Note that everytime we stop and start the instance these services need to be restarted if they are not running as Daemon processes.

## Tech stack
1.   Nifi -nifi-1.10.0
2.   Hadoop -hadoop_2.7.3
3.   Hive-apache-hive-2.1.0
4.   Spark-spark-2.4.5
5.   Zookeeper-zookeeper-2.3.5
6.   Kafka-kafka_2.11-2.4.0
7.   Airflow-airflow-1.8.1
8.   Tableau-

Known errors and resolutions
- Everytime consume kafka processor is run, the group id attribute needs to be changed and can be given some random text value
- When we see the below error while starting Hive :

Caused by: java.net.URISyntaxException: Relative path in absolute URI: ${system:java.io.tmpdir%7D/$%7Bsystem:user.name%7D

## How to run

## Project structure
```
.gitignore
Config with Docker/
  bat_files/
    copy.bat
    copy_bat/
    ec2connect.bat
    portforwarding.bat
    replace_ip.bat
  docker_exp/
    airflow_init.sh
    docker-compose.yml
    hive_connection.py
    hive_script.py
    test.py
README.md
hive_script_airflow.py
pyspark_job_to_write_data_to_kafkatopic.py
```

## Credits
Based on a ProjectPro guided project.
