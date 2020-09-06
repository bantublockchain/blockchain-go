pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        sh '''go install services/horizon
'''
      }
    }

    stage('dockerize') {
      steps {
        sh '''docker build -t interstellartech/blockchain-expansion -f services/horizon/Dockerfile services/horizon

'''
      }
    }

  }
}