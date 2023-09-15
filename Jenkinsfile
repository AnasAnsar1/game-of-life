pipeline {
  agent { label 'GOL' }

  triggers { pollSCM ('* * * * *') }

  stages {
    stage('SCM') {
      steps {
        git branch: 'master', url: 'https://github.com/AnasAnsar1/game-of-life.git'
      }
    } 
    
    stage('build package') {
      steps {
        sh 'mvn package'
      }
    }
  }

  post {
      always {
        junit '**/surefire-report/*.xml'
      }
    }

}