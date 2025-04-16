pipeline {
    agent any

    environment {
        IMAGE_NAME = 'java-hello'
        IMAGE_TAG = 'v1'
        DOCKER_HUB_USER = 'admin' // optional
    }

    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("${IMAGE_NAME}:${IMAGE_TAG}")
                }
            }
        }

        stage('Run Container') {
            steps {
                script {
                    docker.image("${IMAGE_NAME}:${IMAGE_TAG}").run()
                }
            }
        }

        // Optional: Push to Docker Hub
        stage('Push to Docker Hub') {
            steps {
                withDockerRegistry([ credentialsId: 'docker-hub-login', url: '' ]) {
                    script {
                        docker.image("${IMAGE_NAME}:${IMAGE_TAG}").push()
                    }
                }
            }
        }
    }
}
