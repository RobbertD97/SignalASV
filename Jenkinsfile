pipeline {
agent any
  stages {
    stage('build & SonarQube analysis') {
        steps {
            withSonarQubeEnv('SonarQube') { // Will pick the global server connection you have configured
                bat './gradlew clean sonarqube'
            }
        }
    }
   
  }
}