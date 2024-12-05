pipeline {
    agent any
    environment {
        DOCKER_IMAGE = 'frontend'
        GITHUB_REPO = 'https://github.com/UsmanDevelop/newProject.git'
    }
    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/UsmanDevelop/newProject.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("${env.DOCKER_IMAGE}")
                }
            }
        }
        stage('Run Container') {
            steps {
                sh 'docker run -d -p 3000:3000 ${env.DOCKER_IMAGE}'
            }
        }
    }
}
