pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                script {
                    docker.build('my-image:latest')
                }
            }
        }
        stage('Deploy') {
            steps {
                // Here you can add steps to deploy your Docker image if needed
            }
        }
    }
}

