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
          sh '''git log --reverse | tail -n 10
git remote add new https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/titlisME/k-9.git
git fetch --all
git branch -r
git remote -v
git checkout -b master new/master
commits=$(git log --reverse --format=%H HEAD..master)'''
        }

      }
    }
  }
}