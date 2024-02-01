# A Spark Cluster in Docker

### Disclaimer

[x] **Yes, I understand this is stupid way to run a real spark cluster, and you should too.**

My guess is one of the best ways to not get hired as a big data engineer would be to go bragging on linkedin about running a spark cluster on your laptop.

You scale out when you can no longer scale up. Scaling out on single hardware is for toy / experimental / educational purposes only. 

KNOW THIS.

### What's in the box?

This repo will build a dockerized spark cluster.

- 3 worker nodes
- 1 master node
- 1 pyspark jupyter notebook running as the client
- 1 instance of Minio, because a spark cluster is useless without networked storage.

Consider this an exercise in learning / understanding the subtle differences between local spark and a clustered spark.

It's better than paying for it on Azure, AWS or GCP, I suppose.

### Running the cluster

1. install docker
2. clone this repo
3. from the terminal in this repo folder run `docker-compose up -d`
4. congratulations! you have a spark cluster and S3 compatible storage. 
5. when you have had enough, `docker-compose down`

### JupyterLab Spark client 

1. open a browser to http://localhost:8888 and use `sparkpw` as the jupyter token.
2. you are now in jupyterlab - a readily available spark client.
3. your spark cluster is `spark://master:7077`
4. the `work` folder has example pyspark scripts.
5. To view the jobs on the server go to http://localhost:8080 

### Your own spark client

If you want to double-down on the stupidity, you can connect to your cluster from your PC/Mac!

1. install spark 3.5 on your PC/Mac
2. connect to your spark cluster `spark://localhost:7077`

### Minio S3 Compatible storage

You'll need networked storage to do anything useful in your spark cluster.

1. open minio client http://localhost:9000
2. login as user `minio` with password `miniopw`
3. create a bucket for your files and then upload your files through the web ui

### Make it even more stupider

Edit the `docker-compose.yaml` and change the number of `replicas:` on line 32. Run a  50 node cluster from your laptop and impress your friends with your big-data prowess!!!


