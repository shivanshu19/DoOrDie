pipeline {
    agent {
        docker {
            image 'mcr.microsoft.com/dotnet/sdk:9.0'
            args '-v /root/.nuget/packages:/root/.nuget/packages'
        }
    }
    environment {
        DOTNET_CLI_HOME = '/tmp/dotnet-home'
    }
    stages {
        stage('Build') {
            steps {
                sh 'mkdir -p /tmp/dotnet-home'
                sh 'dotnet restore'
                sh 'dotnet build --no-restore'
            }
        }
    }
}
