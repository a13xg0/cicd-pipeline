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
        sh 'docker build -t gorbach_cicd'
      }
    }

  }
}