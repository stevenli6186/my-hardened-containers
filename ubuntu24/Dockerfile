# Use the latest Red Hat UBI 9 image
FROM registry.access.redhat.com/ubi9/ubi:latest

# Set environment variables (adjust as needed)
ENV JAVA_HOME=/usr/lib/jvm/java-17-amazon-corretto \
    PATH=$JAVA_HOME/bin:$PATH

# Update system, fix vulnerabilities, and install dependencies
RUN dnf update -y \
    && dnf install -y dnf-utils \
    && dnf swap -y curl-minimal curl \
    && dnf -y update libxml2 --releasever=2023.6.20250218 \
    && curl -o /tmp/corretto-17.rpm https://corretto.aws/downloads/latest/amazon-corretto-17-x64-linux-jdk.rpm \
    && dnf install -y /tmp/corretto-17.rpm \
    && rm -f /tmp/corretto-17.rpm \
    && dnf clean all