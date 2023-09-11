pipeline {
  agent { label 'GOL-JDK' }

  triggers { pollSCM ('* * * * *') }

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
  }

  post {
    success {
      archiveArtifacts artifacts: '**/*.war'
    }

    always {
      junit '**/surefire-reports/*.xml'
    }
  }

}