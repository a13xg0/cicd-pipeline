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

  }
}