pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                // Your build steps here
                // For example, compile your Java code
                sh 'mvn clean package'
            }
        }
        stage('Test') {
            steps {
                // Run your tests with JaCoCo enabled
                sh 'mvn test jacoco:prepare-agent'
            }
        }
    }

    post {
        always {
            // Generate and publish JaCoCo coverage report
            jacoco(execPattern: '**/target/jacoco.exec')
            // Archive artifacts
            archiveArtifacts artifacts: 'target/*.jar'
        }
    }
}
