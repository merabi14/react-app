pipeline {
    agent any
    
    environment {
        MAIN_PORT = '3000'
        DEV_PORT = '3001'
    }
    
    stages {
        stage('Build') {
            steps {
                dir('src'){
                    sh 'npm install'
                }
            }
        }
        
    stage('Test') {
        steps {
        // Change directory to src
            dir('src') {
            // Run npm test command
                    sh 'npm test'
                }
            }
        }

        
        stage('Docker build') {
            steps {
                script {
                    sh 'pwd'
                    sh 'ls'
                    docker.build(temp:0.1 .)
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
