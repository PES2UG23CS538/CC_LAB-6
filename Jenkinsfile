pipeline {
    agent any

    stages {

        stage('Build Backend Image') {
            steps {
                script {
                    sh 'docker build -t lab6-backend backend'
                }
            }
        }

        stage('Build NGINX Image') {
            steps {
                script {
                    sh 'docker build -t lab6-nginx nginx'
                }
            }
        }

        stage('Deploy Backend Containers') {
            steps {
                script {
                    sh 'docker rm -f backend1 backend2 || true'
                    sh 'docker run -d --name backend1 lab6-backend'
                    sh 'docker run -d --name backend2 lab6-backend'
                }
            }
        }

        stage('Deploy NGINX Load Balancer') {
            steps {
                script {
                    sh 'docker rm -f nginx || true'
                    sh 'docker run -d -p 8080:80 --name nginx --link backend1 --link backend2 lab6-nginx'
                }
            }
        }
    }
}
