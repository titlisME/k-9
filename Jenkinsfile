pipeline {
  agent any
  stages {
    stage('Run Test') {
      steps {
        echo 'Running Tests'
      }
    }
    stage('Pull next commit from master') {
      steps {
        sh 'git log'
      }
    }
  }
}