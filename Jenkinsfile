// Declarative

pipeline {
  agent any

  tools {
    maven 'Maven'        // Name defined in Manage Jenkins → Tools
    jdk 'jdk-24'       // Optional if you configured a JDK tool
  }

  triggers {
    // Uses GitHub Webhook if configured
    githubPush()
    // pollSCM('H/2 * * * *') // Uncomment if you prefer polling
  }

  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }
    stage('Build') {
      steps {
        bat 'mvn -q clean package'
      }
    }
    stage('Run') {
      steps {
        bat 'java -jar target\\your-artifact-name.jar'
        // Example: bat 'java -jar target\\simple-java-app-1.0.0.jar'
      }
    }
  }

  post {
    always {
      archiveArtifacts artifacts: 'target\\*.jar', fingerprint: true
    }
  }
}
