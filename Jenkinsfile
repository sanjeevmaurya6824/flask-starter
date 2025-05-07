pipeline {
    agent any

    stages {
        stage('Check Docker Access') {
            steps {
                sh 'docker ps'
            }
        }
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/sanjeevmaurya6824/flask-starter.git'
            }
        }
       stage('Build Docker Image') {

            steps {

                sh 'docker build -t flask-student .'

            }
        }
        stage('Stop Previous Container') {
            steps {
                sh 'docker stop flask-student || true'
            }
        }
        stage('Run New Docker Container') {
            steps {
                sh 'docker run -d --name flask-student -p 5000:5000 flask-student'
            }
        }
        stage('Post Actions') {
            steps {
                echo 'Deployment Successful!'
            }
        }
    }
}
