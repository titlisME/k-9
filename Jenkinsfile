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
          sh '''if git config remote.neworigin.url > /dev/null; then 
  echo "neworigin remote already exists."; 
else
  git remote add neworigin https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/titlisME/k-9.git
fi
git fetch --all
commits=$(git log --reverse --format=%H HEAD..master)
if [ -z "$commits" ]; then 
  echo "no more commits. done\\!";
else 
  nextcommit=$(echo "$commits" | grep -m1 "");
  git merge --no-edit $commits
  origin=$(git remote -v | grep -m1 "" | sed -E "s/.*https:\\/\\/(.*.git).*/\\1/")
  git push https://${GIT_USERNAME}:${GIT_PASSWORD}@$origin jenkins
fi'''
        }

      }
    }
  }
}