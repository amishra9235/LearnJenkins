pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Clone the GitHub repository
                git branch: 'main', url: 'https://github.com/amishra9235/LearnJenkins.git'
            }
        }

        stage('Build') {
            steps {
                // Build the Maven project on Windows
                bat 'mvn clean install'
            }
        }

        stage('Run Tests') {
            steps {
                // Execute test cases on Windows
                bat 'mvn test'
            }
        }

        stage('Publish Test Results') {
            steps {
                // Archive JUnit test results
                junit 'target\\surefire-reports\\*.xml'
            }
        }
    }

    post {
        always {
            // Clean up workspace
            cleanWs()
        }
        success {
            echo 'Build and tests executed successfully!'
        }
        failure {
            echo 'Build or tests failed. Check logs.'
        }
    }
}
