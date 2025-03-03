ARG BASE_REGISTRY=registry1.dso.mil
ARG BASE_IMAGE=ironbank/redhat/ubi/ubi8
ARG BASE_TAG=8.10
FROM $BASE_REGISTRY/$BASE_IMAGE:$BASE_TAG

RUN dnf upgrade -y && \
    dnf install -y java-17-openjdk-headless freetype fontconfig dejavu-sans-fonts && \
    dnf clean all && \
    rm -rf /var/cache/dnf

# Don't inherit a healthcheck from base image
HEALTHCHECK NONE

ENV LANG C.UTF-8
ENV JAVA_HOME /usr/lib/jvm/jre-17-openjdk
ENV PATH $JAVA_HOME/bin:$PATH
