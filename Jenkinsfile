pipeline {
    agent any

    environment {
        IMAGE_NAME="thethymca/pythonapp:${BUILD_NUMBER}"
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/harkaur02/simple-python-app-Dockerized.git'
                echo 'git branch main cloned'
            }
        }
        stage('Build and Push Docker Image') {
            steps{
                script {
                    sh "docker build -t ${IMAGE_NAME} ."
                    echo 'Docker Image build done!'
                    docker.withDockerRegistry('https://index.docker.io/v1/','docker-credentials') {
                    // docker image push
                    sh "docker push ${IMAGE_NAME}"
                    }
                }
            }
        }
    }
}
