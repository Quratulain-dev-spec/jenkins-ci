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
    }
     
}