pipeline {
    agent any

    tools {
        maven 'maven'
    }

    stages {

        stage('Checkout') {
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
                sh 'xvfb-run mvn test'
            }
        }

        stage('Package') {
            steps {
                sh 'mvn package'
            }
        }
    }

    post {
       
        success {
            echo 'Build and Selenium tests executed successfully!'
        }

        failure {
            echo 'Build or tests failed!'
        }
    }
}
