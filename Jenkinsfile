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
     
     stage('Code Analysis') {
      steps {
        // script
        sh 'mvn sonar:sonar'
      }
    }
  }

}
