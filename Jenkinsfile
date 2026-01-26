pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                powershell '''
                mvn.cmd clean compile
                '''
            }
        }

        stage('Test') {
            steps {
                powershell '''
                mvn.cmd test
                '''
            }
        }

        stage('Package') {
            steps {
                powershell '''
                mvn.cmd package
                '''
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
