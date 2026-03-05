pipeline {
    agent any 

    stages {
        stage('Checkout Code') {
            steps {
                checkout scm
            }
        
        }

        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }
        stage('Build') {
            steps{
                bat 'npm run build'
            }
        }

        stage('Unit Test + Coverage') {
            steps {
                    bat 'npm test -- --coverage --watchAll=false --passWithNoTests'
            }
        }
        stage('Docker Build') {
            steps {
                    bat 'docker build -t my-nodejs-app:latest ./src'
                }
            }
        }
    
    post {
        always {
            echo "Pipeline finished!"
        }
        success {
            echo "All stages passed ✅"
        }
        failure {
            echo "Pipeline failed ❌"
        }
    }
}