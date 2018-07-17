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
git checkout -t -b master origin/master
git checkout jenkins
commits=$(git log --reverse --format=%H HEAD..master)'''
        }

      }
    }
  }
}