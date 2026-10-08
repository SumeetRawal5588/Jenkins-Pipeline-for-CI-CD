pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'npm ci'
            }
        }

        stage('Test') {
            steps {
                bat 'npm test'
            }
        }

        stage('Docker Build') {
            steps {
                bat 'docker build -t nodejs-demo-app:jenkins .'
            }
        }

        stage('Deploy') {
            steps {
                bat 'docker stop nodejs-demo-container || exit 0'
                bat 'docker rm nodejs-demo-container || exit 0'
                bat 'docker run -d --name nodejs-demo-container -p 3000:3000 nodejs-demo-app:jenkins'
            }
        }

        stage('Verify') {
            steps {
                bat 'docker ps'
            }
        }
    }
}
