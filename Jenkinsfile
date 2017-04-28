pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'echo \'here goes the building steps\''
      }
    }
    stage('Test') {
      steps {
        parallel(
          "Test": {
            sh 'echo \'here goes the testing steps\''
            
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