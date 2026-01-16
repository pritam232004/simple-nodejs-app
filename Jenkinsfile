pipeline {
    agent any

    environment {
        CONTAINER_NAME = "node-container"
        APP_PORT = "3000"
    }

    stages {

        stage('Pull Docker Image') {
            steps {
                sh 'docker pull pritam2004/nodeapp:latest'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh '''
                docker stop $CONTAINER_NAME || true
                docker rm $CONTAINER_NAME || true
                '''
            }
        }

        stage('Run Container') {
            steps {
                sh '''
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
