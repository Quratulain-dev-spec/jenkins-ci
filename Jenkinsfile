pipeline{
    agent any
    stages{
        stage ("code checkout")
        {
            steps{
                checkout scm
            }
        
        }
        stage ("install dependency")
        {
            steps{
                bat "npm install"
            }
        }
        stage('Security Scan') {
             steps {
                 bat 'npm audit --audit-level=high'
             }
        }
        stage ("build")
        {
            steps{
                bat "npm run build"
            }
        }
        stage("Test")
        {
            steps {
                bat "npm test  -- --passWithNoTests"
            }
        }
    
    }
     
}
