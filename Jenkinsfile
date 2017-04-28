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
    stage('Log') {
      steps {
        junit(testResults: 'target', allowEmptyResults: true)
      }
    }
    stage('Deploy') {
      steps {
        sh 'echo \'Deploy step\''
      }
    }
  }
}