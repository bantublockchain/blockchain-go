pipeline {

  environment {
    registry = 'interstellartech/blockchain-expansion'
    registryCredential = 'dockerhub-interstellartech'
  }

  agent any
  stages {
    stage('build') {
      steps {
        sh '''go build -o ./services/horizon/expansion ./services/horizon
'''
      }
    }

    stage('Building image') {
      steps{
        script {
          dockerImage = docker.build("$registry:$BUILD_NUMBER", "-f services/horizon/Dockerfile services/horizon")
        }
      }
    }

    stage('Deploy Image') {
      steps{
        script {
          docker.withRegistry( '', registryCredential ) {
            dockerImage.push()
            dockerImage.push('latest')
          }
        }
      }
    }

    stage('Remove Unused docker image') {
      steps{
        sh "docker rmi $registry:$BUILD_NUMBER"
      }
    }
    
  }
}