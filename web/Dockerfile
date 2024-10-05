FROM ubuntu:24.04

ENV PATH=$PATH:/root/flutter/bin
RUN apt-get update -y \
    && apt-get upgrade -y \
    && apt-get install git curl xz-utils unzip -y \
    && curl -fL -o /root/flutter.tar.xz https://storage.googleapis.com/flutter_infra_release/releases/stable/linux/flutter_linux_3.24.3-stable.tar.xz  \
    && tar -xf /root/flutter.tar.xz -C /root/ \
    && rm -f /root/flutter.tar.xz \
    && chown -R $(whoami) /root/flutter \
    && flutter doctor 

