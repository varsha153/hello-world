pipeline {
   agent any

  stages {
    stage('Checkout') {
      steps {
        echo 'Checkout'
        checkout scm
      }
    }

    stage('Build') {
      steps {
        // script
        sh 'mvn clean install'
      }
    }
     
     stage('SonarQube analysis') {
            steps {
                withSonarQubeEnv('sonarqube-server') {
                  sh 'mvn sonar:sonar'
                }
            }
        }
     
     
  }

}
