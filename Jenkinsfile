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
        

        stage('Unit Test + Coverage') {
            steps {
                    bat 'npm test -- --coverage --watchAll=false --passWithNoTests'
            }
        }
        stage('Docker Build') {
            steps {
                    bat 'docker build -t my-nodejs-app:latest .'
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
