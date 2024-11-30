pipeline {
  agent any
  stages {
    stage('Build and Run MERN Application') {
      steps {
        script {
          // Build the Docker image for the MERN application
          sh 'docker build -t mern-app .'

          // Run the newly built Docker container
          sh 'docker run -d -p 3000:3000 --name mern-app mern-app'
        }
      }
    }
  }
}
