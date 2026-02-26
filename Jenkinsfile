pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t lab6-backend backend'
                }
            }
        }

        stage('Run Container') {
            steps {
                script {
                    sh 'docker rm -f lab6-container || true'
                    sh 'docker run -d -p 8081:8080 --name lab6-container lab6-backend'
                }
            }
        }
    }
}
