pipeline{
    agent any
    stages{
        stage ("code checkout")
        {
            steps{
                checkout scm
            }
        
        }
        stage ('npm install')
        {
            steps{
                bat "npm install"
            }
        }
        stage("Security Scan") {
            steps {
                bat "npm audit --audit-level=moderate"
            }
        }
        stage ("build")
        {
            steps{
                bat "npm run build"
            }
        }
        stage ("Test")
        {
            steps{
                bat "npm test"
            }

        }
        stage('Code Coverage') 
        {
            steps {
                 bat 'npm test -- --coverage'
            }
        }
        
    }
     
}