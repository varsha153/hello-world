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
                withSonarQubeEnv('My SonarQube Server') {
                  sh 'mvn sonar:sonar'
                }
            }
        }
     
     
  }

}
