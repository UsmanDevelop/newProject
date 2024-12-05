pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                echo 'Cloning the repository...'
                git branch: 'main', url: 'https://github.com/UsmanDevelop/newProject.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    echo 'Building Docker image...'
                    try {
                        sh 'docker version' // Check if Docker is available
                        sh 'ls -la' // Verify files in the workspace
                        sh 'docker build -t frontend .' // Use shell command to build Docker image
                        echo 'Docker image built successfully.'
                    } catch (Exception e) {
                        echo "Error during Docker build: ${e.message}"
                        error "Docker build failed. Stopping pipeline."
                    }
                }
            }
        }
        stage('Run Container') {
            steps {
                script {
                    echo 'Running Docker container...'
                    try {
                        sh 'docker run -d -p 3000:3000 frontend'
                        echo 'Docker container is running.'
                    } catch (Exception e) {
                        echo "Error during Docker run: ${e.message}"
                        error "Failed to run Docker container. Stopping pipeline."
                    }
                }
            }
        }
    }
    post {
        always {
            echo 'Pipeline execution completed.'
        }
        failure {
            echo 'Pipeline failed. Please check the logs.'
        }
    }
}
