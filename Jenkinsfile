pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-app:latest .'
            }
        }

        stage('Remove Old Container') {
            steps {
                sh '''
                docker stop devops-container || true
                docker rm devops-container || true
                '''
            }
        }

        stage('Run New Container') {
            steps {
                sh '''
                docker run -d \
                --name devops-container \
                -p 5000:5000 \
                devops-app:latest
                '''
            }
        }

        stage('Health Check') {
            steps {
                sh 'docker ps'
            }
        }
    }
}
