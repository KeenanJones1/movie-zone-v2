FROM ubuntu:22.04

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y \
    curl \
    git \
    vim \
    build-essential \
    python3.10 \
    python3-pip \
    python3.10-venv \
    nodejs \
    npm \
    && apt-get clean

RUN update-alternatives --install /usr/bin/python python /usr/bin/python3.10 1

# Create workdir
WORKDIR /app

# Copy Python and Node deps
COPY requirements.txt ./
COPY package.json ./