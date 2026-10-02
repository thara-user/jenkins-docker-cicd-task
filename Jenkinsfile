pipeline {

    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'docker build -t jenkins-docker-app:latest .'
            }
        }

        stage('Test') {
            steps {
                sh '''
                    docker rm -f test-container 2>/dev/null || true
                    docker run -d --name test-container -p 8083:80 jenkins-docker-app:latest
                    sleep 5
                    curl -f http://localhost:8083
                    docker rm -f test-container
                '''
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                    docker rm -f jenkins-docker-container 2>/dev/null || true
                    docker run -d --name jenkins-docker-container -p 8082:80 jenkins-docker-app:latest
                '''
            }
        }
    }

    post {
        success {
            echo 'CI/CD Pipeline completed successfully!'
        }

        failure {
            echo 'CI/CD Pipeline failed!'
        }
    }
}
