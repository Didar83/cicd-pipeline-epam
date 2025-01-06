pipeline {
  agent {
    docker {
      image 'node:7.8.0'
      args '-p 3000:3000'
    }

  }
  stages {
    stage('Checkout') {
      steps {
        sh 'docker ps'
      }
    }

  }
}