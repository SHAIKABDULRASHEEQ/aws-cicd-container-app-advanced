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

        stage('Save Image') {
            steps {
                sh 'docker save devops-app:latest -o devops-app.tar'
            }
        }

        stage('Copy Image to App Server') {
    steps {
        sh '''
        scp -i /var/lib/jenkins/.ssh/id_rsa \
        -o StrictHostKeyChecking=no \
        devops-app.tar \
        ec2-user@56.125.218.48:/home/ec2-user/
        '''
    }
}
        }

        stage('Deploy on App Server') {
    steps {
        sh '''
        ssh -i /var/lib/jenkins/.ssh/id_rsa \
        -o StrictHostKeyChecking=no \
        ec2-user@56.125.218.48 "
        docker load -i /home/ec2-user/devops-app.tar &&
        docker stop devops-container || true &&
        docker rm devops-container || true &&
        docker run -d --name devops-container -p 5000:5000 devops-app:latest
        "
        '''
    }
}
    }
}
