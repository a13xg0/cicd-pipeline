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
        sh 'docker build -t gorbach_cicd:$BUILD_NUMBER .'
      }
    }

    stage('Docker image deploy') {
      steps {
        script {
          docker.withRegistry('https://registry.hub.docker.com', 'dockerhub-cicd')
          {
            docker.image("gorbach_cicd:$env.BUILD_NUMBER").push("latest")
          }
        }

      }
    }

  }
}