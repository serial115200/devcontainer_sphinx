# syntax=docker/dockerfile:1.3-labs

ARG VARIANT=3-bullseye
FROM mcr.microsoft.com/vscode/devcontainers/python:${VARIANT}

COPY config /
COPY requirements.txt /

#RUN <<EOF
#sed -i 's/deb.debian.org/mirrors.ustc.edu.cn/g' /etc/apt/sources.list
#pip config set global.index-url https://mirrors.ustc.edu.cn/pypi/web/simple
#EOF

RUN <<EOF
apt-get update
apt-get install --no-install-recommends --yes \
     graphviz \
     imagemagick \
     make \
     git
apt-get autoremove
apt-get clean
rm -rf /var/lib/apt/lists/*
EOF

RUN <<EOF
pip3 install --no-cache-dir --upgrade pip3
pip3 install --no-cache-dir -r requirements.txt
EOF
