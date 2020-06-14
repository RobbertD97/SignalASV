pipeline {
agent any
  stages {
    stage('build & SonarQube analysis') {
        steps {
            withSonarQubeEnv('SonarQube') { // Will pick the global server connection you have configured
                sh './gradlew clean sonarqube'
            }
        }
    }
   
  }
}