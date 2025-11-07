pipeline {
    agent any
    tools {
        jdk "jdk-17"
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/meganathan-33/dev66.git'
            }
        }

        stage('Build') {
            steps {
                bat "./gradlew clean build"
            }
        }

        stage('Test') {
            steps {
                bat "./gradlew test"
            }
        }

        stage('Package') {
            steps {
                echo "✅ Build and test completed successfully!"
                archiveArtifacts artifacts: 'build/libs/*.jar', fingerprint: true
            }
        }
    }

    post {
        success {
            echo "✅ Pipeline Success!"
        }
        failure {
            echo "❌ Pipeline Failed!"
        }
    }
}
