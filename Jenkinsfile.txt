node('docker') {
  stage('SCM') {
    checkout poll: false, scm: [$class: 'GitSCM', branches: [[name: 'master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/RobbertD97/SignalASV.git']]]
  }
  stage('SonarQube Analysis') {
        sh "/home/jenkins/tools/hudson.plugins.sonar.SonarRunnerInstallation/sonarqubescanner/bin/sonar-scanner -Dsonar.host.url=http://localhost:9000 -Dsonar.projectName=signalasv -Dsonar.projectVersion=1.0 -Dsonar.projectKey=SignalASV:app -Dsonar.sources=. -Dsonar.projectBaseDir=/home/jenkins/workspace/signal_test_pipeline"
    }
  }