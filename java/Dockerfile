# AlpineLinux with a glibc-2.21 and Oracle Java 8
FROM centos:7 as src
# https://www.oracle.com/java/technologies/javase/javase-jdk8-downloads.html
# Java Version
COPY *.tar.gz /src/

RUN cd /src && tar -xf jdk-*-linux-x64.tar.gz

# 集成了基础工具的centos镜像
FROM centos:7

# Java Version
ENV JAVA_VERSION_MAJOR 8
ENV JAVA_VERSION_MINOR 281
ENV JAVA_VERSION_BUILD 14

COPY --from=src /src/jdk1.${JAVA_VERSION_MAJOR}.0_${JAVA_VERSION_MINOR} /opt/jdk

# Set environment
ENV JAVA_HOME /opt/jdk
ENV PATH ${PATH}:${JAVA_HOME}/bin
ENV JAVA_OPTS -XX:+UnlockExperimentalVMOptions -XX:+UseCGroupMemoryLimitForHeap -XX:MaxRAMFraction=2 -Xmx512m -Xms512m -Dfile.encoding=utf-8 -XX:+PrintFlagsFinal -XshowSettings:vm

WORKDIR /app
