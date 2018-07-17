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
    stage('3') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'github', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
          sh '''touch 123.txt
          git add .
          git commit -m "test"
          git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/titlisME/k-9.git jenkins'''
        }
      }
    }
  }
}
