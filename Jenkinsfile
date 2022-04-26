pipeline {
    agent none

    stages {
        stage('Build and test C#') {
            agent {
                docker {
                    image 'mcr.microsoft.com/dotnet/sdk:6.0'
                }
            }
            steps {
                withEnv(['DOTNET_CLI_HOME=/tmp/dotnet_cli_home']){
                    sh 'dotnet build'
                    sh 'dotnet test'
                }
            }
        }
        stage('Build and test Ts') {
            agent {
                docker {
                    image 'node:17-bullseye'
                }
            }
            steps {
                dir('DotnetTemplate.Web'){
                    sh 'npm install'
                    sh 'npm run build'
                    sh 'npm t'
                    sh 'npm run lint'
                }
            }  
        }
    }
}