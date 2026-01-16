pipeline {
    agent any

    environment {
        APP_PORT = "3000"
        IMAGE_NAME = "pritam2004/nodeapp:latest"
        CONTAINER_NAME = "node-container"
    }

    stages {

        stage('Build pull') {
            steps {
                bat 'docker pull %IMAGE_NAME%'
            }
        }

        stage('Run Container') {
            steps {
                bat '''
                docker rm -f %CONTAINER_NAME% || exit 0
                docker run -d ^
                  -p %APP_PORT%:%APP_PORT% ^
                  --restart always ^
                  --name %CONTAINER_NAME% ^
                  %IMAGE_NAME%
                '''
            }
        }
    }
}

