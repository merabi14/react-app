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
            dir('src') {
                    sh 'npm test'
                }
            }
        }

    stage('Docker build') {
        steps {
            script {
                if (env.BRANCH_NAME == 'main') {
                    sh 'docker build -t nodemain:v1.0 .'
                } 
                else if (env.BRANCH_NAME == 'dev') {
                    sh 'docker build -t nodedev:v1.0 .'
                }
            }
        }
    }   
        
    stage('Deploy') {
        steps {
            script {
                if (env.BRANCH_NAME == 'main') {
                    build job: 'Deploy_to_main'
                }
                else if (env.BRANCH_NAME == 'dev') {
                    build job: 'Deploy_to_dev'
                }
            }
        }
    }
    }
}
