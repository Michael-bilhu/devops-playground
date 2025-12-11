pipeline {
    agent any

    environment {
        DOCKERHUB_USER = 'michaelbilhu2'   // your Docker Hub username
        IMAGE_NAME     = 'webapp'
    }

    stages {

        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                dir('app') {
                    bat "docker build -t %DOCKERHUB_USER%/%IMAGE_NAME%:${BUILD_NUMBER} ."
                }
            }
        }

        stage('Login & Push to Docker Hub') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub-creds',
                    usernameVariable: 'USER',
                    passwordVariable: 'PASS'
                )]) {
                    dir('app') {
                        bat """
docker login -u %USER% -p %PASS%
docker push %DOCKERHUB_USER%/%IMAGE_NAME%:${BUILD_NUMBER}
"""
                    }
                }
            }
        }
    }
}
