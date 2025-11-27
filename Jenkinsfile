pipeline {
  agent any

  environment {
    PATH = "/usr/local/bin:${env.PATH}"
  }

  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }
    
    stage('Install Backend Dependencies') {
      steps {
        dir('backend') {
          sh 'npm install'
          // sh 'npm test'   // Optional: uncomment if you have backend tests
        }
      }
    }
    
    stage('Install and Build Frontend') {
      steps {
        dir('frontend') {
          sh 'npm install'
          sh 'npm run build'
        }
      }
    }

    stage('Build and Deploy Docker Containers') {
      steps {
        sh 'docker compose build'
        sh 'docker compose up -d'
      }
    }
  }

  post {
    success {
      echo 'Full-stack build and deployment succeeded!'
    }
    failure {
      echo 'Build or deployment failed.'
    }
  }
}
