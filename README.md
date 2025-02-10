# Hadoop Multinode Cluster Setup and HDFS Operations

This project demonstrates how to set up a multi-node Hadoop cluster using Docker Compose and perform basic HDFS operations.

## 🚀 Features
- Multi-node Hadoop cluster setup using Docker Compose
- Downloading and storing a dataset in HDFS
- Copying files between HDFS directories
- Deleting directories while skipping trash
- Exploring files using NameNode Web UI

## 📁 Repository Structure
- `docker-compose.yaml` → Hadoop cluster setup file
- `setup.md` → Step-by-step guide for setting up the cluster
- `solutions.md` → Solutions to the given tasks

## 🔧 Prerequisites
- Docker & Docker Compose installed
- Basic knowledge of Hadoop and HDFS

## 🏗️ Setting up the Cluster
1. Clone the repository:
   ```bash
   git clone https://github.com/YOUR_GITHUB_USERNAME/hadoop-multinode-hdfs.git
   cd hadoop-multinode-hdfs
   ```

2. Start the Hadoop cluster:
   ```bash
   docker-compose up -d
   ```

3. Verify the cluster is running:
   ```bash
   docker ps
   ```

## 📌 Tasks and Solutions
Refer to the [solutions.md](solutions.md) file for the detailed commands and explanations.
