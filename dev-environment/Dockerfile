FROM debian/stable-slim
LABEL authors="jbrofee"

# Installs tools
RUN apt-get update && \
    apt-get install -y \
    bash \
    git \
    curl \
    neovim \
    openjdk-21-jre-headless \
    lazygit \
    ripgrep \
    fzf \
    fd-find

RUN curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash
RUN nvm install --lts


ENTRYPOINT ["top", "-b"]