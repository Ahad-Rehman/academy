pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'devops-lab',
                url: 'https://github.com/Ahad-Rehman/academy.git'
            }
        }

        stage('Build Docker Image') {
    steps {
        sh 'docker ps'
        sh 'docker build -t academy-app .'
    }
}

        stage('Run Container') {
            steps {
                sh '''
                docker rm -f academy-app || true
                docker run -d -p 5000:80 --name academy-app academy-app
                '''
            }
        }
    }
}
