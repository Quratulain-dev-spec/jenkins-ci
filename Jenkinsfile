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
    }
     
}
