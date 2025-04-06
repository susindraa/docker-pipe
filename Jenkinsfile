pipeline {
    agent any

    environment {
        IMAGE_NAME = 'susindraa/docker-pipe'   // your docker hub image name
        DOCKER_CREDENTIALS_ID = 'docker-id'  // set this ID in Jenkins credentials
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url:  'https://github.com/susindraa/docker-pipe.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                    script {
                        docker.build("${docker-pipe}", '.')
                    }
                }
            }
        

        stage('Push to Docker Hub') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', "${docker-id}") {
                        docker.image("${docker-pipe}").push('latest')
                    }
                }
            }
        }
    }
}
