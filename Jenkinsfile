pipeline {
    agent any

    environment {
        IMAGE_NAME = 'java-hello'
        IMAGE_TAG = 'v1'
    }

    stages {
        stage('Build Docker Image') {
            steps {
                bat 'docker build -t java-hello:v1 .'
            }
        }

        stage('Run Container') {
            steps {
                bat 'docker run --rm java-hello:v1'
            }
        }

        stage('Push to Docker Hub') {
    steps {
        withCredentials([usernamePassword(credentialsId: 'docker-hub-login', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
            bat '''
                echo %DOCKER_PASS% | docker login -u %DOCKER_USER% --password-stdin
                docker tag java-hello:v1 %DOCKER_USER%/java-hello:v1
                docker push %DOCKER_USER%/java-hello:v1
            '''
        }
    }
}

    }
}
