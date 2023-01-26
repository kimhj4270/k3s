pipeline {
  agent any
  stages {
    stage('git scm update') {
      steps {
        git url: 'https://github.com/kimhj4270/k3s.git', branch: 'master'
      }
    }

    stage('K8S Manifest Update') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'jitoo', passwordVariable: 'password', usernameVariable: 'username')]) {
          sh 'touch 1.1 && echo "v1,2" >> ./1.1'
          sh 'git init'
          sh 'git add .'
          sh 'git config --global user.email "jjs_0719@naver.com"'
          sh 'git config --global user.name "jitoo"'
          sh 'git branch -m master'
          sh 'sudo git commit -m "Update for Jenkins"'
          sh 'git remote set-url origin https://$username:$password@github.com/jitoo/k3s.git'
          sh 'git push -u origin +master --force'
        }
      }
    }

  }
}

