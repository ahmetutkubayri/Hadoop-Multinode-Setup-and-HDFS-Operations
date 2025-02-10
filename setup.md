# Hadoop Multi-node Setup Guide

This document provides a step-by-step guide to setting up a Hadoop cluster using Docker Compose.

## Step 1: Install Docker and Docker Compose
Ensure you have **Docker** and **Docker Compose** installed on your machine.

- Verify installation:
  ```bash
  docker --version
  docker-compose --version
  ```

## Step 2: Start the Cluster
1. Create and navigate to your project directory:
   ```bash
   mkdir hadoop-multinode-hdfs && cd hadoop-multinode-hdfs
   ```

2. Create a `docker-compose.yaml` file and paste the following content:
   ```yaml
   version: '3'
   services:
     namenode:
       image: bde2020/hadoop-namenode:2.0.0-hadoop3.2.1-java8
       container_name: namenode
       ports:
         - "9870:9870"
         - "9000:9000"
       environment:
         - CLUSTER_NAME=test
         - CORE_CONF_hadoop_http_staticuser_user=root
         - CORE_CONF_fs_defaultFS=hdfs://namenode:9000
         - HDFS_CONF_dfs_replication=1
       volumes:
         - namenode:/hadoop/dfs/name
       networks:
         - hadoop
     
     datanode:
       image: bde2020/hadoop-datanode:2.0.0-hadoop3.2.1-java8
       container_name: datanode
       ports:
         - "9864:9864"
       environment:
         - CORE_CONF_hadoop_http_staticuser_user=root
         - CORE_CONF_fs_defaultFS=hdfs://namenode:9000
         - HDFS_CONF_dfs_replication=1
       volumes:
         - datanode:/hadoop/dfs/data
       networks:
         - hadoop

   volumes:
     namenode:
     datanode:

   networks:
     hadoop:
   ```

3. Start the cluster:
   ```bash
   docker-compose up -d
   ```

4. Check the running containers:
   ```bash
   docker ps
   ```

## Step 3: Access the NameNode Web UI
- Open `http://127.0.0.1:9870` in your browser.
