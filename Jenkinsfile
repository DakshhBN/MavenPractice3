pipeline {
    agent any

    tools {
        maven 'maven'
        jdk 'jdk11'
    }

    stages {

        stage('Verify Environment') {
            steps {
                sh 'java -version'
                sh 'mvn -version'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
    }

    post {
        always {
            junit '**/target/surefire-reports/*.xml'
        }
        success {
            echo 'Selenium Tests Passed!'
        }
        failure {
            echo 'Build or Tests Failed!'
        }
    }
}
