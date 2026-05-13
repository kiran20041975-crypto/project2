pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t nodejs-demo .'
            }
        }

        stage('Run Container Test') {
            steps {
                sh 'docker rm -f node-container || true'
                sh 'docker run -d -p 3000:3000 --name node-container nodejs-demo'
            }
        }

        stage('Check Running Container') {
            steps {
                sh 'docker ps'
            }
        }
    }
}