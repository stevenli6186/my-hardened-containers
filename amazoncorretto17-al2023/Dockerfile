# Use the latest Amazon Corretto 17 on AL2023 as the base image
FROM public.ecr.aws/amazoncorretto/amazoncorretto:17-al2023

# Install required dependencies for building Python 3.12.9
RUN dnf update -y && \
    dnf install -y \
      gcc gcc-c++ make \
      zlib-devel bzip2 bzip2-devel readline-devel \
      sqlite sqlite-devel openssl-devel \
      libffi-devel xz-devel && \
    curl -fsSL -o Python-3.12.9.tgz https://www.python.org/ftp/python/3.12.9/Python-3.12.9.tgz && \
    tar -xzf Python-3.12.9.tgz && cd Python-3.12.9 && \
    ./configure --enable-optimizations && \
    make -j$(nproc) && make altinstall && \
    cd .. && rm -rf Python-3.12.9 Python-3.12.9.tgz && \
    dnf clean all && rm -rf /var/cache/dnf

# Set Python 3.12.9 as the default for `python3` and `python`
RUN alternatives --install /usr/bin/python3 python3 /usr/local/bin/python3.12 1 && \
    alternatives --install /usr/bin/python python /usr/local/bin/python3.12 1
