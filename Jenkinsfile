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
                    sh 'docker login -u newyaf44 -p klausisgay'
                    sh 'docker push my-image:latest'
                    // Add additional deployment steps here if needed
                }
            }
        }
    }
}


