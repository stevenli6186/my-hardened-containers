# Use Fedora 41 as the base image
FROM fedora:41

# Set the release version for Fedora 41 to ensure latest package updates
ENV FEDORA_RELEASE=41

# Update the system and install necessary tools
RUN dnf -y update --refresh && \
    dnf -y install dnf-plugins-core curl && \
    dnf clean all

# Install Amazon Corretto 17
RUN curl -fL -o /tmp/corretto-17.rpm https://corretto.aws/downloads/latest/amazon-corretto-17-x64-linux-jdk.rpm && \
    dnf install -y /tmp/corretto-17.rpm && \
    rm -f /tmp/corretto-17.rpm && \
    dnf clean all

# Verify all installed packages are up-to-date
RUN dnf -y upgrade --refresh && dnf clean all

# Verify installation
RUN java -version && python --version && dnf --version