# Use the latest Ubuntu 24 base image
FROM ubuntu:24.04

# Update and apply the latest security patches
RUN apt-get update -y && \
    apt-get upgrade -y && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*