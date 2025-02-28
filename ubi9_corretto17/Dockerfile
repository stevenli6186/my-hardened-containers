# Use Red Hat UBI 9 as the base image
FROM registry.access.redhat.com/ubi9/ubi:latest

# Set environment variables
ENV JAVA_HOME=/usr/lib/jvm/java-17-amazon-corretto
ENV PATH="$JAVA_HOME/bin:$PATH"

# Install dependencies and Corretto 17
RUN dnf install -y dnf-utils \
    && dnf config-manager --add-repo https://corretto.aws/downloads/latest/amazon-corretto-17-x64-linux-jdk.rpm \
    && dnf install -y amazon-corretto-17 \
    && dnf clean all
