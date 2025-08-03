pipeline {
    agent any

    environment {
        IMAGE_NAME = "shivanshu19/doordie:latest"
    }

    stages {
        stage('Pull latest Docker image') {
            steps {
                script {
                    sh "docker pull $IMAGE_NAME"
                }
            }
        }

        stage('Stop existing container') {
            steps {
                script {
                    sh """
                    docker stop doordie || true
                    docker rm doordie || true
                    """
                }
            }
        }

        stage('Run new container') {
            steps {
                script {
                   sh 'docker run -d -p 80:80 --name doordie shivanshu19/doordie:latest'
                }
            }
        }
    }
}
