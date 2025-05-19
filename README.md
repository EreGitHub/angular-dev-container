# 🛠️ Angular Dev Container para VS Code

<p align="center">
  <img src="https://angular.io/assets/images/logos/angular/angular.svg" alt="Angular Logo" width="100" style="margin-right: 20px;"/>
  <img src="https://www.docker.com/wp-content/uploads/2022/03/Moby-logo.png" alt="Docker Logo" width="100"/>
</p>

Este repositorio proporciona un entorno de desarrollo aislado y reproducible para aplicaciones Angular, utilizando [Dev Containers](https://code.visualstudio.com/docs/devcontainers/containers) de Visual Studio Code. Ideal para desarrolladores que buscan un entorno consistente sin tener que instalar herramientas localmente.

---

## 🚀 Características principales

- Node.js y Angular CLI configurables mediante argumentos.
- Git, curl, wget, nano y otras utilidades preinstaladas.
- Extensiones útiles de VS Code preconfiguradas (Angular, Prettier, EditorConfig).
- Puertos expuestos por defecto: `4200` (ng serve), `9876` (Karma).
- Persistencia del código fuente en tu máquina local (`src/`).
- Compatible con cualquier sistema que soporte Docker.

---

## ✅ Requisitos
[Dev Containers](https://code.visualstudio.com/docs/devcontainers/containers)
- [Docker](https://www.docker.com/products/docker-desktop)
- [Visual Studio Code](https://code.visualstudio.com/)
- Extensión [Remote - Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) instalada en VS Code.

---

## 📁 Estructura del proyecto

```plaintext
angular-dev-container/
├── .devcontainer/
│   ├── devcontainer.json
│   └── Dockerfile
├── src/                  <-- Aquí se guarda tu proyecto Angular
└── README.md
```

---

## 🧭 Guía paso a paso

### 1. Clonar este repositorio

```bash
git clone https://github.com/EreGitHub/angular-dev-container.git
cd angular-dev-container
```

### 2. Abrir en VS Code

```bash
code .
```

VS Code detectará automáticamente el archivo `.devcontainer/devcontainer.json` y te mostrará una notificación. Selecciona **“Reopen in Container”**.

> Alternativamente: `F1` → `Remote-Containers: Reopen in Container`

### 3. Crear un nuevo proyecto Angular

Dentro del contenedor, abre una terminal:

```bash
ng new my-app
ng serve --host 0.0.0.0   # Inicia el servidor de desarrollo
```

### 4. Usar un proyecto Angular existente

**Opción A: Clona tu proyecto en la carpeta `src/` antes de abrir el contenedor**

```bash
cd angular-dev-container/src
git clone https://github.com/usuario/proyecto-angular.git .
```

**Opción B: Clona dentro del contenedor una vez abierto**

```bash
git clone https://github.com/usuario/proyecto-angular.git .
npm install
ng serve --host 0.0.0.0   # Inicia el servidor de desarrollo
```

---

## ⚙️ Configuración del contenedor

### 📦 Extensiones de VS Code preinstaladas

- [Angular Language Service](https://marketplace.visualstudio.com/items?itemName=Angular.ng-template)
- [Prettier - Code formatter](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
- [EditorConfig for VS Code](https://marketplace.visualstudio.com/items?itemName=EditorConfig.EditorConfig)

### 🔌 Puertos expuestos

- `4200` para `ng serve`
- `9876` para pruebas unitarias con Karma

---

## 🔧 Personalización de versiones de Node.js y Angular CLI

Puedes modificar las versiones de Node.js y Angular CLI editando los argumentos en el archivo `.devcontainer/devcontainer.json`:

```json
"args": {
  "NODE_VERSION": "22.11.0",
  "ANGULAR_VERSION": "19.0.1"
}
```

Después de realizar cambios, reconstruye el contenedor para aplicar nuevas versiones.

---

## ⚠️ Solución de Problemas

### 🔄 Reconstruir el contenedor

Si modificas `Dockerfile` o `devcontainer.json`:

```bash
F1 → Remote-Containers: Rebuild Container
```

### 🛑 Permisos en Linux/macOS

```bash
chmod -R 755 ./src
```

### 🔍 Verificar Versiones

```bash
node -v          # Debe mostrar v22.11.0
ng version       # Debe mostrar Angular CLI: 19.0.1
```

---

## 📌 Notas Importantes

- Tu código está seguro: Todo en `./src` persiste aunque destruyas el contenedor.
- Extensiones recomendadas ya están preinstaladas en el contenedor.
- No necesitas Node/Angular instalados localmente - ¡Todo corre en Docker!

---

## 📄 Licencia

[MIT](LICENSE)

---

## 📬 Contacto

Si tienes dudas o sugerencias, no dudes en crear un issue o enviar un pull request.

¡Feliz codificación con Angular! 🌐🔥