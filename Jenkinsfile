pipeline {
    agent any
    environment {
        DOCKER_IMAGE = 'bolt-app'
    }
    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/SkrytyZubr/bolt-ap.git', branch: 'main'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build(env.DOCKER_IMAGE)
                }
            }
        }
        stage('Run Docker Container') {
            steps {
                script {
                    docker.image("${env.DOCKER_IMAGE}:latest").run("-p 4000:80")
                }
            }
        }
    }
}
