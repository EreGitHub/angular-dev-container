ARG NODE_VERSION=22

FROM node:${NODE_VERSION}-slim

# Evitar interacciones con apt-get
ENV DEBIAN_FRONTEND=noninteractive

# Instalar dependencias
RUN apt-get update && apt-get install -y --no-install-recommends \
    git \
    curl \
    wget \
    zip \
    unzip \
    nano \
    sudo \
 && rm -rf /var/lib/apt/lists/*

# Agrega permiso de sudo sin contraseña al usuario 'node'
RUN echo "node ALL=(ALL) NOPASSWD:ALL" > /etc/sudoers.d/node \
 && chmod 0440 /etc/sudoers.d/node

# Configurar directorios de trabajo
WORKDIR /workspace

# Argumentos para versiones
ARG ANGULAR_VERSION=16

# Instalar Angular CLI globalmente con la versión específica
RUN npm install -g @angular/cli@${ANGULAR_VERSION}

# Configura Git de forma predeterminada (opcional si se usa GitHub Codespaces o VS Code devcontainers)
RUN git config --system core.editor "nano" \
 && git config --system core.autocrlf input

# Muestra versiones instaladas
RUN echo "Node.js: $(node -v)" \ 
    && echo "Angular CLI: $(ng version --version)"