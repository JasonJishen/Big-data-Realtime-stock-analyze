# Docker environment setup

## code structure

1. local-setup.sh fast deploy single node Kakfa, Cassandra, Zookeeper environment

## MacOS, *nix

create a docker-machine virtual machine, 2CPU, 2G memorty
```sh
docker-machine create --driver virtualbox --virtualbox-cpu-count 2 --virtualbox-memory 2048 bigdata
```
run script to run all the related docker container (Kafka, Cassandra, Zookeeper, Redis)
```sh
./local-setup.sh bigdata
```

## Windows

create a docker-machine virtual machine, 2CPU, 2G memorty
```sh
docker-machine create --driver virtualbox --virtualbox-cpu-count 2 --virtualbox-memory 2048 bigdata
```

Start Zookeeper Server
```sh
docker run -d -p 2181:2181 -p 2888:2888 -p 3888:3888 --name zookeeper confluent/zookeeper 
```

Start Kafka Server
```sh
docker run -d -p 9092:9092 -e KAFKA_ADVERTISED_HOST_NAME=192.168.99.100:9092 -e KAFKA_ADVERTISED_PORT=9092 --name kafka --link zookeeper:zookeeper confluent/kafka 
```

Start Cassandra Server
```sh
docker run -d -p 7199:7199 -p 9042:9042 -p 9160:9160 -p 7001:7001 --name cassandra cassandra:3.7
```

Start Redis Server
```sh
docker run -d -p 6379:6379 --name redis redis:alpine
```
