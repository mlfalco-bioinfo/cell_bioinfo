FROM ubuntu:22.04

# Prevents some interactive prompts
ENV DEBIAN_FRONTEND=noninteractive

# Update and install some basic tools
RUN apt-get update && apt-get install -y \
    curl \
    wget \
    git \
    vim \
    sudo \
    build-essential \
    ca-certificates \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

# Create a non-root user (Codespaces best practice)
ARG USERNAME=codespace
ARG USER_UID=1000
ARG USER_GID=$USER_UID

RUN groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME \
    && apt-get update && apt-get install -y sudo \
    && echo "$USERNAME ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME

USER $USERNAME

WORKDIR /home/$USERNAME/app
