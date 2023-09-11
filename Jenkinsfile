pipeline {
  agent { label 'GOL-JDK' }

  triggers { pollSCM ('* * * * *') }

  parameters {
    string(name: 'Maven_Goal', defaultValue: 'mvn', description: 'Enter maven goal.' )
  }

  stages {
    stage('SCM') {
      steps {
        git branch: 'master', url: 'https://github.com/AnasAnsar1/game-of-life.git'
      }
    } 
    stage('build') {
      steps {
        sh "${params.Maven_Goal}"
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