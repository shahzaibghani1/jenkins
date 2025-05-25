pipeline {
    agent any

    environment {
        IMAGE_NAME = 'webapp'
        CONTAINER_NAME = 'charming_torvalds'
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/shahzaibghani1/jenkins.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh "docker build -t ${IMAGE_NAME} ."
            }
        }

        stage('Run Docker Container') {
            steps {
                // Stop old container if running
                sh "docker rm -f ${CONTAINER_NAME} || true"

                // Run new container
                sh "docker run -d --name ${CONTAINER_NAME} -p 5000:5000 ${IMAGE_NAME}"
            }
        }
    }
}