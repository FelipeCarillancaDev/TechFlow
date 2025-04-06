# Task API TechFlow

Este proyecto muestra una API Node.js que hace pruebas de función con Jest, utiliza Jenkins para automatizar el proceso de compilación, prueba e implementación.

## 🧱 Paso 1: Gestión del Repositorio Git

### 🧩 Inicializar repositorio local
```bash
git init
```

### 🧩 Crear y añadir README.md
```bash
echo "# TechFlow" > README.md
git add README.md
git commit -m "chore: primer commit con README"
```

### 🔗 Conectar con repositorio remoto en GitHub
1. Crear repositorio en GitHub.
2. Luego, enlazarlo con:
```bash
git remote add origin https://github.com/FelipeCarillancaDev/TechFlow
git push -u origin main
```

✅ ¡Repositorio conectado correctamente!

---
### 📋 Rutas disponibles
- `GET /users` → Retorna lista de usuarios.
- `GET /users/:id` → Retorna un usuario específica por ID.

---

## 🔄 Paso 2: Pipeline de Jenkins

### 🛠️ Requisitos previos
- Jenkins instalado (local o en servidor).
- Plugin: Git.
- Configuración de credenciales GitHub (token si es privado).

### 📁 Jenkinsfile explicativo
```groovy
pipeline {
    agent any

    stages {
        stage('Clonar Repositorio') {
            steps {
                git branch: 'main', url: 'https://github.com/tu_usuario/tu_repositorio.git'
            }
        }

        stage('Instalar Dependencias') {
            steps {
                bat 'npm install'
            }
        }

        stage('Ejecutar Pruebas') {
            steps {
                bat 'npm test'
            }
        }

        stage('Levantar API') {
            steps {
                echo 'Levantando API...'
                bat 'start /B npm start'
                sleep time: 5, unit: 'SECONDS'
            }
        }
    }
}
```