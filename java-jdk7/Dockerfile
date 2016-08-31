FROM debian:stable
MAINTAINER Luigi Quitadamo

ENV DEBIAN_FRONTEND noninteractive

ENV JAVA_DOWNLOAD_BASE_URL http://download.oracle.com/otn-pub/java/jdk
ENV JAVA_FOLDER jdk1.7.0_79
ENV JAVA_VERSION 7u79
ENV JAVA_PATCH b15

ENV JVM_ROOT /usr/lib/jvm

RUN apt-get update && apt-get install -y wget && rm -rf /var/lib/apt/lists/*    && \
    apt-get clean                                                               && \
    apt-get autoremove                                                          && \
    echo Downloading $JAVA_DOWNLOAD_BASE_URL/$JAVA_VERSION-$JAVA_PATCH/jdk-$JAVA_VERSION-linux-x64.tar.gz && \
    wget -q --no-check-certificate --no-cookies --header "Cookie: oraclelicense=accept-securebackup-cookie" \
        $JAVA_DOWNLOAD_BASE_URL/$JAVA_VERSION-$JAVA_PATCH/jdk-$JAVA_VERSION-linux-x64.tar.gz  && \
    tar -xvf jdk-$JAVA_VERSION-linux-x64.tar.gz                                 && \
    rm jdk-$JAVA_VERSION-linux-x64.tar.gz                                       && \
    mkdir -p /usr/lib/jvm                                                       && \
    mv ./$JAVA_FOLDER $JVM_ROOT                                                 && \
    update-alternatives --install /usr/bin/java java $JVM_ROOT/$JAVA_FOLDER/bin/java 1        && \
    update-alternatives --install /usr/bin/javac javac $JVM_ROOT/$JAVA_FOLDER/bin/javac 1     && \
    update-alternatives --install /usr/bin/javaws javaws $JVM_ROOT/$JAVA_FOLDER/bin/javaws 1  && \
    java -version
