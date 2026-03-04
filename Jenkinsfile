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
        stage ("build")
        {
            steps{
                bat "npm run build"
            }
        }
    }
     
}
