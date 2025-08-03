pipeline {
    agent any

    environment {
        IMAGE_NAME = "shivanshu19/DoOrDie:latest"
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
                    docker stop DoOrDie || true
                    docker rm DoOrDie || true
                    """
                }
            }
        }

        stage('Run new container') {
            steps {
                script {
                    sh """
                    docker run -d --name DoOrDie -p 80:80 $IMAGE_NAME
                    """
                }
            }
        }
    }
}
