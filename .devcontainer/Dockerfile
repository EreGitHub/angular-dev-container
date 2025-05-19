# Argumentos para versiones
ARG NODE_VERSION=22
ARG ANGULAR_VERSION=16

# Base: Node slim con versiones específicas
FROM node:${NODE_VERSION}-slim

# Evitar interacciones con apt-get
ENV DEBIAN_FRONTEND=noninteractive

# Instalar dependencias y herramientas de desarrollo
RUN apt-get update && apt-get install -y --no-install-recommends \
    git \
    curl \
    wget \
    zip \
    unzip \
    nano \
    sudo \
    # Herramientas de desarrollo útiles
    jq \
    tree \
    htop \
    # Para manejo de archivos
    xz-utils \
    # Para soporte de iconos
    libx11-dev \
    libxkbfile-dev \
    # Para soporte de build
    build-essential \
    && rm -rf /var/lib/apt/lists/*

# Configurar usuario y permisos
RUN echo "node ALL=(ALL) NOPASSWD:ALL" > /etc/sudoers.d/node \
    && chmod 0440 /etc/sudoers.d/node \
    && usermod -aG sudo node

# Configurar directorios de trabajo
WORKDIR /workspace

# Instalar Angular CLI globalmente
RUN npm install -g @angular/cli@${ANGULAR_VERSION}

# Configurar Git
RUN git config --system core.editor "nano" \
    && git config --system core.autocrlf input \
    && git config --system --add safe.directory /workspace

# Configurar npm
# RUN npm config set unsafe-perm true

# Crear directorio para el proyecto
# RUN mkdir -p /workspace/angular-app

# Establecer permisos
# RUN chown -R node:node /workspace

# Usuario por defecto
USER node

# Mensaje de bienvenida
RUN echo 'echo "Bienvenido al entorno de desarrollo Angular"' >> /home/node/.bashrc

# Comando por defecto
CMD ["bash"]

# Muestra versiones instaladas
RUN echo "Node.js: $(node -v)" \ 
    && echo "Angular CLI: $(ng version --version)"