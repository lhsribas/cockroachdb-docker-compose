# Run CockroachDB with Docker

## Introduction

CockroachDB is an open-source, distributed SQL database developed by former Google engineers at Cockroach Labs. Designed to run in the cloud, and is known for this resilience and scalability.

The CockroachDB can run in a single machine or can be scaled to hundreds and thousands of servers. Because of this, CockroachDB is the best option for the cloud. It grows as the organizations need to succeed.

Some aspects of CockroachDB were inspired by Spanner – Google’s globally-distributed database offering.

[Access CockroachDB for more informations!](https://www.cockroachlabs.com/docs/stable/architecture/overview.html)

### Compatibility

Designed to be highly compatible with PostgreSQL, this is an important point and nos just because it means that the users do not have to learn as many new things only to work with CockroachDB. 

Note, this means many apps that were designed to work with PostgreSQL can be migrated to work with CockroachDB with no changes necessary. It also means that you can use a wide variety of existing PostgreSQL client drivers to talk to CockroachDB. It’s been tested from diverse languages, including:

* Python
* Ruby
* Java
* Go
* PHP
* Node.js
* C and C++
* Rust
* Clojure

### When to choose CockroachDB

While there’s no doubt that CockroachDB is a smart choice for a wide variety of applications, there are certain use cases that the product is especially well-suited for, such as:

* Multi-datacenter deployments
* Cloud migrations
* Replicated or distributed online transaction processing

When you need response times in the milliseconds regardless of scale, combined with available, reliable data, CockroachDB is a viable solution. However, the product isn’t the best choice for heavy analytics.

## Starts CockroachDB With Docker Compose
<br/>

Now we runs the CockroachDB with Docker Compose in your local machine, you can clone the git url below.

<br/>

### Gets the git repository.

<br/>

```bash
$ git clone https://github.com/lhsribas/cockroachdb-docker-compose.git
```

### Docker bridge network for the CockroachDB nodes
<br/>

The command **docker network create** creates a specific network to run the CockroachDB.

<br/>

```bash
$ docker network create -d bridge network_cockroachdb
```

### Spin up CockroachDB containers with Docker Compose
<br/>

The command bellow start the cluster with two nodes, and the flag **--build** Build images before starting containers.

<br/>

```
$ docker-compose up --build
```

### Docker Compose with the CockroachDB cluster
<br/>

Since the containers are running in the foreground, you’ll need to open another tab or terminal window and use the following command to list the nodes’ containers:

<br/>

```
$ docker ps
```

### Troubleshooting a CockroachDB cluster in Docker
<br/>

If you encounter a port conflict, you can try to stop and remove the containers for the nodes using docker stop and docker rm. You can also use lsof to look for the processes using the 26257 Cockroach port as seen below:

<br/>

```
$ lsof -i -sTCP:LISTEN | grep 26257
```

### Initialize and interact with the CockroachDB cluster
<br/>

You can use the following command to initialize your cluster if needed:

<br/>

```
$ docker exec -it node_1 ./cockroach init --insecure
```

### Access the CockroachDB interactive shell
<br/>

We’ll use the docker exec command to connect and interact with the node_1 container by taking advantage of the -it interactive options:

<br/>

```
$ docker exec -it node_1 /bin/bash
```

### CockroachDB SQL interactive shell
<br/>

Once you’re inside the container, use the ./cockroach sql command to enter the SQL interactive shell for the CockroachDB node:

<br/>

```
$ ./cockroach sql --insecure
```

```
$ CREATE DATABASE some_db;
```
