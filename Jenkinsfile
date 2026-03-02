pipeline {
    agent any

    tools {
        maven 'maven'
    }

    stages {

        stage('Build & Test') {
            steps {
                sh 'mvn clean install'
            }
        }
    }

    post {
        always {
            junit 'target/surefire-reports/*.xml'
        }
        success {
            echo 'Selenium Tests Passed!'
        }
        failure {
            echo 'Build or Tests Failed!'
        }
    }
}
