pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                git 'https://github.com/KavishRagav/githubendsem'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t demo-app .'
            }
        }

        stage('Run Docker Container') {
            steps {
                bat 'docker stop demo-container || exit 0'
                bat 'docker rm demo-container || exit 0'
                bat 'docker run -d -p 8081:80 --name demo-container demo-app'
            }
        }
    }
}