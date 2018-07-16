pipeline {
  agent any
  stages {
    stage('Run Test') {
      steps {
        echo 'Running Tests'
        sh 'ls'
      }
    }
    stage('Pull next commit from master') {
      steps {
        sh 'git branch'
      }
    }
    stage('1') {
      steps {
        sh 'git log'
      }
    }
    stage('2') {
      steps {
        sh 'git remote -v'
      }
    }
  }
}