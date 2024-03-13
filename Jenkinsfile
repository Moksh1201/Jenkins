pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                // Use the correct Maven installation name
                sh 'Maven-3.9.6/bin/mvn clean package'
            }
        }
        // Add other stages as per your pipeline requirements
    }
}
