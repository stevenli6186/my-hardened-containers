# Use Amazon Linux 2023 as the base image
FROM amazonlinux:2023

# Set working directory
WORKDIR /usr/src

# Manually install Amazon Corretto 17 without dnf
RUN curl -fsSL -o corretto-17.tar.gz https://corretto.aws/downloads/latest/amazon-corretto-17-x64-linux-jdk.tar.gz && \
    /bin/tar -xzf corretto-17.tar.gz && \
    mv amazon-corretto-17* /usr/lib/jvm/java-17-amazon-corretto && \
    rm -rf corretto-17.tar.gz

# Set Java environment variables
ENV JAVA_HOME=/usr/lib/jvm/java-17-amazon-corretto
ENV PATH="${JAVA_HOME}/bin:${PATH}"
