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
     
     
     stage("Quality Gate") {
            steps {
                timeout(time: 2, unit: 'MINUTES') {
                    // Parameter indicates whether to set pipeline to UNSTABLE if Quality Gate fails
                    // true = set pipeline to UNSTABLE, false = don't
                    waitForQualityGate abortPipeline: true
                }
            }
        }
     
     
  }

}
