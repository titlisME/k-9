pipeline {
  agent any
  stages {
    stage('Run Test') {
      steps {
        echo 'Running Tests'
        sh 'ls'
      }
    }
    stage('Pull next commit') {
      steps {
        withCredentials(bindings: [usernamePassword(credentialsId: 'github', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
          sh '''touch test2.txt
git add .
git commit -m "test"
origin = $(git remote -v | grep -m1 "" | sed -E "s/.*https://(\\/\\/.*.git).*/\\1/")
git push https://${GIT_USERNAME}:${GIT_PASSWORD}@$origin jenkins'''
        }

      }
    }
  }
}