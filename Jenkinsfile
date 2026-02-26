pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                echo 'Cloning repository...'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("lab6-backend")
                }
            }
        }

        stage('Run Container') {
            steps {
                script {
                    sh 'docker run -d --name lab6-container -p 8081:80 lab6-backend || true'
                }
            }
        }
    }
}
