pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }

    stage('Application Build') {
      steps {
        sh 'scripts/build.sh'
      }
    }

    stage('Application Test') {
      steps {
        sh 'scripts/test.sh'
      }
    }

    stage('Docker image build') {
      steps {
        sh 'docker build -t gorbach_cicd .'
      }
    }
    
    stage('Docker image deploy') {
      steps {
        docker.withRegistry('https://registry.hub.docker.com', 'dockerhub-cicd')
        {
          app.push("$env.BUILD_NUMBER")
          app.push("latest")
        }
      }
    }

  }
}
