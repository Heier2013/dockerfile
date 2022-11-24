FROM ubuntu:18.04

# 配置镜像源加速
RUN sed -i 's/ports.ubuntu.com/mirrors.ustc.edu.cn/g' /etc/apt/sources.list \
    && sed -i 's/archive.ubuntu.com/mirrors.ustc.edu.cn/g' /etc/apt/sources.list \
    && sed -i 's/security.ubuntu.com/mirrors.ustc.edu.cn/g' /etc/apt/sources.list

# 设置时区
ENV TZ 'Asia/Shanghai'
RUN echo $TZ > /etc/timezone \
    && apt-get update && apt-get install -y tzdata \
    && rm /etc/localtime \
    && ln -snf /usr/share/zoneinfo/$TZ /etc/localtime \
    && dpkg-reconfigure -f noninteractive tzdata \
    && apt-get clean \
    && rm -rf /tmp/*

# 添加work用户
RUN groupadd -r work --gid=1001 && useradd -r -m -s /bin/bash -g work --uid=1001 work
