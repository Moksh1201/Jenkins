ppipeline {
   agent any

  environment {
    DIRECTORY_PATH = "mokshm/desktop/Deakin-Unit-Page"
    TESTING_ENVIRONMENT = "staging"
    PRODUCTION_ENVIRONMENT = "Moksh"
  }

  stages {
     stage('Build') {
        steps {
           echo "Fetching source code from "
           echo "Compiling the code and generating artifacts"
        }
     }
     stage('Test') {
        steps {
           echo "Running unit tests"
           echo "Running integration tests"
        }
         post {
                
                success {
                    emailext  subject: 'Unit Test Status - Success', 
                              body: 'Unit Test has been completed successfully.', 
                              to: "mokshmadaan27@gmail.com",
                              attachLog: true
                }
                failure {
                    emailext subject: 'Unit Test Status - Failure', 
                              body: 'Unit Test has failed.', 
                             to: "mokshmadaan27@gmail.com",
                              attachLog: true
                }
            }
     }
     stage('Code Quality Check') {
        steps {
           echo "Checking code quality"
        }
     }
     stage('Deploy') {
        steps {
           echo "Deploying application to ${env.TESTING_ENVIRONMENT}"
        }
     }
     stage('Approval') {
        steps {
           script {
             sleep 10 // Simulate manual approval for 10 seconds
           }
        }
     }
     stage('Deploy to Production') {
        steps {
           echo "Deploying code to production environment: "
        }
     }
  }

