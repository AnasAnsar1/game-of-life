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
    stage('post_build_message') {
      steps {
        sh 'echo "Changed message for pollSCM"'
      }
    }
  }

  post {
    success {
      archiveArtifacts artifacts: '/home/ubuntu/remote_root/workspace/Game-of-life/gameoflife-web/target/gameoflife.war'
    }

    always {
      junit '/remote_root/workspace/Game-of-life/gameoflife-web/target/surefire-reports/*.xml'
    }
  }

}