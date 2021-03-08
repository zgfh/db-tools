kafka

https://kafka.apache.org/quickstart
https://kafka.apache.org/documentation/#quickstart_createtopic


1. 先构建java
```
cd ../java
docker build -t java:8 .
```
2. 安装
```
#清理
docker-compose down -v

# 把192.168.1.7替换为你的机器ip
export HOSTIP=192.168.1.7 ;docker-compose up -d
```


3. 使用
```
先进入容器
docker-compose exec  kafka bash

# create topic: https://kafka.apache.org/documentation/#quickstart_createtopic
创建名为quickstart-events的topic:
bin/kafka-topics.sh --create --topic quickstart-events --bootstrap-server localhost:9092

# 创建 event:  
bin/kafka-console-producer.sh --topic quickstart-events --bootstrap-server localhost:9092

# 读取 event: 
bin/kafka-console-consumer.sh --topic quickstart-events --from-beginning --bootstrap-server localhost:9092

```

也可以用(以主机ip是192.168.1.7为例)
```
KAFKA_IP="192.168.1.7"
docker run -it kafka_kafka --create --topic test --bootstrap-server $KAFKA_IP:9092
docker run -it kafka_kafka bin/kafka-console-producer.sh --topic test --bootstrap-server $KAFKA_IP:9092

docker run -it kafka_kafka bin/kafka-console-consumer.sh --topic test --from-beginning --bootstrap-server $KAFKA_IP:9092
```



https://github.com/wurstmeister/kafka-docker/issues/389