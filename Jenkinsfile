pipeline {
    agent any

    stages {
        stage('Clonar Repositorio') {
            steps {
                git branch: 'main', url: 'https://github.com/FelipeCarillancaDev/TechFlow.git'
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
