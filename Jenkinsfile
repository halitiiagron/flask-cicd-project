pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Test Docker') {
            steps {
                bat 'docker version'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t flask-cicd .'
            }
        }

        stage('Run Container') {
            steps {
                bat 'docker stop flask-app || exit 0'
                bat 'docker rm flask-app || exit 0'
                bat 'docker run -d -p 5000:5000 --name flask-app flask-cicd'
            }
        }
    }
}