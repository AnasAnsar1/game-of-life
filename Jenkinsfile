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
      archiveArtifacts artifacts: '/home/ubuntu/remote_root/workspace/Game-of-life/gameoflife-web/target/gameoflife.war'
    }

    always {
      junit '**/surefire-reports/*.xml'
    }
  }

}