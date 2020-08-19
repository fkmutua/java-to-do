
pipeline {
    agent any
    tools {
        gradle "Gradle-6"
    }
    stages {
      stage('clone repository') {
          steps {
              git 'https://github.com/fkmutua/java-to-do'
            }
        }
        stage('Build the project') {
            steps {
                sh 'gradle build'
            }
        }
        stage('Tests') {
            steps {
                sh 'gradle test'
            }
        }
        stage('Deploy to Heroku') {
  steps {
    withCredentials([usernameColonPassword(credentialsId: 'mutua', variable: 'HEROKU_CREDENTIALS' )]){
      sh 'git push https://${HEROKU_CREDENTIALS}@git.heroku.com/fierce-woodland-56405.git master'
            }
        }
    }
    }
}