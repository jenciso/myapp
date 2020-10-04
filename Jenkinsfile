pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        script {
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }

      }
    }

    stage('Push Image') {
      steps {
        script {
          docker.withRegistry( '', registryCredential ) {
            dockerImage.push()
          }
        }

      }
    }

  }
  environment {
    registry = 'jenciso/myapp'
    registryCredential = 'dockerhub'
    dockerImage = ''
  }
}