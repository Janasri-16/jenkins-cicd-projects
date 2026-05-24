pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t jenkins-cicd-projects .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker stop jenkins-cicd-container || true'
                sh 'docker rm jenkins-cicd-container || true'
            }
        }

        stage('Deploy Container') {
            steps {
                sh 'docker run -d -p 80:80 --name jenkins-cicd-container jenkins-cicd-projects'
            }
        }
    }
}
