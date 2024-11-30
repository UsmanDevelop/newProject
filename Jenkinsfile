pipeline {
  agent any
  stages {
    stage('Checkout Code') {
      steps {
        checkout([
          $class: 'GitSCM',
          branches: [[name: '*/main']], // Replace 'main' with the correct branch name if different
          userRemoteConfigs: [[url: 'https://github.com/UsmanDevelop/RegistrationPage.git']] // Replace with your repository URL
        ])
      }
    }
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
