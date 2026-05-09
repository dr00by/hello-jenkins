pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps { checkout scm }
        }
        stage('Build Docker Image') {
            steps {
                echo 'Building Docker image'
                sh 'docker build -t hello-jenkins:latest .'
            }
        }
        stage('Run Container') {
            steps {
                echo 'Running container'
                sh 'docker run --rm hello-jenkins:latest'
            }
        }
    }
    post {
        always {
            echo 'Pipeline completed'
            sh 'docker rmi hello-jenkins:latest || true'
        }
    }
}
