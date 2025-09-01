pipeline {
    agent any

    tools {
        jdk 'jdk-24'       // your JDK tool name
        maven 'Maven' // your Maven tool name
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/vihankumbhare1234/Maven-project.git'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean install'
            }
        }
    }

    post {
        success {
            echo 'Build completed successfully!'
        }
        failure {
            echo 'Build failed.'
        }
    }
}
