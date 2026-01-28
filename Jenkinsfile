pipeline {
    agent any

    tools {
        maven 'Maven3'
        jdk 'Java17'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                bat 'C:\\Windows\\System32\\cmd.exe /c mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                bat 'C:\\Windows\\System32\\cmd.exe /c mvn test'
            }
        }

        stage('Package') {
            steps {
                bat 'C:\\Windows\\System32\\cmd.exe /c mvn package'
            }
        }
    }

    post {
        always {
            junit allowEmptyResults: true, testResults: '**/target/surefire-reports/*.xml'
            archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
        }
    }
}
