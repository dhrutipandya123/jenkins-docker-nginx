
pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t jenkins-docker-nginx:latest .'
            }
        }

        stage('Deploy with Nginx') {
            steps {
                sh 'docker rm -f jenkins-docker-nginx || true'
                sh 'docker run -d --name jenkins-docker-nginx -p 80:80 jenkins-docker-nginx:latest'
            }
        }
    }
}
