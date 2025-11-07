pipeline {
    agent any

    tools {
        maven 'maven-3.9.11'
        jdk 'jdk-17'
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/meganathan-33/dev66.git'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }

        stage('Package') {
            steps {
                bat 'mvn package'
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
        }
        success {
            echo '✅ Pipeline Success!'
        }
        failure {
            echo '❌ Pipeline Failed!'
        }
    }
}
