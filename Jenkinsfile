pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t nodejs-demo:latest .'
            }
        }

        stage('Run Container Test') {
            steps {
                sh 'docker rm -f node-container || true'
                sh 'docker run -d -p 3000:3000 --name node-container nodejs-demo:latest'
            }
        }

        stage('Check Running Container') {
            steps {
                sh 'docker ps'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
               sh 'kubectl apply -f k8s-deployment.yaml'
               sh 'kubectl apply -f k8s-service.yaml'
            }
        }

        stage('Verify Kubernetes Deployment') {
            steps {
                sh 'kubectl get pods'
                sh 'kubectl get svc'
            }
        }
    }
}