pipeline {
    agent any

    tools {
        maven 'maven'   // Name must match Jenkins Global Tool Configuration
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/adithyaS360/seconprojprac.git'
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

        stage('Package') {
            steps {
                sh 'mvn package'
            }
        }

        stage('Run Application') {
            steps {
                sh 'mvn exec:java -Dexec.mainClass="com.example.App"'
            }
        }
    }

    post {
        success {
            echo 'Build and deployment successful!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
