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
                script {
                    // Use withCredentials to securely access Docker credentials
                    withCredentials([[$class: 'UsernamePasswordMultiBinding', credentialsId: 'docker-cred', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD']]) {
                        // Use the Docker Hub credentials from Jenkins credentials store
                        sh 'docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD'
                        sh 'docker push my-image:latest'
                    }
                    // Add additional deployment steps here if needed
                }
            }
        }
    }
}

