pipeline {
    agent any
    
    environment {
        MAIN_PORT = '3000'
        DEV_PORT = '3001'
    }
    
    stages {
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
        
        stage('Docker build') {
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
        
        stage('Deploy') {
            steps {
                echo "deploy image"
            }
        }
    }
}
