pipeline {
    agent any
    
    environment {
        MAIN_PORT = '3000'
        DEV_PORT = '3001'
    }
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Build') {
            steps {
                echo "Build Successful"
            }
        }
        
        stage('Test') {
            steps {
                echo "test Successful"
            }
        }
        
        stage('Set Port and Logo') {
            steps {
                script {
                    // Set port number based on the branch
                    if (env.BRANCH_NAME == 'main') {
                        PORT = MAIN_PORT
                        echo "${PORT}"
                    } else if (env.BRANCH_NAME == 'dev') {
                        PORT = DEV_PORT
                        echo "${PORT}"
                    } else {
                        echo "else"
                    }
                }
            }
        }
        
        stage('Build Docker Image') {
            steps {
                echo "building docker file"
            }
        }
        
        stage('Deploy') {
            steps {
                echo "deploy image"
            }
        }
    }
}
