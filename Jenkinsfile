pipeline {
  agent { label 'GOL-JDK' }

  triggers { pollSCM ('* * * * *') }

  stages {
    stage('SCM') {
      steps {
        git branch: 'master', url: 'https://github.com/AnasAnsar1/game-of-life.git'
      }
    } 
    stage('build & SonarQube analysis') {
      steps {
        withSonarQubeEnv(credentialsId: 'squ_9c23d123c2c3c4eae650d472f05888bf5cc4697b', installationName: 'GOL_SONAR' ) {
          sh 'mvn clean package sonar:sonar'
        }
      }
    }
  }
}