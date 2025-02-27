# Use Amazon Corretto 17 as the base image
FROM public.ecr.aws/amazoncorretto/amazoncorretto:17-al2023

# Install necessary dependencies for building Python
RUN dnf install -y \
    gcc gcc-c++ make \
    zlib-devel bzip2 bzip2-devel readline-devel \
    sqlite sqlite-devel openssl-devel \
    libffi-devel xz-devel tar curl && \
    dnf clean all

# Set working directory
WORKDIR /usr/src

# Download and compile Python 3.12.9
RUN curl -fsSL -o Python-3.12.9.tgz https://www.python.org/ftp/python/3.12.9/Python-3.12.9.tgz && \
    tar -xzf Python-3.12.9.tgz && cd Python-3.12.9 && \
    ./configure --enable-optimizations && \
    make -j$(nproc) && make altinstall && \
    cd .. && rm -rf Python-3.12.9 Python-3.12.9.tgz

# Ensure the system uses Python 3.12 instead of the default version
RUN alternatives --install /usr/bin/python3 python3 /usr/local/bin/python3.12 1 && \
    alternatives --set python3 /usr/local/bin/python3.12

# Update `dnf` to use the new Python 3.12 instead of the default version
RUN sed -i '1s|#!/usr/bin/python3|#!/usr/local/bin/python3.12|' /usr/bin/dnf
