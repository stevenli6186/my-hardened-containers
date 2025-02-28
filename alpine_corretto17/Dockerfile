# Use the latest Alpine image
FROM alpine:latest

# Set environment variables for non-interactive installation
ENV JAVA_HOME=/usr/lib/jvm/corretto-17
ENV PATH="${JAVA_HOME}/bin:${PATH}"

# Install required dependencies
RUN apk add --no-cache curl tar bash gcompat \
    && wget -O /tmp/corretto.tar.gz https://corretto.aws/downloads/latest/amazon-corretto-17-x64-linux-jdk.tar.gz \
    && mkdir -p ${JAVA_HOME} \
    && tar -xzf /tmp/corretto.tar.gz -C ${JAVA_HOME} --strip-components=1 \
    && rm -rf /tmp/corretto.tar.gz

# Verify installation
RUN java -version
