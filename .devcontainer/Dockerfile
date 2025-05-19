ARG NODE_VERSION=22

FROM node:${NODE_VERSION}

# Evitar interacciones con apt-get
ENV DEBIAN_FRONTEND=noninteractive

# Instalar dependencias
RUN apt-get update && apt-get install -y \
    git \
    curl \
    wget \
    zip \
    unzip \
    nano \
    sudo \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Configurar sudo para el usuario node
RUN echo "node ALL=(ALL) NOPASSWD:ALL" > /etc/sudoers.d/node \
    && chmod 0440 /etc/sudoers.d/node

# Configurar directorios de trabajo
WORKDIR /workspace

# Argumentos para versiones
ARG ANGULAR_VERSION=16

# Instalar Angular CLI globalmente con la versión específica
RUN npm install -g @angular/cli@${ANGULAR_VERSION}

# Configuración de Git para evitar problemas de permisos
RUN git config --system core.editor "code --wait" \
    && git config --system core.autocrlf input

# Mensaje de versión para confirmar instalación correcta
RUN echo "Node.js $(node -v)" \
    && echo "npm $(npm -v)" \
    && echo "Angular CLI $(ng version --version)"