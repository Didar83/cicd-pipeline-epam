pipeline {
  agent {
    docker {
      image 'node:7.8.0'
      args '-p 3000:3000'
    }

  }
  stages {
    stage('Check out git') {
      steps {
        echo 'Check out scm'
        checkout scm
      }
    }

    stage('Build') {
      steps {
        echo 'Build with script'
        sh 'script ./scripts/build.sh'
      }
    }

    stage('Test') {
      steps {
        echo 'Test with script'
        sh 'script ./scripts/test.sh'
      }
    }

    stage('Build Docker Image') {
      steps {
        echo 'Build Docker image with Dockerfile'
        script {
          docker.build('didar83/cicd-pipeline-epam')
        }

      }
    }

  }
}