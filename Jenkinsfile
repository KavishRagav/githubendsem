pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t demo-app .'
            }
        }

        stage('Run Docker Container') {
            steps {
                bat '''
                docker stop demo-container 2>nul
                docker rm demo-container 2>nul
                docker run -d -p 8081:80 --name demo-container demo-app
                '''
            }
        }

        stage('Verify Container') {
            steps {
                bat 'docker ps'
            }
        }
    }

    post {
        success {
            echo 'Application deployed successfully in Docker container.'
        }

        failure {
            echo 'Pipeline failed. Check console output.'
        }
    }
}