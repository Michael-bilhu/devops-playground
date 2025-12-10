pipeline {
    agent any

    environment {
        DOCKERHUB_USER = 'michaelbilhu2'       // change if different
        IMAGE_NAME     = 'webapp'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh """
                  docker build -t ${DOCKERHUB_USER}/${IMAGE_NAME}:${BUI>
                """

