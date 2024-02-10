pipeline {
    agent any

    environment {
        DOCKER_CREDENTIALS_ID = 'your-docker-hub-credentials-id'
        DOCKER_IMAGE_NAME = 'your-docker-image-name'
        DOCKER_IMAGE_TAG = 'latest'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("${DOCKER_IMAGE_NAME}:${DOCKER_IMAGE_TAG}")
                }
            }
        }

        stage('Push Docker Image to Docker Hub') {
            steps {
                script {
                    withCredentials([usernamePassword(credentialsId: "${docker-cred}", usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
                        docker.withRegistry('https://index.docker.io/v1/', "docker") {
                            docker.image("${DOCKER_IMAGE_NAME}:${DOCKER_IMAGE_TAG}").push("${DOCKER_IMAGE_TAG}")
                        }
                    }
                }
            }
        }
    }
}


