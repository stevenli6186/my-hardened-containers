# Use Red Hat UBI 9 as the base image
FROM registry.access.redhat.com/ubi9/ubi:latest

# Set environment variables
ENV JAVA_HOME=/usr/lib/jvm/java-17-amazon-corretto
ENV PATH="$JAVA_HOME/bin:$PATH"

# Swap curl-minimal for curl and install dependencies
RUN dnf swap -y curl-minimal curl \
    && dnf install -y dnf-utils \
    && curl -o /tmp/corretto-17.rpm https://corretto.aws/downloads/latest/amazon-corretto-17-x64-linux-jdk.rpm \
    && dnf install -y /tmp/corretto-17.rpm \
    && rm -f /tmp/corretto-17.rpm \
    && dnf clean all
