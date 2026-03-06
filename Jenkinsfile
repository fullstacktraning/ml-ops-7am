pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                git 'https://github.com/fullstacktraning/ml-ops-7am.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t ml-fastapi-app .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker stop ml-container || true'
                sh 'docker rm ml-container || true'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d -p 8000:8000 --name ml-container ml-fastapi-app'
            }
        }

    }
}