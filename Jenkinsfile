pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "sofiiija/kiii-exercises"
    }

    stages {

        stage('Clone repository') {
            steps {
                checkout scm
            }
        }

        stage('Build image') {
            steps {
                script {
                    docker.build("${DOCKER_IMAGE}")
                }
            }
        }

        stage('Push image') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'dockerhub-credentials') {
                        docker.image("${DOCKER_IMAGE}").push('latest')
                    }
                }
            }
        }
    }
}
