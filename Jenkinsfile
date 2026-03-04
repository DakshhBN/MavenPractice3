pipeline {
    agent any

    tools {
        maven 'maven'   // Must match the Maven name in Jenkins Global Tool Configuration
    }

    environment {
        HEADLESS = 'true'
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/DakshhBN/MavenPractice3.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('Run Selenium Tests') {
            steps {
                sh 'mvn test -Dheadless=${HEADLESS}'
            }
        }

        stage('Package Application') {
            steps {
                sh 'mvn package'
            }
        }

    }

    post {
      
        success {
            echo 'Build and Selenium tests passed!'
        }
        failure {
            echo 'Build or tests failed!'
        }
    }
}
