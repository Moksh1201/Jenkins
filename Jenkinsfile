pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                // Build code using Maven
                sh 'mvn clean package'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                // Run unit tests
                sh 'mvn test'
                // Run integration tests
                // Add commands for integration tests here
            }
        }
        // Define other stages (e.g., Code Analysis, Security Scan, Deployment) similarly
    }
    post {
        success {
            // Send email notification on pipeline success
            emailext subject: "Pipeline Success",
                      body: "The pipeline completed successfully.",
                      to: "your_email@example.com"
        }
        failure {
            // Send email notification on pipeline failure
            emailext subject: "Pipeline Failure",
                      body: "The pipeline failed.",
                      to: "your_email@example.com"
        }
    }
}
