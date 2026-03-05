pipeline{
    agent any
    stages{
        stage ('code checkout')
        {
            steps{
                checkout scm
            }
        
        }
        stage ('install dependency')
        {
            steps{
                bat 'npm install'
            }
        }
        stage('Security Scan') {
             steps {
                 bat 'npm audit --audit-level=moderate || echo "Security vulnerabilities found, check manually"'
             }
        }
        stage ('build')
        {
            steps{
                bat 'npm run build'
            }
        }
        stage('Test')
        {
            steps {
                bat 'npm test  -- --passWithNoTests'
            }
        }
    
    }
     
}
