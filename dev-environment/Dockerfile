FROM debian/stable-slim
LABEL authors="jbrofee"

# Installs tools
RUN apt-get update && \
    apt-get install -y \
    bash \
    git \
    curl \
    neovim \


ENTRYPOINT ["top", "-b"]