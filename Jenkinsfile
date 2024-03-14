pipeline {
    agent any

    environment {
        DIRECTORY_PATH = "mokshm/desktop/Deakin-Unit-Page"
        TESTING_ENVIRONMENT = "staging"
        PRODUCTION_ENVIRONMENT = "Moksh"
    }

    stages {
        stage('Build') {
            steps {
                echo 'Dependency installation...'
                echo 'Building the application...'
                git branch: 'main', url: 'https://github.com/Moksh1201/HTML/tree/main/10.1p'
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
                echo 'Analyzing code quality...'
            }
        }
        stage('Security') {
            steps {
                echo 'Conducting security scans...'
                
                script {
                    def emailScript = """
                        \$SMTPServer = "smtp.gmail.com"
                        \$SMTPFrom = "mokshmadaan27@gmail.com"
                        \$SMTPTo = "mokshmadaan27@gmail.com"
                        \$SMTPSubject = "Security checks passed."
                        \$SMTPBody = "The pipeline has successfully cleared security checks."
                        \$SMTPUsername = "mokshmadaan27@gmail.com"
                        \$SMTPPassword = "vvmq fcsn vzwa hbvp"
    
                        Send-MailMessage -From \$SMTPFrom -To \$SMTPTo -Subject \$SMTPSubject -Body \$SMTPBody -SmtpServer \$SMTPServer -UseSsl -Port 587 -Credential (New-Object System.Management.Automation.PSCredential (\$SMTPUsername, (ConvertTo-SecureString -AsPlainText \$SMTPPassword -Force)))
                    """
                    powershell(emailScript)
                }
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
                    sleep 10 
                }
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "Deploying code to production environment: "
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
