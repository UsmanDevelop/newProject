pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/UsmanDevelop/newProject.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build('frontend','.')
                }
            }
        }
        stage('Run Container') {
            steps {
                sh 'docker run -d -p 3000:3000 frontend'
            }
        }
    }
}
