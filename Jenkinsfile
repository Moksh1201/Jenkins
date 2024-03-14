pipeline {
    agent any

    environment {
        DIRECTORY_PATH = "https://github.com/Moksh1201/Jenkins"
        TESTING_ENVIRONMENT = "staging"
        PRODUCTION_ENVIRONMENT = "Moksh"
    }

    stages {
        stage('Build') {
            steps {
                echo "Fetching the source code from ${env.DIRECTORY_PATH}"
                echo "Building the code using Maven"
            }
        }
        stage('Unit and integration tests') {
            steps {
                echo "Running unit and integration tests using JUnit"
            }
            post {
                success {
                    emailext  subject: 'Success: Testing Stage', 
                               body: 'Tests ran successfully', 
                               to: "mokshmadaan27@gmail.com",
                               attachLog: true
                }
                failure {
                    emailext  subject: 'Failure: Testing Stage', 
                               body: 'Failed to run tests', 
                               to: "mokshmadaan27@gmail.com",
                               attachLog: true
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo "Checking the quality of the code using SonarQube"
            }
        }
        stage('Security Scan') {
            steps {
                echo "Performing Security Scan using Synk"
            }
            post {
                success {
                    emailext  subject: 'Success: Security Scan', 
                               body: 'Security scan was successful', 
                               to: "mokshmadaan27@gmail.com",
                               attachLog: true
                }
                failure {
                    emailext  subject: 'Failure: Security Scan', 
                               body: 'Failed while scanning for security vulnerabilities', 
                               to: "mokshmadaan27@gmail.com",
                               attachLog: true
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo "Deploying to Staging Server (AWS EC2)"
            }
        }
        stage('Integration tests on Staging') {
            steps {
                echo "Running Integration Tests using Apache Camel tool"
                echo "Updating code"
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "Deploying to production environment: ${env.PRODUCTION_ENVIRONMENT}"
            }
        }
    }

    post {
        success {
            emailext subject: "Pipeline '${currentBuild.fullDisplayName}' Successful",
                      body: 'The build was successful. Congratulations!',
                      to: 'mokshmadaan27@gmail.com',
                      attachLog: true
        }
          
        failure {
            emailext subject: "Pipeline '${currentBuild.fullDisplayName}' Failed",
                      body: 'The build has failed. Please investigate.',
                      to: 'mokshmadaan27@gmail.com',
                      attachLog: true
        }
    }
}
