pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Repository checked out from GitHub'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t devops-assignment .'
            }
        }

        stage('Run Docker Container') {
            steps {
                bat '''
                docker stop devops-assignment || ver > nul
                docker rm devops-assignment || ver > nul
                docker run -d -p 8081:80 --name devops-assignment devops-assignment
                '''
            }
        }

    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }

        failure {
            echo 'Pipeline failed.'
        }
    }
}