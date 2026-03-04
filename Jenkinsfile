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
        stage("Test")
        {
            steps {
                bat "npm test  -- --passWithNoTests"
            }
        }
        stage("Docker Build")
        {
             steps {
                 bat "docker build -t todo-app"
            }
        }
    }
     
}
