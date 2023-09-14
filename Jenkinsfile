pipeline {
  agent { label 'GOL' }

  triggers { pollSCM ('* * * * *') }

  stages {
    stage('SCM') {
      steps {
        git branch: 'master', url: 'https://github.com/AnasAnsar1/game-of-life.git'
      }
    } 
    
    stage('build & SonarQube analysis') {
      steps {
        withSonarQubeEnv('SELF_HOSTED') {
          sh 'mvn clean package sonar:sonar'
        }
      }
    }
    
    post {
      always {
        junit '**/surefire-report/*.xml'
      }
    }

  }
}