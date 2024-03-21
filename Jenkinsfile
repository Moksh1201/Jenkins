pipeline {
    agent any

    environment {
        REPOSITORY_URL = "https://github.com/Moksh1201/Jenkins"
        TESTING_ENVIRONMENT = "staging"
        PRODUCTION_ENVIRONMENT = "AWS EC2"
    }

    stages {
        stage('Retrieve Code') {
            steps {
                echo "Retrieving code from ${env.REPOSITORY_URL}"
            }
        }
        stage('Compile and Build') {
            steps {
                echo "Building the project using Maven"
            }
        }
        stage('Code Analysis') {
            steps {
                echo "Running unit and integration tests with JUnit"
            }
            post {
                success {
                    emailext  subject: 'Test Outcome: Success', 
                               body: 'All tests passed without issues.', 
                               to: "mokshmadaan27@gmail.com",
                               attachLog: true
                }
                failure {
                    emailext  subject: 'Test Outcome: Failure', 
                               body: 'Some tests failed during execution.', 
                               to: "mokshmadaan27@gmail.com",
                               attachLog: true
                }
            }
        }

        stage('Security Inspection') {
            steps {
                echo "Performing security analysis utilizing Synopsys Security Scan"
            }
            post {
                success {
                    emailext  subject: 'Security Review: Passed', 
                               body: 'No security threats were identified.', 
                               to: "mokshmadaan27@gmail.com",
                               attachLog: true
                }
                failure {
                    emailext  subject: 'Security Review: Failed', 
                               body: 'Security vulnerabilities detected.', 
                               to: "mokshmadaan27@gmail.com",
                               attachLog: true
                }
            }
        }
        stage('Deploy to Staging Environment') {
            steps {
                echo "Deploying to Staging Environment (AWS EC2)"
            }
        }
        stage('Integration Testing') {
            steps {
                echo "Executing Integration Tests with Apache Camel"
                echo "Update code base"
            }
        }
        stage('Deploy to Production Environment') {
            steps {
                echo "Deploying to production environment: ${env.PRODUCTION_ENVIRONMENT}"
            }
        }
    }

    post {
        success {
            emailext subject: "Pipeline '${currentBuild.fullDisplayName}' Succeeded",
                      body: 'The build completed successfully. Well done!',
                      to: 'mokshmadaan27@gmail.com',
                      attachLog: true
        }
          
        failure {
            emailext subject: "Pipeline '${currentBuild.fullDisplayName}' Failed",
                      body: 'The build encountered errors. Please investigate.',
                      to: 'mokshmadaan27@gmail.com',
                      attachLog: true
        }
    }
}
