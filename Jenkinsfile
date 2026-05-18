pipeline {
    agent any

    environment {
        IMAGE_NAME = "academy-app"
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'devops-lab',
                credentialsId: 'github-pat',
                url: 'https://github.com/Ahad-Rehman/academy.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t academy-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker stop academy-app || true
                docker rm academy-app || true
                docker run -d -p 5000:80 --name academy-app academy-app
                '''
            }
        }
    }
}
