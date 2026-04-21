pipeline {
    agent any
    stages {
        stage('Clone') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/MuhammadSaqib312/devops-lab-app.git'
            }
        }
        stage('Build Image') {
            steps {
                sh 'docker build -t devops-lab-app .'
            }
        }
        stage('Run Container') {
            steps {
                sh 'docker stop devops-app || true'
                sh 'docker rm devops-app || true'
                sh 'docker run -d -p 5000:5000 --name devops-app devops-lab-app'
            }
        }
        stage('Verify') {
            steps {
                sh 'sleep 3 && curl http://localhost:5000'
            }
        }
    }
}