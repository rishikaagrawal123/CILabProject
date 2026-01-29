pipeline {
    agent any

    tools {
        maven 'Maven3'
        jdk 'Java17'
    }

    stages {
        stage('Build') {
            steps {
                bat '%MAVEN_HOME%\\bin\\mvn.cmd clean compile'
            }
        }

        stage('Test') {
            steps {
                bat '%MAVEN_HOME%\\bin\\mvn.cmd test'
            }
        }

        stage('Package') {
            steps {
                bat '%MAVEN_HOME%\\bin\\mvn.cmd package'
            }
        }
    }
}
