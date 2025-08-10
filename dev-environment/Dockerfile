FROM debian:stable-slim
LABEL authors="jbrofee"

ENV SHELL=/bin/bash

ARG GITHUB_TOKEN
ARG NVIM_CONFIG

# Installs tools
RUN apt-get update && \
    apt-get install -y \
    bash \
    git \
    curl \
    neovim \
    openjdk-21-jre-headless \
    openjdk-21-jdk-headless \
    lazygit \
    ripgrep \
    fzf \
    fd-find \
    build-essential \
    lynx \
    luarocks \
    openssh-client

# Installs Node.js and pnpm using nvm
RUN curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash && \
    bash -c "source /root/.nvm/nvm.sh && nvm install --lts && nvm use --lts" && \
    curl -fsSL https://get.pnpm.io/install.sh | sh -

# If a Github token and nvim config repo are present, clones nvim config to image
RUN if [ -n "$NVIM_CONFIG" ] && [ -n "$GITHUB_TOKEN" ]; then \
        git clone "https://x-access-token:${GITHUB_TOKEN}@github.com/jbrofee/${NVIM_CONFIG}.git" /root/.config/nvim; \
    fi

# The folder that is used when you access the container
WORKDIR /workspace

# Ensures pnpm and node are avaulable in the shell
#RUN echo 'source /root/.nvm/nvm.sh' >> /root/.bashrc

ENTRYPOINT ["/bin/bash"]