pipeline {
    agent any

    stages {

        stage('Clone Repo') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t flask-jenkins-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker stop flask-app || true
                docker rm flask-app || true
                docker run -d -p 5000:5000 --name flask-app flask-jenkins-app
                '''
            }
        }
    }
}
