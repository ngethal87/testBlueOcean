pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh '''echo 'here goes the building steps'
javac -cp .:/usr/share/java/junit4-4.12.jar  Calculator.java 
javac -cp .:/usr/share/java/junit4-4.12.jar  CalculatorTest.java
'''
      }
    }
    stage('Test') {
      steps {
        parallel(
          "Test-01": {
            sh '''echo 'here goes the testing steps'
java -cp .:/usr/share/java/junit4-4.12.jar org.junit.runner.JUnitCore  CalculatorTest'''
            
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