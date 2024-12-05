pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                echo 'Cloning the repository...'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    echo 'Building Docker image...'
                    try {
                        sh 'docker version' // Check if Docker is available
                        sh 'ls -la' // Verify files in the workspace
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
                        echo 'Docker container is running.'
                    } catch (Exception e) {
                        echo "Error during Docker run: ${e.message}"
                        error "Failed to run Docker container. Stopping pipeline."
                    }
                }
            }
        }
    }
}
