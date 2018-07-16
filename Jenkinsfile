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
        sh '''touch test.txt
git add .
git commit -m "test push"
git push origin jenkins'''
      }
    }
  }
}