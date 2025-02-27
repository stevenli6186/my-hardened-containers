# Use the latest Amazon Corretto 17 on AL2023 as the base image
FROM amazoncorretto:17-al2023

# Update the system and apply security patches
RUN dnf update -y && \
    dnf clean all && \
    rm -rf /var/cache/dnf