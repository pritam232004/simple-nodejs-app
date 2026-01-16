pipeline {
    agent any

    environment {
        IMAGE_NAME = "pritam2004/nodeapp:latest"
        CONTAINER_NAME = "node-container"
        APP_PORT = "3000"
    }

    stages {

        stage('Pull Docker Image') {
            steps {
                bat 'docker pull pritam2004/nodeapp:latest'
            }
        }

        stage('Stop Old Container') {
            steps {
                bat '''
                docker stop $CONTAINER_NAME || true
                docker rm $CONTAINER_NAME || true
                '''
            }
        }

        stage('Run Container') {
            steps {
                bat '''
                docker run -d \
                -p ${APP_PORT}:${APP_PORT} \
                --name $CONTAINER_NAME \
                --restart always \
                $IMAGE_NAME
                '''
            }
        }
    }
}


