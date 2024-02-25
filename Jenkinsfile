pipeline {
    agent any
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
                withCredentials([string(credentialsId: 'DOCKERHUB_PASS', variable: 'DOCKERHUB_PASS')]) {
                    sh "docker login -u merabi14 -p ${DOCKERHUB_PASS}"
                }
                if (env.BRANCH_NAME == 'main') {
                    sh 'docker build -t merabi14/nodemain:v1.0 .'
                    sh 'docker push merabi14/nodemain:v1.0'
                } 
                else if (env.BRANCH_NAME == 'dev') {
                    sh 'docker build -t merabi14/nodedev:v1.0 .'
                    sh 'docker push merabi14/nodedev:v1.0'
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
