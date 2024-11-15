# Docker Hadoop Yarn cluster for Spark 3.x

<p align="center">
  <img src="logo.jpg">
</p>

Provides a Docker multi-node Hadoop cluster with Spark 3.x on Yarn cluster.  Tested working on Ubuntu 24.04 arm64 VM (using UTM on Apple Silicon)

* [Usage](#usage)
  * [Build](#build)
  * [Run](#run)
  * [Stop](#stop)
  * [Connect to Master Node](#connect-to-master-node)
  * [Run spark applications on cluster :](#run-spark-applications-on-cluster-)
    * [spark-shell](#spark-shell)
    * [spark submit](#spark-submit)
    * [Web UI](#web-ui)

## Usage

### Build

```bash
make build
```

### Run

```bash
make start
```

### Stop

```bash
make stop
```

### Connect to Master Node

```bash
make connect
```

```bash
 ---- MASTER NODE ---- 
root@cluster-master:/#
```

### Run spark applications on cluster

Once connected to the master node

#### spark-shell

```bash
spark-shell --master yarn --deploy-mode client
```

#### spark submit

```bash
spark-submit --master yarn --deploy-mode cluster --class org.apache.spark.examples.SparkPi $SPARK_HOME/examples/jars/spark-examples_2.12-3.0.2.jar
```

#### Web UI

* Get master node ip:

```bash
make master-ip
```

```bash
 ---- MASTER NODE IP ---- 
Master node ip : 172.20.0.4
```

* Access to Hadoop cluster Web UI : `master-node-ip:8088`
* Access to spark Web UI : `master-node-ip:8080`
* Access to hdfs Web UI : `master-node-ip:50070`
