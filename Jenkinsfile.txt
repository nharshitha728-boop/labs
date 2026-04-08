pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/nharshitha728-boop/labs.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t my-app .'
            }
        }

        stage('Run Container') {
            steps {
                bat 'docker run -d -p 5000:5000 my-app'
            }
        }
    }
}