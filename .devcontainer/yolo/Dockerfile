FROM nvcr.io/nvidia/pytorch:21.11-py3

ARG USERNAME
ARG USER_UID
ARG USER_GID

ENV HOME /home/$USERNAME
ENV SHELL /bin/bash

RUN groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME \
    && apt update \
    && apt upgrade --no-install-recommends -y \
    && apt install --no-install-recommends -y sudo curl wget git tmux zip htop screen libgl1-mesa-glx \
    && apt install --no-install-recommends -y libglib2.0-0 libsm6 libxrender1 libxext6 libgl1-mesa-dev \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME \
    && apt autoremove -y \
    && apt clean -y \
    && rm -rf /var/lib/apt/lists/*

USER $USERNAME
WORKDIR $HOME

RUN pip install --upgrade pip \
    && pip install --upgrade seaborn thop