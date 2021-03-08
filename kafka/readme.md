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
# 把192.168.1.7替换为你的机器ip
docker-compose up -d -e HOSTIP=192.168.1.7
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