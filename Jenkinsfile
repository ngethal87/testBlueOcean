pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'make build'
      }
    }
    stage('Test') {
      steps {
        parallel(
          "Test": {
            sh 'make test'
            
          },
          "Test 02": {
            sh 'echo \'hello, world!\''
            
          }
        )
      }
    }
    stage('Deploy') {
      steps {
        sh 'echo \'Deploy step\''
      }
    }
  }
}