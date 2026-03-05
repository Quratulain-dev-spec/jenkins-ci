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
                    bat 'docker build -t anniesaeed/my-nodejs-app:latest .'
                }
            }
            stage ('Trivy') {
                steps {
                    bat '''
                    trivy.exe image ^
                    --severity CRITICAL ^
                    --exit-code 1 ^
                    --format json ^
                    -o frontend-trivy-report.json ^
                    --timeout 30m ^
                    anniesaeed/my-nodejs-app:latest
                    '''
                }
            }
            stage('Docker Login') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub',
                    usernameVariable: 'DOCKER_USER',
                    passwordVariable: 'DOCKER_PASS'
                )]) {
                    bat 'docker login -u %DOCKER_USER% -p %DOCKER_PASS%'
                }
            }
        }

        stage('Push Images to DockerHub') {
                steps {
                    bat 'docker push anniesaeed/my-nodejs-app:latest'
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
