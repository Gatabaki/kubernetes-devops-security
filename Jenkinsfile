pipeline {
  agent any

  stages {
       stage('Build Artifact - Maven') {
          sh "mvn clean package  -DskipTests=true"
          archive  'target/*.jar'
       }

       stage('Test') {
            steps {
                // Run your tests with JaCoCo enabled
                sh "mvn test"
            }
        
    

            post {
              always {
                // Publish JaCoCo coverage report
                junit  'target/surefire-reports/*.xml'
                jacoco execPattern: 'target/jacoco.exec'
        }
    }

  } 
}
}