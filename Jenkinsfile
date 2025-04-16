pipeline {
agent any
stages {
stage('Clone Repository') {
steps {
git branch: 'main', url: 'https://github.com/PriteshBhuravane/java-docker-jenkins-pipeline.git'
}
}

stage('Build Docker Image') {
steps {
script {
docker.build("java-hello-world-app")

}
}
}
stage('Run Docker Container') {
steps {
script {
docker.image("java-hello-world-app").run()
}
}
}
}
}
