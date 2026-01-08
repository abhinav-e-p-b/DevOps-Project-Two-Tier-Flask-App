pipeline {
    agent any

    stages {
        stage('Clone repo') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/abhinav-e-p-b/DevOps-Project-Two-Tier-Flask-App.git'
            }
        }

        stage('Build image') {
            steps {
                sh 'docker build -t flask-app:latest .'
            }
        }

        stage('Deploy with docker compose') {
            steps {
                sh '''
                docker compose down -v || true
                docker system prune -f || true
                docker compose up -d --build
                '''
            }
        }
    }
}
