# 🎨 EarDefender – Frontend

**User Interface for Audio DeepFake Detection**

## 🚀 Overview

The **Frontend** module provides the graphical interface for the EarDefender platform.
Built with **Vue.js**, it enables users to:

- Submit audio/video materials for analysis

- Configure analysis options and detection methods

- View detailed DeepFake detection results

- Access links and metadata from processed content


Designed to be lightweight, responsive, and integrated directly with the Connector API.


## 🐳 Running via Docker (recommended)

1. **Build Docker image**

`docker build -t frontend-app .`

2. **Run container**

Expose the application on port 8080:

`docker run -p 8080:8080 frontend-app`



## 💻 Running Locally (without Docker)

1. **Install dependencies**

`npm install`

2. **Start development server (hot reload)**

`npm run serve`

3. **Build for production**

`npm run build`

4. **Lint and fix files**

`npm run lint`


## ⚙️ Additional Configuration

For advanced project configuration, see the official** Vue CLI reference**:

👉 https://cli.vuejs.org/config/
