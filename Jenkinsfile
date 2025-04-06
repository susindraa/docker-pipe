pipeline {
    agent any

    environment {
        IMAGE_NAME = 'susindraa/first-dock'   // your docker hub image name
        DOCKER_CREDENTIALS_ID = 'docker-hub-creds'  // set this ID in Jenkins credentials
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/susindraa/Docker-Zero-to-Hero.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                dir('FIRST DOCK') {
                    script {
                        docker.build("${IMAGE_NAME}", '.')
                    }
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', "${DOCKER_CREDENTIALS_ID}") {
                        docker.image("${IMAGE_NAME}").push('latest')
                    }
                }
            }
        }
    }
}
