pipeline {
    agent any

    environment {
        APP_NAME = 'week09-app'
        APP_VERSION = 'v1'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building Week 09 application...'
                sh 'node --version'
                sh 'npm --version'
            }
        }

        stage('Test') {
            steps {
                echo 'Running automated tests...'
                sh 'npm test'
            }
        }

        stage('Package') {
            steps {
                echo 'Building Docker image...'
                sh 'docker build -t ${APP_NAME}:${APP_VERSION} .'
            }
        }
    }

    post {
        success {
            echo 'Week 09 CI pipeline completed successfully!'
        }

        failure {
            echo 'Week 09 CI pipeline failed.'
        }
    }
}
