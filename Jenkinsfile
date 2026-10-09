
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
                sh 'npm ci'
            }
        }

        stage('Test') {
            steps {
                sh 'npm test'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t nodejs-demo-app:jenkins .'
            }
        }

        stage('Deploy') {
            steps {
                sh 'docker rm -f nodejs-demo-container || true'
                sh 'docker run -d --name nodejs-demo-container -p 3000:3000 nodejs-demo-app:jenkins'
            }
        }

        stage('Verify') {
            steps {
                sh 'docker ps'
            }
        }
    }

    post {
        success {
            echo 'CI/CD Pipeline completed successfully!'
        }
        failure {
            echo 'CI/CD Pipeline failed. Check Console Output.'
        }
    }
}
