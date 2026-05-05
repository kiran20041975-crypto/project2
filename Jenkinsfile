pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t kiran1975/nodejs-app:latest .'
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'docker push kiran1975/nodejs-app:latest'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl apply -f k8s-deployment.yaml'
                sh 'kubectl apply -f service.yaml'
            }
        }
    }
}