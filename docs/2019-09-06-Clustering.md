# Clustering Elasticsearch Nodes

> 1 MASTER, TWO DATA NODES \
> FOR DEMO ONLY. NOT RECOMMENDED FOR PRODUCTION

I was able to create a three node elastic search cluster with a single master node (es-master-01) and two data nodes (es-data-01 and es-data-02)

The MOST IMPORTANT item to remember in this experiment is `discovery.zen.ping.unicast.hosts` which lists the hosts to ping. If the nodes cannot communicate with each other they turn themselves as a master node

Another IMPORTANT but easy configuration is `cluster.name`. This needs to be same for the nodes to join the same cluster.
## es-master-01

```
...
node.master: true
node.data: false
node.name: es-master-01
cluster.name : es-cluster-01
discovery.zen.ping.unicast.hosts:
 - es-master-01
 - es-data-01
 - es-data-02
 ...
```

## es-data-01/02

```
...
node.master: false
node.data: true
node.name: es-data-01/02
cluster.name : es-cluster-01
discovery.zen.ping.unicast.hosts:
 - es-master-01
 - es-data-01
 - es-data-02
 ...
```