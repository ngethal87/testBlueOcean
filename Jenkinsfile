pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh '''echo 'here goes the building steps'
javac HelloWorld.java'''
      }
    }
    stage('Test') {
      steps {
        parallel(
          "Test-01": {
            sh '''echo 'here goes the testing steps'
java HelloWorld'''
            
          },
          "Test-02": {
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