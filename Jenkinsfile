pipeline {
  agent { label 'GOL-JDK' }

  triggers { pollSCM ('* * * * *') }

  stages {
    stage('SCM') {
      steps {
        git branch: 'master', url: 'https://github.com/AnasAnsar1/game-of-life.git'
        mail subject: 'Git'
          body: 'Repo has been cloned'
          to: 'ansariianas78@gmail.com'
      }
    } 
    stage('build') {
      steps {
        sh "mvn package"
      }
    }
  }

  post {
    success {
      archiveArtifacts artifacts: '**/*.war'
      mail subject: 'Build Success'
        body: 'Build has been succeded'
        to: 'ansariianas78@gmail.com'
    }

    always {
      junit '**/surefire-reports/*.xml'
      mail subject: 'Build is Done'
        body: 'Build done message'
        to: 'ansariianas78@gmail.com'
    }

    failure {
      mail subject: 'Build has failed'
        body: 'Build has been failed'
        to: 'ansariianas78@gmail.com'
    }
  }

}