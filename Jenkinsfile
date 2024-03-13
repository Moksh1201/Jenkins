pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                // Build code using Maven
                sh 'mvn clean package'
            }
        }
    }
}
