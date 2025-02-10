# Solutions to Hadoop Multi-node HDFS Tasks

This file contains solutions to the given Hadoop and HDFS-related tasks.

## Q-1: Setup Multinode Hadoop Cluster and Add `Wine.csv` to HDFS
- Start the Hadoop cluster:
  ```bash
  docker-compose up -d
  ```
- Download and add the dataset to HDFS:
  ```bash
  docker exec -it namenode bash
  curl -O https://raw.githubusercontent.com/erkansirin78/datasets/master/Wine.csv
  hdfs dfs -mkdir -p /user/root/hdfs_odev
  hdfs dfs -put Wine.csv /user/root/hdfs_odev
  ```

## Q-2: Copy the HDFS File to Another Directory
```bash
hdfs dfs -mkdir -p /tmp/hdfs_odev
hdfs dfs -cp /user/root/hdfs_odev/Wine.csv /tmp/hdfs_odev
```

## Q-3: Delete the `/tmp/hdfs_odev` Directory (Skip Trash)
```bash
hdfs dfs -rm -r -skipTrash /tmp/hdfs_odev
```

## Q-4: Explore the File from NameNode Web UI
- Open `http://127.0.0.1:9870` in your browser and navigate to **Utilities → Browse the file system**.
