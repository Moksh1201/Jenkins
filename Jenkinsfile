pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                // Use the configured Maven installation
                sh 'mvn clean package'
            }
        }
        // Add other stages as per your pipeline requirements
    }
}
