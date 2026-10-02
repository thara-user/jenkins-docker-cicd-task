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
                bat 'docker build -t jenkins-docker-app:latest .'
            }
        }

        stage('Test') {
            steps {
                bat '''
                    docker rm -f test-container 2>NUL || exit /b 0
                    docker run -d --name test-container -p 8083:80 jenkins-docker-app:latest
                    timeout /t 5 /nobreak
                    curl -f http://localhost:8083
                    docker rm -f test-container
                '''
            }
        }

        stage('Deploy') {
            steps {
                bat '''
                    docker rm -f jenkins-docker-container 2>NUL || exit /b 0
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
