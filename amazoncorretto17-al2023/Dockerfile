# Use the latest Amazon Corretto 17 on AL2023 as the base image
FROM public.ecr.aws/amazoncorretto/amazoncorretto:17-al2023

# Remove existing Python versions (including Python 3.9)
RUN dnf remove -y python3 python3-libs && \
    dnf clean all && rm -rf /var/cache/dnf

# Install required dependencies for building Python 3.12.9
RUN dnf install -y \
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

# Set Python 3.12.9 as the default and remove any old symlinks
RUN ln -sf /usr/local/bin/python3.12 /usr/bin/python3 && \
    ln -sf /usr/local/bin/python3.12 /usr/bin/python && \
    rm -f /usr/bin/python3.9 /usr/local/bin/python3.9

