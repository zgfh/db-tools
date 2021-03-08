FROM java:8 as src
ADD https://downloads.apache.org/kafka/2.7.0/kafka_2.13-2.7.0.tgz /src/
RUN cd /src/ ; tar -zvxf kafka_2.13-2.7.0.tgz
VOLUME /tmp/


FROM java:8
COPY --from=src /src/kafka_2.13-2.7.0/ /app/
EXPOSE 9092 2181
VOLUME /tmp/
CMD ["bash","-c","bin/zookeeper-server-start.sh -daemon config/zookeeper.properties && bin/kafka-server-start.sh config/server.properties "]