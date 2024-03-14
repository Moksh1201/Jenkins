pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                echo 'Dependency installation...'
                echo 'Building the application...'
                git branch: 'main', url: 'https://github.com/mayank1818/task-10.1p.git'
            }
        }
        stage('Testing') {
            steps {
                echo 'Executing tests...'
                
                script {
                    def emailScript = """
                        \$SMTPServer = "smtp.gmail.com"
                        \$SMTPFrom = "mokshmadaan27@gmail.com"
                        \$SMTPTo = "mokshmadaan27@gmail.com"
                        \$SMTPSubject = "Test succeeded."
                        \$SMTPBody = "The test phase has passed."
                        \$SMTPUsername = "mokshmadaan27@gmail.com"
                        \$SMTPPassword = "vvmq fcsn vzwa hbvp"
    
                        Send-MailMessage -From \$SMTPFrom -To \$SMTPTo -Subject \$SMTPSubject -Body \$SMTPBody -SmtpServer \$SMTPServer -UseSsl -Port 587 -Credential (New-Object System.Management.Automation.PSCredential (\$SMTPUsername, (ConvertTo-SecureString -AsPlainText \$SMTPPassword -Force)))
                    """
                    powershell(emailScript)
                }
            }
        }
        stage('Code Analysis') {
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
        stage('Deploy Staging') {
            steps {
                echo 'Deploying to staging environment...'
            }
        }
        stage('Integration Test') {
            steps {
                echo 'Performing integration tests...'
            }
        }
        stage('Deploy Production') {
            steps {
                echo 'Deploying to production environment...'
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
