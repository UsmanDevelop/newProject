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
                    // Build Docker image using the Dockerfile in the current directory (.)
                    docker.build('frontend', '.')
                }
            }
        }
        stage('Run Container') {
            steps {
                script {
                    // Stop and remove any existing container with the same name
                    sh 'docker rm -f frontend || true'
                    // Run the Docker container
                    sh 'docker run -d --name frontend -p 3000:3000 frontend'
                }
            }
        }
    }
    post {
        always {
            echo 'Pipeline execution completed.'
        }
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Please check the logs.'
        }
    }
}
