pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/s-azeem7/Devops_project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t ci-cd-demo:latest .'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                docker ps -q --filter "name=ci-cd-demo" | grep -q . && docker stop ci-cd-demo && docker rm ci-cd-demo || true
                docker run -d --name ci-cd-demo -p 8080:80 ci-cd-demo:latest
                '''
            }
        }
    }
}

