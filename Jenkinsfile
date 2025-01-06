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

    stage('Docker Build') {
      agent {
        docker {
          image 'node:lts'
          args '-p 3001:3000'
        }

      }
      steps {
        echo 'Build image with Dockerfile '
        script {
          docker.build('didar83/cicd-pipeline-epam')
        }

      }
    }

  }
}