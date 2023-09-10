pipeline {
  agent { label 'GOL-JDK' }
  stages {
    stage('SCM') {
      steps {
        git branch: 'master', url: 'https://github.com/AnasAnsar1/game-of-life.git'
      }
    } 
    stage('build') {
      steps {
        sh 'mvn package'
      }
    }
    stage('post_build_message') {
      steps {
        sh 'echo "build is done"'
      }
    }
  }
}